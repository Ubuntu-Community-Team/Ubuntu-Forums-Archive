---
title: "Portable Virtual Ubuntu on pendrive/usb stick/etc"
date: 2008-11-13
forum: Virtualisation
---

### Post by Syock on 2008-11-13
Scenario: I want to use Ubuntu, installed to an external USB drive, on a PC running a Linux OS. There are limitations:
[LIST=1]
[*]Target PC cannot boot on USB
[*]I don't possess super user rights/administrator privileges
[*]The PC also won't boot on CD
[/LIST]
So a solution I'm thinking of right now is a virtual machine that runs straight from the USB. So far, I found that only QEMU runs without requiring install. But the binary I downloaded from the homepage ([http://bellard.org/qemu/download.html](http://bellard.org/qemu/download.html)) needs to be unpacked to /, which is impossible due to limitation no. 2 stated above.
What are the possible options then?


Btw, these threads have been referred:
[http://ubuntuforums.org/showthread.php?t=776960&highlight=usb](http://ubuntuforums.org/showthread.php?t=776960&highlight=usb) (no reply so far)
[http://ubuntuforums.org/showthread.php?t=724293&highlight=usb](http://ubuntuforums.org/showthread.php?t=724293&highlight=usb) (introduced QemuPuppy, which is exactly what I want, but I tried and it didn't run. The output window is blank)
[http://ubuntuforums.org/showthread.php?t=636473&highlight=usb](http://ubuntuforums.org/showthread.php?t=636473&highlight=usb) (no answer)

---

### Post by C.S.Cameron on 2008-11-13
Will a Boot CD for the USB device fit your needs?

---

### Post by bodhi.zazen on 2008-11-13
> **Syock said:**
> Scenario: I want to use Ubuntu, installed to an external USB drive, on a PC running a Linux OS. There are limitations:
[LIST=1]
[*]Target PC cannot boot on USB
[*]I don't possess super user rights/administrator privileges
[/LIST]
So a solution I'm thinking of right now is a virtual machine that runs straight from the USB. So far, I found that only QEMU runs without requiring install. But the binary I downloaded from the homepage ([http://bellard.org/qemu/download.html](http://bellard.org/qemu/download.html)) needs to be unpacked to /, which is impossible due to limitation no. 2 stated above.
What are the possible options then?


Btw, these threads have been referred:
[http://ubuntuforums.org/showthread.php?t=776960&highlight=usb](http://ubuntuforums.org/showthread.php?t=776960&highlight=usb) (no reply so far)
[http://ubuntuforums.org/showthread.php?t=724293&highlight=usb](http://ubuntuforums.org/showthread.php?t=724293&highlight=usb) (introduced QemuPuppy, which is exactly what I want, but I tried and it didn't run. The output window is blank)
[http://ubuntuforums.org/showthread.php?t=636473&highlight=usb](http://ubuntuforums.org/showthread.php?t=636473&highlight=usb) (no answer)

I believe qemu is the only option, and you can put the qemu binary on the usb drive.

[http://www.pendriveapps.com/2008/02/09/portable-qemu-manager/](http://www.pendriveapps.com/2008/02/09/portable-qemu-manager/)

[http://www.erikveen.dds.nl/qemupuppy/](http://www.erikveen.dds.nl/qemupuppy/)

The last link is working for me (both linux and windows hosts) ;)

The main problem with qemu is that it is slow, even with kqemu or other acceleration.

This is why people use Puppy or I prefer DSL, you need a light weight browser (firefox is much too slow).

---

### Post by Syock on 2008-11-13
> **C.S.Cameron said:**
> Will a Boot CD for the USB device fit your needs?
No. I should have noted that as well. I've just edited the first post to say that I cannot boot on CD

> **bodhi.zazen said:**
> 
[http://www.pendriveapps.com/2008/02/09/portable-qemu-manager/](http://www.pendriveapps.com/2008/02/09/portable-qemu-manager/)

[http://www.erikveen.dds.nl/qemupuppy/](http://www.erikveen.dds.nl/qemupuppy/)

The last link is working for me (both linux and windows hosts) ;)


The portable-qemu-manager isn't available for Linux hosts OS. And as I said in TFM, I've tried QEMUpuppy but it only outputs blank screen, at least on my own PC. Haven't tried it on the target PC yet. Btw, what did you try it on? Mine is Kubuntu Ibex. Target PC is old Redhat-based Vine Linux, I don't even know it's kernel version.

Also extra info: it seems DSL embedded was available for Linux for some time, but they somehow removed the support. Now if only I can get my hands on that...

---

### Post by bodhi.zazen on 2008-11-13
I have a portable puppy with XFCE as the Window manager. Works on Ubuntu, Fedora, and Windows XP.

[http://puppylinux.org/wiki/archives/old-wikka-wikki/categoryderivative/simplepup](http://puppylinux.org/wiki/archives/old-wikka-wikki/categoryderivative/simplepup)

---

