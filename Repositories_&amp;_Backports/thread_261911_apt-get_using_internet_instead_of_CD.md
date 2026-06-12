---
title: "apt-get using internet instead of CD"
date: 2006-09-20
forum: Repositories &amp; Backports
---

### Post by adam410 on 2006-09-20
I've just installed ubuntu dapper server on an x86 machine.

It's connected to the internet via ethernet because i can ping sites and ssh to off-site machines.

when i try and run apt-get to install sshd it prompts for the CD:

> 
$ sudo apt-get install openssh-server
...
Media change: please insert the disc labeled
'Ubuntu-Server 6.01.1 _Dapper Drake_ ...'
in the drive '/cdrom/' and press enter

even when i do this it just hangs for a long time, and optimally I'd like it to get the files via the internet.

Thanks,
   Adam

---

### Post by encompass on 2006-09-20
If you look in your sources list in sysnaptic you can disable it from there.  Everything should be file from that point.
If you want to get more technical it is in your sources file... /etc/apt/sources.list

---

