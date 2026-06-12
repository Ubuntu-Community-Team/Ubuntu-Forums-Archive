---
title: "LTSP - Pendrive plugged on server appears on all terminals"
date: 2009-05-11
forum: Server Platforms
---

### Post by Guevara76 on 2009-05-11
I am more of a user LTSP 5.0 on Ubuntu 8.04.2, but I'm having some problems,
these are the details:

Server - Ubuntu 8.04.2
Machine - Pentium dual core, 4GB of ram
The terminals have lighter adapter PCchips M571 and M598, all with the USB
cable plugged in front of the cabinet connector which gives support to usb,
the J7 connector if I am not mistaken.

The problems are:

- When a spit of Pendrive in terminals sometimes mounts and sometimes not, with many attempts, which in tests with only one
machine connected to the server directly with a cable, the problem persists,
when all 20 machines were connected to a switch then this happened again,
the manager of the network has not said the switch configuration and some
that could not cause any problem.

- [B]When the Pendrive spit on the server appears in all the 20 terminals
Pendrive being assembled.[/B](this is not the correct) ---> This is the big problem, I edit udev rules in the 
server and in the chroot ltsp on /opt/ltsp/etc/udev. I try remove users of terminals of plugdev group, and not success.

- If i put users in the group of my user with powers to root, the icon
appears in the usb client on the server. (this is not the correct)


In lts.conf are the lines:
LOCAL_STORAGE Y
Module1: "usb-ohci"
Module2: "ehci-usb"

All users are in the group of Fuse and own group.

What I wanted to resolve is the bid of Pendrive that [B]appears for all the
machines[/B] and assemble in Pendrive correct terminals and not appear on the
server.
Well, that's it, grateful for the attention of anyone who can help.

---

### Post by Guevara76 on 2009-05-15
Pendrive and cdrom still appear on all terminals.[LEFT]Anyone had this problem before?[/LEFT]

---

### Post by drave on 2009-05-15
> **Guevara76 said:**
> Pendrive and cdrom still appear on all terminals.[LEFT]Anyone had this problem before?[/LEFT]

as they should

everybody logged in will be using the server root filesystem, so when you plug in a flash drive or cd-rom and it gets mounted under /media/cdrom or /media/flash or whatever,everybody can see it.  maybe an icon will appear on everybody's desktop or in nautilus or something, if they're running those

i think you can either disable them alltogther or change access permissions, but i dont know how to do either

---

### Post by Guevara76 on 2009-05-20
The users are in their own group, we tried to put the parameter "nouser" in fstab, and failed. Have not yet discovered how to prevent the cdrom and the pendrive plugged on server appear in the terminals. Thanks!

---

### Post by Guevara76 on 2009-07-16
I not found anything in the LTSP manual for ubuntu:

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

you should update the documentation so that users can find information without having to ask for help in the forum. 
 Nobody needed plug a pen drive on the server using LTSP?

[LEFT]this problem has not been answered by the team of LTSP.

thanks.
[/LEFT]

---

### Post by Guevara76 on 2009-07-30
Nobody??

---

### Post by Guevara76 on 2009-08-19
I still have the error.
Somebody can help?

---

### Post by smaclean on 2009-09-08
On the LTSP server, try going to System - Administration - Users and Groups, click on one of the users and choose Properties, click the User Priviledges tab, and take the check off Access external storage devices automatically, see if that works.

---

### Post by t0rtura on 2010-09-09
> **Guevara76 said:**
> I am more of a user LTSP 5.0 on Ubuntu 8.04.2, but I'm having some problems,
these are the details:

Server - Ubuntu 8.04.2
Machine - Pentium dual core, 4GB of ram
The terminals have lighter adapter PCchips M571 and M598, all with the USB
cable plugged in front of the cabinet connector which gives support to usb,
the J7 connector if I am not mistaken.

The problems are:

- When a spit of Pendrive in terminals sometimes mounts and sometimes not, with many attempts, which in tests with only one
machine connected to the server directly with a cable, the problem persists,
when all 20 machines were connected to a switch then this happened again,
the manager of the network has not said the switch configuration and some
that could not cause any problem.

- [B]When the Pendrive spit on the server appears in all the 20 terminals
Pendrive being assembled.[/B](this is not the correct) ---> This is the big problem, I edit udev rules in the 
server and in the chroot ltsp on /opt/ltsp/etc/udev. I try remove users of terminals of plugdev group, and not success.

- If i put users in the group of my user with powers to root, the icon
appears in the usb client on the server. (this is not the correct)


In lts.conf are the lines:
LOCAL_STORAGE Y
Module1: "usb-ohci"
Module2: "ehci-usb"

All users are in the group of Fuse and own group.

What I wanted to resolve is the bid of Pendrive that [B]appears for all the
machines[/B] and assemble in Pendrive correct terminals and not appear on the
server.
Well, that's it, grateful for the attention of anyone who can help.

Are you using LDM? When I use LDM in lts.conf I'm able to access pendrives... Try it. and give us a feedback please...

---

