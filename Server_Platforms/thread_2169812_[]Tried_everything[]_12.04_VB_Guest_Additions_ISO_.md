---
title: "[?]Tried everything[?] 12.04 VB Guest Additions ISO not working"
date: 2013-08-23
forum: Server Platforms
---

### Post by Cocolate on 2013-08-23
I am extremely frustrated and I am extremely confused. I must have read 50+ threads with workarounds to fix VirtualBox. I have tried everything I could find online and I really didn't want to make a thread about it. I just want to finish the installation and move on... but of course with my onslaught of problem after problem with everything I have been working on since installing the OS this just wont "come through"...

First my machine is a UEFI specification motherboard. Which means only "certain OS's" will work with it, for now.

That should not have any effect on my VirtualBox.....unless thats why I cannot fix it.

*I am running Ubuntu 12.04 and my guest OS is BT5*
I downloaded VB from oracle official dwnld- 4.2.16
Downloaded & installed the extension pack for my version
I installed 'Users and Groups' and checked my username under the Vbox location
I enabled the USB 2.0 Controller in VB settings and 'added filter from device' (my pendrive)
I downloaded the ISO for the guest additions. Here is the best tut I found for dat  >> [http://xmodulo.com/2013/07/how-to-install-virtualbox-guest-additions-for-linux.html](http://xmodulo.com/2013/07/how-to-install-virtualbox-guest-additions-for-linux.html)

The last part of the tut **does NOT** show the correct output for guestadditions with grep command


 **$** *lsmod | grep vbox *


```

vboxpci                22911  0 
vboxnetadp             25617  0 
vboxnetflt             27271  0 
vboxdrv               285068  3 vboxpci,vboxnetadp,vboxnetflt

```
 
I've had problems with getting my output to show the correct 

> 
vboxvideo              12611  0
drm                   286313  1 vboxvideo
vboxsf                 39557  0
**vboxguest             235614  2 vboxsf **


I have successfully 'mounted' the ISO, but I have had a massive issue trying to clearly see that its successfully installed.

I cannot seem to mount it now after restarting my whole system and when I try to boot my USB from VB I always get error 

```

FATAL: No bootable medium found! System Halted
```

Opening VB and selecting "install guest additions" the 'Devices' menu does nothing. I presume I am not understanding the guestadditions ISO portion and I have exhausted my resources through Google with no solution.

What am I missing? Please

---

