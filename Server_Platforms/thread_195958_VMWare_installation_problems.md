---
title: "VMWare installation problems?"
date: 2006-06-13
forum: Server Platforms
---

### Post by iaef on 2006-06-13
I have just downloaded and installed ubuntu server 6.06 LTS.
I have installed it as a vm under vmware wkst 5.5.1-build 19175.
While I was installing I noticed it took a lot of time under configuring apt (scanning mirror or something like that).
Now, it supposedly finished and ejected the CD.

The problem is that I have 1 hour awaiting for it to boot. It only says "uncompressing Linux... Ok, booting the kernel."
nothing more... the CPU is working at 100% so I guess it must be doing something. How much time does it takes to boot the server? I can ping to it, apparently, but I cannot do anything more... even ALT-F2 won't bring another terminal.
Maybe it is already running and I am not aware of it. But if this is the case, how do I use the LAMP environment?

---

### Post by Ignite_nz on 2006-06-13
I suggest you ensure that your copy of Ubuntu is not corrupted in any way, run a checksum on it, or if you want just download a new copy, or even better get Ubuntu to ship you a CD for free by going to [http://shipit.ubuntu.com](http://shipit.ubuntu.com) :) Hope this helps.

Or you could simply delete that virtual machine, make another one and try it again, also try and get VMWare server, its much better and it's free.

---

### Post by iaef on 2006-06-14
I have run the initial checksum and everything is ok. At home, I have no problem installing it. It seems to be only on the laptop at work.
You said vmware server is a much better product... what do you mean by this?

---

### Post by dk_pa on 2006-06-14
Isn't there bug with VMWare + Ubuntu 6.06 server install?  If you did the server install have you tried the desktop intall (vice versa).  I thought I saw something on here about that.

---

### Post by pbonafous on 2006-06-16
You probably right, it 's a bug, you will find a solution here :
[http://ubuntuforums.org/showthread.php?t=186851&highlight=vmware+uncompressing](http://ubuntuforums.org/showthread.php?t=186851&highlight=vmware+uncompressing)

with the command "apt-get install linux-686".

---

