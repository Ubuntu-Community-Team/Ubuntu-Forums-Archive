---
title: "Raising Resolution on Virtualbox"
date: 2010-03-12
forum: Virtualisation
---

### Post by iTrascurato on 2010-03-12
I have my Ubuntu Virtualbox machine up and running.  I've been looking forward to following this:  [http://www.ehow.com/how_2343701_screen-resolution-ubuntu-virtual-box.html](http://www.ehow.com/how_2343701_screen-resolution-ubuntu-virtual-box.html)

That way I can get the resolution much higher than the current max of 800x600.  However, when I cd into the cdrom, there is a folder called OS2 with a few things inside, and nowhere can "VBoxLinuxAdditions.run" be found.  I just need to run that and restart it, but the file doesn't seem to be on my disk.  This is Ubuntu 9.10 desktop, by the way.

Does anybody have that file that they can send me, or can you point me in the right direction?

Thanks.

---

### Post by sv87411 on 2010-03-12
Which version of VirtualBox did you install - the Ubuntu repo version or of the one off of the official website?

Also, can you confirm you are following step 3? "Go to top of virtual window, click on devices then select "Install Guest Additions"" and that you are indeed seeing a new CD ROM mounted on your virtual Machine. 

Do the files you see in /media/cdrom still exist if you disconnect the VirtualBox guest additions ISO?

EDIT: Also, I trust you are looking inside the /media/cdrom0 directory **on your virtual machine** not your main host machine.

---

### Post by Beowulf.1000 on 2010-03-12
I had the same issue (solved) with a virtual WinXP inside Linux. Once I installed the guest addition I got full screen Windows. You just press Ctrl+f to go full screen and get the high resolution (1600x900 on my machine).

---

### Post by iTrascurato on 2010-03-12
Sorry guys, let me further clarify.  This is a Ubuntu virtual machine that is installed on my work (host) machine, which is Win 7.

It did mount "VBOXADDITIONS_3.".

```
ls -l /media/cdrom0
OS2
Readme.txt
```

```
ls -l /media/cdrom0/OS2
gengradd.dll
libc063.dll
readme.txt
VBoxGuest.sys
vboxmouse.sys
VBoxService.exe
```

---

### Post by howefield on 2010-03-12
Have a browse here

[http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

---

### Post by iTrascurato on 2010-03-12
> **howefield said:**
> Have a browse here

[http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

Same tutorial as the one I linked to, essentially.


Fixed my own issue though.  The Ubuntu CD was still in.  I took it out, restarted, then mounted guest additions again and got all of the included files that should be there.  Very odd.

---

