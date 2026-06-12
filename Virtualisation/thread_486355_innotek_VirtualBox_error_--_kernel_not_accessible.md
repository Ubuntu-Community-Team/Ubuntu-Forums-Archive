---
title: "innotek VirtualBox error -- kernel not accessible"
date: 2007-06-27
forum: Virtualisation
---

### Post by johnnybgood115 on 2007-06-27
All, 

I am trying to install a virtual wndows machine onto my ubuntu box.  However, when using VirtualBox I receive a lengthy error which reads: 


[INDENT][INDENT][SIZE="2"]The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/SIZE][/INDENT][/INDENT]



If you guys, and girls, have any idea how I can get around this or what this error means it would be greatly appreciated.  Do I just need to logout??  

Thanks in advance!

---

### Post by bodhi.zazen on 2007-06-27
You need to add yourself to the ***vboxusers*** group

Do this under "users and groups"

You then need to log out and back in for the changes to take effect ;)

---

### Post by Ripfox on 2008-01-17
Users and Groups in VB? Or in Ubuntu? Where do I find that setting/config file?

---

### Post by bodhi.zazen on 2008-01-17
On the Ubuntu host, where you installed VirtualBox

---

### Post by Ripfox on 2008-01-18
Right, figured it out!

---

### Post by Dissident85 on 2008-02-14
I am having the same problem... but when i try to add my self to the user group it just doesn't seem to save.. i open "system > administration > users and groups" then i went to manage groups and found the vboxusers group and ticked my name then click ok... but if i open it back up my name is un ticked??? wtf??? please help!

---

### Post by bodhi.zazen on 2008-02-18
> **Dissident85 said:**
> I am having the same problem... but when i try to add my self to the user group it just doesn't seem to save.. i open "system > administration > users and groups" then i went to manage groups and found the vboxusers group and ticked my name then click ok... but if i open it back up my name is un ticked??? wtf??? please help!

If all else fails, edit /etc/group manually.

```
sudo cp /etc/group /etc/group.bak
gksu gedit /etc/group
```

Add your user at the end of the vboxusers line.

Save your changes and lcose gedit. Log off and back on (you need to do this for the changes to take effect).

---

### Post by linuxtoindia on 2008-04-02
> **ripfox said:**
> Users and Groups in VB? Or in Ubuntu? Where do I find that setting/config file?
thanks! got the answer!

just in users and groups!

---

### Post by loneowais on 2008-06-28
I have added myself to users..i did this before in gutsy...it worked fine then..

but now its not working even by adding the users..

i am using the xxx.16 kernel

installed virtualbox kernel module xxx.16 also

still no luck...

and  hey, i'm using Sun xVM Virtual Box...not the OSE

---

### Post by gkjau on 2008-07-06
i have the same problem
i tried to add manually but my user is already there:
> vboxusers: x :125:myuser(without space beside 'x')
i use xx.19 kernel
thx

---

### Post by gkjau on 2008-07-08
i solved the problem...
thanks anyway

---

### Post by rlindsley on 2008-07-28
Hi there,

I am completely new to this.  I am having the same problem.

When I go into the userlist, I am listed in vboxusers.  I also edited the group file, where I am listed as well.  Specifically here's how it is listed:

vboxusers:x:1001:rlindsley,root

Is there something I am missing?  I have logged in and out but to no avail.

Thanks in advance!
Robert.

---

### Post by rlindsley on 2008-08-02
Hi there,

Does anybody have any thoughts on this?  I would love to make Linux my primary OS, but I need virtualization for certain things (iTunes, etc).

Any thoughts on this would be much appreciated!

Thanks,
Robert.

---

### Post by bodhi.zazen on 2008-08-03
You have several options for virtualization, each has advantages and disadvantages.

Most people seem to solve the issue you are having with VirutalBox by installing the closed source edition obtained from sun :

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Alternate would be VMWare Server :

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934")

---

### Post by crhylove on 2008-08-03
This is a horribly common bug that MANY people have run into.  I hope it is fixed for the next version of Ubuntu, or maybe even patched soon!

I LOVE virtualbox, once I got it up and running. :)

---

### Post by rlindsley on 2008-08-03
Hey there,

I got VirtualBox running!  Installing it from the Sun site worked for me.  I can't wait to get this my OS installed.  Thank you VERY much!

I am now doing research on how to get a physical partition running within VirtualBox, as I already have Windows XP installed on this machine.

Any thoughts on how to get this running in VirtualBox?  Thanks again!
Robert.

---

