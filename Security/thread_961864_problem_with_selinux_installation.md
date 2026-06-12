---
title: "problem with selinux installation"
date: 2008-10-28
forum: Security
---

### Post by YyYo on 2008-10-28
Hi...

I decided to install selinux on ubuntu 8.04, but no success.

I install selinux and all the available packages: libselinux1, checkpolicy, policycoreutils, selinux-utils, coreutils, procps, sysvinit, dpkg, libpam-modules, cron, selinux-basics

1) After installation I reboot, and after it when I run the command, ***sestatus*** it tell me that the selinux is disabled.
2) in the file /etc/selinux/config file the selinux is in "enforcing" mode.
3) when I run selinux command like newrole in tell me: Sorry, newrole may be used only on a SELinux kernel
4) the command id doesn't show any security context:
   uid=1000(yossioz) gid=1000(yossioz)     groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(yossioz)

It seems that i missed something somewwhere... Please help

---

### Post by OpenSourceFuture on 2008-10-28
Sounds like you need to patch the kernel, compile a new one with Selinux, or run something that will do that for you.

---

### Post by cariboo on 2008-10-28
Have you removed appamor and apparmor utils?

Jim

---

### Post by YyYo on 2008-10-29
Yes, I remove all appArmor components.
Is there any change that I should do in /boot/grub/menu.lst file ?

I saw in([http://etbe.coker.com.au/2008/07/31/installing-se-linux-on-lenny/](http://etbe.coker.com.au/2008/07/31/installing-se-linux-on-lenny/)) that I should append "selinux=1" to the line which start with "# kopt=..". 
Can some one send me the copy of that line....?

---

### Post by YyYo on 2008-10-30
Problem solved!!!
in the "/proc/cmdline" was missing "selinux=1"
After adding it the selinux is enabled (view "sestatus")

---

### Post by pwerner2 on 2008-11-12
Hi, I have a similar problem. Sort of. I installed and set up selinux a while ago, and now I think I'd like to go back to apparmor, but I've removed apparmor and apparmor-utils. I noticed that you (Cariboo907) were going to say something regarding that, but you didn't.

---

### Post by cariboo on 2008-11-12
I wasn't sure, but it looks like you can't run apparmor and selinux together, and I'm not even sure that if you remove selinux you will still be able to use your system, as once it is installed it installs lables to all the files and processes. I don't like to say it, but reinstalling may be the easiest option.

Jim

---

