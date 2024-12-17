---
description: Quick scripts and links when shelling into kubernetes pods
---

# Pod shell tools

***

### NC ([netcat](https://www.geeksforgeeks.org/introduction-to-netcat/))

***

Netcat (commonly abbreviated as nc) is a versatile command-line networking tool used for testing and debugging network connections. It can operate as both a client and server, allowing users to send, receive, and listen for data over TCP and UDP protocols. Netcat is often used for tasks like port scanning, testing service connectivity, transferring files, and establishing basic communication between systems. Its simplicity and flexibility make it a popular choice for network troubleshooting and scripting in environments like Kubernetes pods or across servers.

***



Test Port Connectivity

```
nc -zv <svc> <port>
```

**Example**

```
nc -zv something.aws.com 3000
# open
```

***

#### Listen on a Port (Simple TCP Server)

```
nc -l <port>
```

**Example**

```
nc -l 8080
```

You can connect to it from another pod or host

***

#### Send Data to a Host

```
echo "Hello" | nc <host> <port>
```

**Example**

```
echo "Hello from Pod A" | nc something.aws.com 3000
```

***

Act as a Client (Interactive Session)

```
nc <host> <port>
```

Example

```
nc something.aws.com 8080
```

***

#### Transfer Files Between Pods

To transfer a file from one pod to another using nc.

**On the receiving pod:**

```
nc -l <port> > received_file.txt
```

**On the sending pod:**

```
nc <destination_pod_ip> <port> < file_to_send.txt
```

Example:

Receiving pod (listens on port 9999)

```
nc -l 9999 > received_file.txt
```
