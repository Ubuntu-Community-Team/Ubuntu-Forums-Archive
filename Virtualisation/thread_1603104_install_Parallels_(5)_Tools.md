---
title: "install Parallels (5) Tools"
date: 2010-10-22
forum: Virtualisation
---

### Post by steelbom on 2010-10-22
Hi,

I've got Ubuntu 10.10 and I'm trying to install Parallels Tools, it tells me to open a terminal, mount the DVD drive with the "noexec" flag disabled and go to CD/DVD root directory and run the "sh install" command with root privileges.

So, I've opened the DVD root directory and I see the file "install", I've opened a terminal and I'm typing "sudo sh install" and it says it can't open install; I imagine I'm not using the full directory so I tried "sudo sh /media/Parallels Tools/install" and it just says it can't open /media/Parallels -- I'm not sure what to do about the space in the name, or even if thats the right directory.

Can anyone let me know what I'm doing wrong? Thanks.

---

### Post by Michel66 on 2010-10-25
Hi,

Just open Terminal under 'Applications' - 'Accessories' and Terminal.
Them at :~$ type cd .. in Terminal twice.
Type 'ls' still in Terminal and should get a list of folders and files in that directory.  You should see a folder called "media"
Now type 'cd media'
If you type 'ls' again you should see "Parallels Tools".
Double click on "Parallels Tools" on your desktop.  It should open the Virtual CD and you should have a file called 'install'.
In Terminal type sudo and drag the file 'install'.
In Terminal you should see something like this:

:/media$ sudo '/media/Parallels Tools/install' 

Use the arrow key until you able to enter Tools/./install

Type your password, and it's a go!

---

### Post by jensopetersen on 2010-11-05
Parallels Desktop 5 does not work with 10.10. At least, version 5.0.9376.599993, the latest at the present moment, does not. Installing the tools is the problem.

<http://forum.parallels.com/showthread.php?t=105053&page=2>

Hopefully, a update will come soon!

Jens

---

