---
title: "Ubuntu Noob needs help"
date: 2016-09-28
forum: Server Platforms
---

### Post by linkitup on 2016-09-28
Hey Guys,

I hope that i'm in the right section. :)

I'm using Lubuntu 14.04 and i connect to the Server with xrdp. But when i connect to it, it shows this Error Message: 
```
GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Cannot determine user of subject
```
I can't start any Program on the desktop. I don't have enough Experience to use the Terminal only (When know enough i'm switching to Ubuntu Server ;-) ).

Thanks for your help :)

---

### Post by TheFu on 2016-09-29
If the machines are on the same LAN and you trust it, use **ssh -X userid@servername /full/path/to/program**.  You can use this over the WAN, if you setup ssh for external use, but it will be really slow on most links.  It is secure while rdp is not.  If the client cannot ping the "servername", then put the IP address in there.  Also, ssh should be working first, but that is pretty trivial and always the first thing everyone sets up on any "server."

* ssh X-forwarding has to be allowed in the sshd_config on the remote machine.

I haven't used RDP between Unix systems ... er ... ever.  X-forwarding is the normal way on a LAN.

To troubleshoot, open a terminal on the client and run **xrdp -vvvv remoteserver** ... what does that output?  I'm just guessing on this, BTW. It is common for programs to support more detailed debugging by adding the -vv (more v's gives more answers).  ssh works that way, so do most other C/S programs and many non-C/S ones.

---

