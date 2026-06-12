---
title: "When I disconnect media hard drive, ubuntu doesn't boot"
date: 2010-08-04
forum: Server Platforms
---

### Post by fizgig on 2010-08-04
I have a hard drive that I use to store all my media.  The fstab automounts it at startup to /media/movies

I notice that if I disconnect the media drive and restart ubuntu, ubuntu wont boot past a couple of lines.  Is this a known bug?

---

### Post by spookware on 2010-08-05
yes it is a known bug. [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571444)

To workaround it you need to add "nobootwait" to the line in fstab but sadly this breaks the manual use of the mount command.

---

### Post by fizgig on 2010-08-05
Thanks.  That is indeed the bug.  That's the second large bug I've encountered in Ubuntu server. Going to have to try a more stable distro.

---

### Post by arrrghhh on 2010-08-05
Honestly Ubuntu is not much of a server OS.  I use it, but for enterprise-class server stuff RHEL, CentOS and Debian are still my preferred server OSes.  SLES is good, but I don't have a lot of exposure to it.

---

### Post by fizgig on 2010-08-05
Yeah. Thinking about going debian so I can stay with apt.

Ubuntu is still my preferred desktop os though.

---

### Post by UnresponsiveBeeVictim on 2010-08-11
edit: nevermind

---

