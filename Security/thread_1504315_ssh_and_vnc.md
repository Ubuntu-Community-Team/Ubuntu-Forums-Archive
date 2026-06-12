---
title: "ssh and vnc?"
date: 2010-06-07
forum: Security
---

### Post by TheNewbieGeek on 2010-06-07
Hi I am going to add some security features to ubuntu and I was reading the sticky at the top of this forum topic. It said the two most common hacks are ssh and vnc. I don't want to use these then but I don't know what services use them. Can you tell me.  Also I am wondering if anybody could recommend a good read on how to make ubuntu airtight. thanks for the replies.

---

### Post by an0dos on 2010-06-07
> **TheNewbieGeek said:**
> Hi I am going to add some security features to ubuntu and I was reading the sticky at the top of this forum topic. It said the two most common hacks are ssh and vnc. I don't want to use these then but I don't know what services use them. Can you tell me.  Also I am wondering if anybody could recommend a good read on how to make ubuntu airtight. thanks for the replies.

SSH and VNC are both ways of controlling your computer from another computer. They are not enabled by default and so you don't need to worry about them. Basically, don't enable the remote desktop (system-->preferences-->remote desktop).

Apply security updates when they are available. Keep your computer behind a router. Use the no-script add-on for firefox. Don't be so paranoid that using a computer ceases to be fun :) If you do those things you should be pretty safe.

---

### Post by movieman on 2010-06-08
Basically the problems are due to running ssh or vnc with insecure passwords; a lot of people do it, sometimes without even realising, and a lot of bad guys scan the Internet for open ssh and vnc ports and try to log in using a dictionary of passwords. So if you don't run sshd or vnc then you're safe.

If you do run sshd, configure it to use public keys rather than passwords, and if you run vnc, configure it to only listen on the local machine and use ssh to forward it to wherever you're accessing it from. And in both cases if you must make them visible to the Internet then set them to use non-standard ports so the crackers won't bother you (99+% of them only check the standard port numbers when scanning the Internet since scanning all ports is very slow and often blocked by routers).

---

