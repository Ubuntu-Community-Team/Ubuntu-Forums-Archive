---
title: "Port 22 in OpenSSH"
date: 2007-11-21
forum: Server Platforms
---

### Post by dyingflight on 2007-11-21
I am trying to create an SSH server for learning more about "Technical usage of the internet." I am receiving an error when i try to use the command ($ssh localhost) or ($ssh admin00@localhost). The error is (ssh: connect to host 192.168.1.102 port 22: Connection refused). I have installed the OpenSSH server and client, and I can connect to other SSH servers using OpenSSH. Please help!!!:confused:

---

### Post by HermanAB on 2007-11-22
SSH has two parts, a client and a server.  Your client works, since you can connect to other servers, but your server isn't running.

---

### Post by ToniVC1963 on 2007-11-22
You need to start the server. Try "sudo /etc/init.d/ssh start".

---

### Post by steve.horsley on 2007-11-22
The server _should_ have started when you installed it, but you can check in two ways. First, use the command
**ps -ef | grep sshd**
to see if the process is running. The menu System->Administration->Services and looking at the entry for Remote Shell Server is a less direct way of checking that it's running.

You can also look and see if port 22 is being listened to with this command:
**netstat -lt**
and look for *.ssh, or 
**netstat -ltn**
and look for :::22

---

