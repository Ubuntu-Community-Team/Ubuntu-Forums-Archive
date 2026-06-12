---
title: "APC Powerchute does not install on Ubuntu Server 8.04 lts x86_64"
date: 2009-12-04
forum: Server Platforms
---

### Post by lk2oo3 on 2009-12-04
Hi all,
i'm new in the forum, from years working with linux oss, 
i hope someone may explain me why it is no more possible to install APC Powerchute software.. 

This is the problem:
last week i decide to change my server HD with a new 1.5 TB HD.
Now i'm reinstalling all softwares but i do not understand why powerchute does not install anymore. 

this is what system returns when I install Powerchute:
bash: ./pbe_agent_linux_jvm.bin: No such file or directory
 
I install executing as root in the console ./pbe_agent_linux_jvm.bin
which owner is root and permissions are 777.
This is exactly how I installed Powerchute all other time. 

Thanks in advance for any answer, 
Bye, Luca.



- pbe_agent_linux_jvm.bin is the installer for powerchute business edition v 7.05
- on the old 512 GB HD (same MB, CPU, RAM etc) powerchute installed and worked perfectly
- also, on 2009 august, I installed other 2 Ubuntu servers 8.04 lts x86_64, same way, powerchute installation ok
- Server HW: Intel Quad Core Q9300, 8GB RAM, MB ASUS P5Q SE, 2 512GB HD + 1 1,5TB HD, 3 total NetCards
- kernel version on which Powerchute does not installs is 
2.6.24-25-server #1 SMP .. x86_64 GNU/Linux
while kernel version on which Powerchute works is 
2.6.24-24-server #1 SMP .. x86_64 GNU/Linux

---

### Post by lk2oo3 on 2009-12-09
hey, nobody has an idea?

i've the sensation this is a stupid problem..
after all, APC is very common UPS, Ubuntu server also:
i think this may help other users in the community that need to do an HD upgrade to Tera size.

Yesterday I installed Powerchute software as described in my post, on a Ubuntu 8.04 lts VmWare Server Virtual Machine:

why it does not installs on my Ubuntu Server physical PC??

again,
thanks to all of you that may help me,
bye.

---

### Post by tgalati4 on 2009-12-09
You can boot into the older kernel if that works for you.  Just select the older kernel when you first boot up.  Do some research to determine what changed from 2.6.24 to 2.6.25.  Then file a bug against 2.6.25 at kernel.org.

It could also be a buggy hard disk.  Disks over 1 TB need to be broken in before committing to a server.  Otherwise, you get strange problems that appear to be software related.

Run badblocks on it.

---

### Post by lk2oo3 on 2009-12-10
hi,

> You can boot into the older kernel if that works for you.  Just select the older kernel when you first boot up.  Do some research to determine what changed from 2.6.24 to 2.6.25.  Then file a bug against 2.6.25 at kernel.org.


old kernel was on the old 512GB HD, now formatted.. so this test is not more possible. Before format, I tried to add the 1,5 TB HD in the system but Gparted did non correctly recognized HD and i had to partition and format via fdisk and mke2fs. Ububtu 8.04 lts, instead recognized HD during install and let me terminate installation..

> It could also be a buggy hard disk.  Disks over 1 TB need to be broken in before committing to a server.  Otherwise, you get strange problems that appear to be software related.


In effect, my sensation is the problem is here..
perhaps not a hard buggy disk but a not correct partitioning and format problem.

File on disk have strange behaviour, one of this is that i tried change permissions on a directory, and only a part of the file and subdirectories inherited right permission. 

I was able to reassign right permissions only using webmin file manager, not via chmod/chown command (!!).
In the next days i think i'll make 2 tests: 
1. check disk as you suggested 
2. install SO on a different Tera disk.

I will post results, tnx, bye.

---

### Post by lk2oo3 on 2009-12-13
ok,
this week-end i made a lot of test on VMware Server, installing ubuntu 8.04 server lts 64bit, ubuntu 9.10 server 64 bit,
but nothing changed, until googling the error i found this article
[http://codeandcode.blogspot.com/2008/04/sofficebin-no-such-file-or-directory_12.html](http://codeandcode.blogspot.com/2008/04/sofficebin-no-such-file-or-directory_12.html)
with a similar problem as mine.
This article explains that the reason why some binary file (soffice.bin for him) does not install on new 64 bit OS
is that they are 32 bit software and, in 64 bit systems, it needs to install 32 bit compatibility pack ia32-libs.
The "No such file or directory" message, is due to not installed 32bit libraries, not to non exixtent *.bin file.  

So, in my case, on Ubuntu Hardy 64 bit i solved in this way:
 
sudo aptitude update
sudo aptitude install ia32-libs  

then a sudo ./pbe_agent_linux_jvm.bin let me start Powerchute wizard.

For other that are intrested in APC Powerchute 7.04, 7.05 SW install, I also add that it is possible to install software only from a X server console, also via vnc or nx, not directly from a remote ssh shell.

Thanks to all, bye, Luca.

---

