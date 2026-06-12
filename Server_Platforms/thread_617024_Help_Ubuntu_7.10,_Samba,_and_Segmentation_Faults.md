---
title: "Help: Ubuntu 7.10, Samba, and Segmentation Faults"
date: 2007-11-18
forum: Server Platforms
---

### Post by xls on 2007-11-18
Hello everyone in the Ubuntu forums.  Long time reader, first time poster.  I've been using Linux off and on for quite some time now.  I've run into a problem and I'm totally stumped.  Before anyone says RTFM, just lemme know which manual I need to be reading.

I have some new hardware and I'm setting it up as an all purpose Linux server.  I downloaded ubuntu 7.10 server and got that installed without any real problems.  I selected LAMP, OpenSSH, and Samba options from the installer.  I am attempting to setup a very simple Anonymous read-only samba file server for use with my home network.  I already have samba configured and running on an older (read: boat anchor) computer which is an older Ubuntu server version.  I've done this once before but that was about a year ago and I haven't had to change or fix anything so it's all a little fuzzy.

anyway, i'm using a very simple samba configuration and testparm is happy with it.  yet when i try to start samba it simply fails and says "segmentation fault" as to the reason why.  I've checked the samba logs and they weren't very helpful.  I need to check the system logs but I'm not sure where to look.  I suspect that this error is due to some permissions snafu since 7.10 is suppose to have better security.  

I'm extremely eager to learn.  Up until know my experience with linux, especially ubuntu linux, has been crazy positive.  I'm hoping someone can kindly point me in the right direction.  I'll be checking back frequently to answer any questions and help troubleshoot.

---

### Post by Rich99 on 2007-11-19
See here:
[http://ubuntuforums.org/showthread.php?t=614558](http://ubuntuforums.org/showthread.php?t=614558)

The latest update is borked, downgrade to the previous release.

---

### Post by HermanAB on 2007-11-19
Samba 2.0.27 isdue out today.  See the Samba web site.

Cheers,

H.

---

### Post by xls on 2007-11-19
ok, so it wasn't anything on my end.  i just ran aptitude safe-upgrade and that went ahead an downloaded some new samba packages (samba 3.0.26a-1ubuntu2.1) and samba started right up and works great.

thanks guys

---

