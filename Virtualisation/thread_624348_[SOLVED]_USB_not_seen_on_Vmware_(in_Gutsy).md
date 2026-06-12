---
title: "[SOLVED] USB not seen on Vmware (in Gutsy)"
date: 2007-11-26
forum: Virtualisation
---

### Post by JustinAlf on 2007-11-26
I'm trying to dump Audio onto my Sony HD Minidisc player. (I know I know, I"m getting a Sandisk Sansa for Christmas.)  

I have a Vmware server set up with Windows XP.  I have 3 usb cords plugged into my computer.  1 is to a Sandisk USB 2 GB drive, 2 is a dell printer.  Both are recognized by Gutsy.  My Sony HD Minidisc player is NOT recognized.  

When I start up the Vmware windows XP, I cannot see any of the USB devices, even though Gutsy will see them.  I had everything working very well under Edgy, Feisty, even Dapper!  Does anyone know how I can get this working so that my Windows Virtual console will see my USB devices and I can use my Minidisk player!?  Any Help would be greatly appreciated.

---

### Post by HermanAB on 2007-11-26
Install VMware tools inside the Windows XP guest.  You can get the tools package as part of the VMware Workstation download.  Get the evaluation version of Vmware Workstation - it costs nothing - and the tools package is in there.  Run it from inside Windoze XP to install it.

---

### Post by JustinAlf on 2007-11-27
I'll give that a try. but I've got the workstation server now with the tools already downloaded, why won't it work that way?

---

### Post by JustinAlf on 2007-11-27
NM got it.  THanks for the help

---

### Post by arun_gopalan on 2007-12-02
Hi There

What is the solution to this? I installed vmware-server-distribution and from inside the windows XP i installed the vmware tools. Isnt that sufficient? Do I have to install the VMware workstation also?

Please let me know.

I also cannot see the usb devices in XP.

Arun

---

### Post by psypher on 2007-12-04
I wouldn't say that is the solution. If you are still having trouble go to this thread:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3890874#post3890874](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=3890874#post3890874)

there are 2 solutions

---

