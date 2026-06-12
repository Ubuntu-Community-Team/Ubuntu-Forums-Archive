---
title: "Remote access"
date: 2011-04-25
forum: Server Platforms
---

### Post by paulc8481 on 2011-04-25
I built an ubuntu server to host my own web pages for school but I am having problems accessing by remote. I have installed both filezila and putty on my windows desktop to access into my ubuntu server but as of yet I have been unable to get into my server. I have tried a number of different ways but still no success. Can anyone give me some advice to get under way and also is ther a way to access my server from places like work if I do not have privileges to download applications such as filezila or putty. Shorewall is installed on my server but is set to "0" so it will not start during operaton, and I am using port forwarding and ports 80, 22 and 21 are enabled.
 
Any help would be most appreciated
 
Thanks Paul

---

### Post by volkswagner on 2011-04-25
You tried a number of ways.  Please offer examples and any errors you encounter.

Are you able to use putty to ssh into your server from inside your LAN?  Have you installed openssh package on the server?

If it works locally but not over public internet you need to verify the port is actually open, ie: nto blocked via your ISP. Navigate to canyouseeme.org from inside your LAN and check the ports 80, 22, 21.

---

### Post by ruffEdgz on 2011-04-25
So from a remote computer, it can see that port 80, 22, and 21 are open or did you just verify that on the local machine?

Also, do you know if your servers IP has a public IP address or local IP addressed assigned via a router? You might just need to have your router configured to handle outside traffic for certain ports to come in and forwarded to your server.

We will probably need a better understanding of your total setup as all I can tell is:
------

SERVER (ubuntu)
|
|
X - No connection
| 
|
Client (PC)

#EDIT# What **volkswagner** said is also helpful to know =D

---

### Post by brettg on 2011-04-27
Did you install openssh-server? It is not installed by default.

---

### Post by Lars Noodén on 2011-04-27
> **paulc8481 said:**
>  Can anyone give me some advice to get under way and also is ther a way to access my server from places like work if I do not have privileges to download applications such as filezila or putty. 

You can run [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/) from a USB stick or even from a temporary directory.  So privileges are not much of a barrier if you can download it or have a USB stick.

---

