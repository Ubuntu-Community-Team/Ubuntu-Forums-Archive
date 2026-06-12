---
title: "[SOLVED] I installed VirtualBox but it comoplains the Kernel Driver is missing."
date: 2008-11-13
forum: Virtualisation
---

### Post by johnhouk on 2008-11-13
what should i do?

---

### Post by randy78 on 2008-11-13
Open a terminal and type: sudo /etc/init.d/vboxdrv setup

---

### Post by johnhouk on 2008-11-13
* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

---

### Post by johnhouk on 2008-11-14
john@ubuntu:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.

---

### Post by SIGTERMer on 2008-11-14
sudo apt-get install virtualbox-ose-guest-modules-[kernel version]-generic

replace [kernel version] with your current kernel version which is probably 2.6.24-21

---

### Post by johnhouk on 2008-11-14
1st command resulted in:
E: Regex compilation error - Unmatched [ or [^
not sure if it was finnished or what.

and im not sure how to replace [kernel version]...
... sory 1st day, cant find my way back home to windows (lack of pxe boot files), and still like learning an alternative. i've always dreaded the day they put windows online, i think thats whats up with 7.

---

### Post by SIGTERMer on 2008-11-14
dude without the brackets :)
if your kernel is 2.6.24-21, then the command would be:
sudo apt-get install virtualbox-ose-guest-modules-2.6.24-21-generic

---

### Post by johnhouk on 2008-11-14
sorry im high

copyn n pastin... you know


Setting up virtualbox-ose-guest-modules-2.6.24-21-generic (24.0.6) ...
FATAL: Error inserting vboxadd (/lib/modules/2.6.24-21-generic/misc/vboxadd.ko): No such device

---

### Post by SIGTERMer on 2008-11-14
- are you sure that you installed the correct version? (matches current kernel version)
- are you sure apt-get finished its job through without errors?

---

### Post by johnhouk on 2008-11-14
its in my applications menu but not the installed only list of addremove. It does run and configure untill i start the vm.

---

### Post by SIGTERMer on 2008-11-14
i'm sorry, i should have been more clearer with my questions..

- are you sure that you installed the correct version of "virtualbox-ose-guest-modules-[]-generic"?

---

### Post by SIGTERMer on 2008-11-14
make sure it matches your kernels version. you can check by typing:
uname -r

---

### Post by johnhouk on 2008-11-14
how do i check the other?

---

### Post by johnhouk on 2008-11-14
i have a 2.6.24-21-generic and installed a 1.5.6_OSE
is this right... er   wrong?

---

### Post by SIGTERMer on 2008-11-14
[repeat] make sure it matches your kernels version. you can check by typing:
uname -r

---

### Post by SIGTERMer on 2008-11-14
then make sure you typed:
sudo apt-get install virtualbox-ose-guest-modules-2.6.24-21-generic

retype it again, it should tell you if you have already installed this package.

if everything checks out, try running virtualbox the way i do it:
sudo virtualbox

ps: i am also running 2.6.24-21 and vb 1.5.6_OSE :)

---

### Post by johnhouk on 2008-11-14
where do i get the kernel version or is that it. if that is it, where do i get the vboxs package version or whatever you call this.

---

### Post by SIGTERMer on 2008-11-14
sorry about the delay - very slow connection :(

the output of uname -r should give you the kernel version which according to you is 2.6.24-21-generic

make sure you installed the kernel dependent package by retyping:
sudo apt-get install virtualbox-ose-guest-modules-2.6.24-21-generic

then, type: sudo virtualbox

it should work

---

### Post by johnhouk on 2008-11-14
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

---

### Post by johnhouk on 2008-11-14
john@ubuntu:~$ sudo apt-get install virtualbox-ose-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-ose-modules-2.6.24-21-generic
The following NEW packages will be installed:
  virtualbox-ose-modules-2.6.24-21-generic virtualbox-ose-modules-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 331kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by SIGTERMer on 2008-11-14
man you'll want to kill me for this mistake..
you installed the wrong package, type this:

sudo apt-get install virtualbox-ose-modules-2.6.24-21-generic

after this type: sudo virtualbox

this time it should make the thing work! sorry again for the mistake :D

---

### Post by johnhouk on 2008-11-14
sorry i was trying to use firefox portable and i experenced my first freeze up, wheres my task manager?... i don't remember if the install finished ill rerun the command

---

### Post by johnhouk on 2008-11-14
Hey that worked.

Too bad you don't know about [how to make files run pre OS]("http://ubuntuforums.org/showthread.php?p=6174011")

---

### Post by johnhouk on 2008-11-14
I got setup to run, but the [disc format freezes everything.]("http://ubuntuforums.org/showthread.php?p=6176650")

---

### Post by SIGTERMer on 2008-11-14
can you be more specific? setup of what? and what format disk?

---

### Post by SIGTERMer on 2008-11-14
ok, just saw other thread. switching to it now :)

---

