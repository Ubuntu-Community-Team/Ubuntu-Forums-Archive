---
title: "rip/shrink DVDs with server - ssh - no gui"
date: 2008-04-04
forum: Server Platforms
---

### Post by jimmy the saint on 2008-04-04
I have a an ubuntu server box set up as a file/media server.  I would like to be able to throw a DVD into the drive and, via ssh, command it to rip the DVD to MP4 or some other smallish format. Basically, I would like to do what K9copy does, only through the command line.  

I have looked at a few of the popular software packages, but they all seem to be gui only.  I would rather not install the full desktop environment, especially since there is no monitor and keyboard attached to the machine.

I am not looking for a DVD-9 to DVD-5 app.  I would like to be able to control the output so that I can get smaller files.

Any suggestions? 
Thanks in advance!!

---

### Post by mrsteveman1 on 2008-04-04
You're gonna need a script for this sort of thing, and perhaps even some udev rules if you want to automate the ripping every time a dvd is inserted (ssh not required etc).

I know the handbrake people have some scripts for automated ripping in OS X, perhaps they have something pre written for linux as well, or perhaps handbrake itself can simply be called with the right arguments.

There is in fact a CLI only version of handbrake, which is what you probably want to use.

---

### Post by zackboarman on 2008-04-05
you might want to give mencoder a try, it has several options, but it does support MPEG 4. so it should fit your needs. and it's a command line program to, so it'll work just fine in your case.

---

### Post by jimmy the saint on 2008-04-05
Hey that handbrake looks like just the ticket.  There are a few scripts out there that make the cli version a lot easier.  The one problem I have with the CLI is that I have been using linux for less than a year, and my mind is still firmly in GUI mode.  It is difficutl to remember all the neccessary options to include in such a complex task when they are not right in front of me!

Thanks a lot Mrsteveman!!!

---

### Post by jimmy the saint on 2008-04-06
Handbrake does indeed look good, but when I attempt to run it via and ssh connection to the server, it says permissin denied.

---

### Post by jimmy the saint on 2008-04-06
That was my fault.... I played with the file permissions a bit.  They either got changed when I ftp'd them over, or the permissions that worked on my laptop did not work on the server.   I am running my first rip with this software.  Thanks for the suggestion, it solved my problem!

---

