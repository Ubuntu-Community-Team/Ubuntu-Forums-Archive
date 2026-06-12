---
title: "Jeos http connection fail"
date: 2008-05-08
forum: Server Platforms
---

### Post by mizar001 on 2008-05-08
Hi. I installed a virtual machine with a jeOS 8.04 system.

I have a similar desktop ubuntu 8.04 in the same subnet, and the ip is static.

When i ping something in internet i have their ip resolved by dns, but when i try :

sudo apt-get update

the command hang in the row : 
0% : Connecting to archive.ubuntu.com [91.189...
and after it tell me that the connection timed out.

It seems that http packets are not recognized by the system. What can i do ?

NOTE : wget and telnet are not there, and every try to install them return to me with a message :
--The package 'xxx' is not present but is mentioned in another package or something similar.

---

### Post by mizar001 on 2008-05-09
Never mind. I was mispelling the gateway ip address.

---

