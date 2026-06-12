---
title: "Kernel image error causing FTP install failure"
date: 2015-02-04
forum: Server Platforms
---

### Post by john358 on 2015-02-04
So I'm new to Ubuntu and trying to install vsftpd on my web server. However, whenever I use the ```
sudo apt-get install vsftpd
``` command, I get this error:

```
E: The package linux-image-3.8.0-41-generic needs to be reinstalled, but I can't find an archive for it.
```

Has anyone else seen this error before? How did you fix it? It comes up trying to install virtually anything right now, and is also preventing me from doing an upgrade. I've been able to find some other forums where people have a similar error, but none with a useable solution.

---

### Post by TheFu on 2015-02-05
An ftp server shouldn't be tied to the kernel that closely.
Let's begin by
a) updating the package list - **sudo apt-get update**
b) upgrading all software on the system - **sudo apt-get dist-upgrade** - this should put the newest, compatible kernel on the box.
BTW - those 2 commands should be [run weekly as normal system patching]("http://blog.jdpfu.com/linsysmaint") for a Linux box. 

Oh - and welcome to the forums.

Any chance I could convince you NOT to run a plain FTP server?  There are many, many, many, reasons this shouldn't be done and should have ended in the mid-1990s. [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  Using sftp handles most of the issues and increases security.

---

