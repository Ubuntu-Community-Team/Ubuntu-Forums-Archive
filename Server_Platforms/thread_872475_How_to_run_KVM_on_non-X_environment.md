---
title: "How to run KVM on non-X environment"
date: 2008-07-28
forum: Server Platforms
---

### Post by satimis on 2008-07-28
Hi folks,


Ubuntu 8.04 server amd64, headless
KVM 1:62+dfsg
QEMU 0.9.1
OpenSSH 1:4.7p1


On running
# kvm -m 750 -cdrom /dev/scd0 -boot d ubuntu6.06.img```


     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15) 
(*) Direct/Memcpy: Using libc memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL - exiting

```


Please advise how to fix the problem.  TIA


B.R.
satimis

---

### Post by cprofitt on 2008-07-28
I have not tried it yet, but perhaps this will help -- [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by cariboo on 2008-07-29
I just used the previous poster's link to install kvm. I'm using intrepid alpha 3 and didn't run into any problems.

JIm

---

### Post by satimis on 2008-07-29
Hi PrivateVoid and cariboo907,


Thanks for your advice and URL.


I was following;
[http://www.howtoforge.com/using-kvm-on-ubuntu-gutsy-gibbon](http://www.howtoforge.com/using-kvm-on-ubuntu-gutsy-gibbon)

installing KVM and got in the midway.  It'll be difficult for me to follow the Ubuntu guide unless I wipe out the HD completely and start over again.


The VM is running on the background.  I can't bring it to foreground.  I don't have vncview running on the local desktop.  Nor I know which package is needed.  I'm still fighting my way.


B.R.
satimis

---

### Post by satimis on 2008-07-29
Hi folks,


I got my problem solved by running Knoppix 5.1-1 LiveCD on local desktop PC which has vncviewer installed. (even it is not completely)


On server run following command;
# kvm -hda ubuntu6.06.img -cdrom /dev/scd0 -m 512 -boot d -vnc :1


After starting Knoppix on local desktop run;

$ vncviewer 192.168.0.110:1 (server LAN IP)```

Connected to RFB server, using protocol version 3.7
No authentication needed
Desktop name "QEMU/KVM"
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8
blue 0
Using default colormap which is TrueColor.  Pixel format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 63 blue 31, shift red 11 green 5 blue 0
Using shared memory PutImage
ShmCleanup called

```


The installation window started.  I think I can proceed installing the guest OS?  However I stopped here because I can't bring the mouse in action over the said window.  Nor the keyboard did function well.  How to improve them?  TIA


Another question;

If I need to do all steps remotely on local desktop I need to start 2 Xterms, one to ssh connect the server.  


One to run the command;
# kvm -hda ubuntu6.06.img -cdrom /dev/scd0 -m 512 -boot d -vnc :1

it will hang after executing the command


Another Xterm to run;
# vncview 192.168.0.110:1


Is there a clue?  TIA


B.R.
satimis

---

### Post by antono on 2008-09-23
> **satimis said:**
> Hi folks,


Ubuntu 8.04 server amd64, headless
KVM 1:62+dfsg
QEMU 0.9.1
OpenSSH 1:4.7p1


On running
# kvm -m 750 -cdrom /dev/scd0 -boot d ubuntu6.06.img```


     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15) 
(*) Direct/Memcpy: Using libc memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL - exiting

```


Please advise how to fix the problem.  TIA


B.R.
satimis

connect to your server with "ssh -X user@server" to enable X forwarding.

And your local X server will render Qemu :)

---

