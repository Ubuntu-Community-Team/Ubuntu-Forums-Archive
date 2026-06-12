---
title: "Ubuntu tutorial"
date: 2004-12-26
forum: The Cafe
---

### Post by Ozitraveller on 2004-12-26
I've got 20++ years in IT, from mainframes to mini's and pc's and used SCO unix. And I'd like to be involved in the development side of linux/Ubuntu. Where does one find out about how it all works? I've bought a couple of books and been totally disappointed. Where can I learn how linux works without having to wade through endless chapters about how vi works, and the endless commmand-line programs and their parameters?

---

### Post by TravisNewman on 2004-12-26
Hmm... one thing I've learned over the years of using Linux is that how vi works and all the command-line programs and their parameters are exactly how LINUX works. If you've got Gnome on top, that's a separate beast, as is the X server, etc, etc. If you're wondering how a specific distribution works, all I can tell you is to get books about them specifically or use the documentation on the website. One great thing about Debian and Gentoo is the massive online documentation, and with RedHat/Fedora you've got the massive amount of books published. Ubuntu hasn't really been around long enough or gotten big enough to have much of either. Ubuntu has a LOT of online documentation, but it's not organized as well as it could be.

Honestly, a good place to start is Linux for Dummies. Laugh if you want, but that book taught me a lot in '98. The O'Reilly books are great for teaching you the core of the os. Yes, that means a lot of command-line programs and their parameters, unfortunately.

---

### Post by Ozitraveller on 2004-12-26
[QUOTE=panickedthumb]Hmm... one thing I've learned over the years of using Linux is that how vi works and all the command-line programs and their parameters are exactly how LINUX works. If you've got Gnome on top, that's a separate beast, as is the X server, etc, etc. If you're wondering how a specific distribution works, all I can tell you is to get books about them specifically or use the documentation on the website. One great thing about Debian and Gentoo is the massive online documentation, and with RedHat/Fedora you've got the massive amount of books published. Ubuntu hasn't really been around long enough or gotten big enough to have much of either. Ubuntu has a LOT of online documentation, but it's not organized as well as it could be.

Honestly, a good place to start is Linux for Dummies. Laugh if you want, but that book taught me a lot in '98. The O'Reilly books are great for teaching you the core of the os. Yes, that means a lot of command-line programs and their parameters, unfortunately.[/QUOTE]


Sorry don't get me wrong I'm not in the least knocking linux (any of the varieties). I'm just impatient to learn more!

I've worked on unix (sco), but that was a while ago, so the command line doesn't frighten me, and I do use them. I'm interested to know how the building block fit together, something like an overview.

Anyway thanks for your suggestion.

---

### Post by charleyramm on 2004-12-27
I think a good way to learn what you are talking about would be to 'do' a linux from scratch system. It walks you through building a basic linux system from source. It takes a long time, and can be a bit tedious. But after finishing a LFS system you would have a BRILLIANT understanding of how linux works.

[www.linuxfromscratch.org](www.linuxfromscratch.org)  If you are serious, i would really recommend this. 

 If that doesn't appeal, i would simply suggest you try to do as many different things with your linux computer as you can. 
 Compile some software
 Compile the linux kernel. 
 Set up a web server with apache, and a bulletin board or something. 
 Set up a linux computer as your internet gateway.

Guides for just about any of this stuff can be found with google.

---

### Post by charleyramm on 2004-12-27
Ok, here's another idea. 

Bootloader (grub or lilo) loads the kernel, Linux.x.x.x. Which is a big ass binary file,  stored in /boot/vmlinuz.x.x.x or something like that.

 kernel starts the init process (/sbin/init or whatever) which reads from a file the list of processes to be started at boot (/etc/initconfig or something), which starts a bunch of other programs. Bash, GDM, network servers, etc.  It starts an FTP server maybe, like ws_ftpd. I really don't know alot about the init process, i just read a howto this morning, and i still have it in my head.  

Next thing you see is a login prompt, then the shell (bash)

Possibly there is a GUI installed. XFree86 or xorg, which you type startx in to bash to start. 

On top of X is a desktop environment, Gnome, KDE, Fluxbox, etc. 

GDM or XDM may replace the 'login' bit with a nice GUI login screen and allow you to choose a desktop environment. GDM is usually set to start automatically with /etc/rc.d/something or other.

 Like someone said earlier,  sort of.  Linux is based around the command line, and  a whole bunch of text files.  So vi is a pretty good starting point.  Have a look in /etc and read some config files. Find the file that loads all those processes when your computer starts, I dont remember what it is. Maybe you can tell me if you find it? :D

I hope that is of some help to you. It was fun thinking about it all anyway. 

 I still say, give LFS a try. Anyone would learn alot.

---

### Post by charleyramm on 2004-12-27
Text files of note, Read them, Know them, Love them. 

/etc/apt/sources.list
/etc/X11/XF86Config-4 
/boot/grub/menu.lst
 
 :-k Anyone know any more?

Programs to remember:

linux, the kernel. /boot/vmlinuz or /vmlinuz. Sometimes also bzimage, can someone explain that please?
bash The shell. /bin/bash
GDM /sbin/gdm I imagine. This is the gui login screen.
xfree86.  
I dont know what the relevant files are for gnome, kde or any of the desktops. I imagine they are complicated. Anyone know about this?

I dont know whether to just skip the standardy unix stuff.

Scripts are important for a lot of linux functionality. Ubuntu, so i'm told uses a lot of python. More traditionally perl is used, or shell scripts. /usr/bin/python and /usr/bin/perl

 I hope people can add to this, because not most importantly i would like to know more of this sort of stuff.  
 
 ;)

---

### Post by Ozitraveller on 2004-12-27
Thanks Charleyramm! This is all good stuff.

I remember seeing a discussion between a school teacher and some of the developers/mods, about writing a textbook for him to be used in teaching school kids with IT/linux/Ubuntu.

I think it was made into a wiki, but I can't find it. Maybe it'll turn up again.

---

