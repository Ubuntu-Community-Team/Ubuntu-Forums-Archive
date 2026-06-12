---
title: "Problem with transferring file via ssh"
date: 2009-04-05
forum: Server Platforms
---

### Post by Ryadt on 2009-04-05
Hi...

I am connected remotely to my server via ssh but I cannot transfer any file using scp.
I get an error message ssh: connect to host 192.168.1.100 port 2220: No route to host

Any ideas please.

---

### Post by spiderbatdad on 2009-04-05
not sure exactly what you are trying to do, but usually no route to host means you are not connected...so seems like there is an error in your command.
There is a simple way to transfer files using sftp over ssh via nautilus if your client is a graphical one. Just go to Places>>Connect to Server.
Select ssh from the drop down menu, and fill in ip address and user you can leave the rest blank. This will mount the file system on your desktop. You can drag and drop files. You can also bookmark the connection by right clicking the directory. Unmount with right click also.

---

### Post by brian_p on 2009-04-05
> **Ryadt said:**
> Hi...

I am connected remotely to my server via ssh but I cannot transfer any file using scp.
I get an error message ssh: connect to host 192.168.1.100 port 2220: No route to host

Any ideas please.

The exact command you used can only help. Whatever it was, scp cannot find 192.168.1.100.

---

### Post by Ryadt on 2009-04-05
> **brian_p said:**
> The exact command you used can only help. Whatever it was, scp cannot find 192.168.1.100.
```
scp -P 2200 /home/ryad/test.txt ryad@192.168.1.11:Documents/

```

---

### Post by brian_p on 2009-04-05
> **Ryadt said:**
> 

```
scp -P 2200 /home/ryad/test.txt ryad@192.168.1.11:Documents/

```

Looks ok to me. You are copying a file from a local machine to a  machine on the same network and both accounts have the same username.

Have you tried pinging the other machine?

---

### Post by lensman3 on 2009-04-05
Unless 192.168.1.xxx is on a local network, then the 192.168.xxx.xxx/24 group is non-routable by the Internet backbone.  You can leave a network with that IP number, but you can't get to it.

---

### Post by spiderbatdad on 2009-04-05
looks like your command is incomplete ie., user@host1 user@host2```
scp -P 2200 user@192.168.1.xx:test.txt ryad@192.168.1.11:Documents/
```Of course this method of transfer requires ssh server running on both machines. sftp is easier from the client to move files to the server.

---

