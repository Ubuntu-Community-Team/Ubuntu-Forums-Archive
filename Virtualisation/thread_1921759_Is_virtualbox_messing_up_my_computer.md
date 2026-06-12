---
title: "Is virtualbox messing up my computer?"
date: 2012-02-07
forum: Virtualisation
---

### Post by Adam745 on 2012-02-07
I've been using Ubuntu for about 6 months now.  Still learning.  Currently running 11.10.  There's been a problem that I've had repeatedly.  Suddenly and without warning I can't boot.  After the bios screen disappears nothing happens and my computer just runs indefinitely.  I can boot to a live CD with no problem.  If I use a live CD all my files are intact.  The hard drive itself is fine.  No bad sectors.  The only way I could find to fix it is to reinstall Ubuntu.  It's happened 4 times.  Since the computer was working fine until it's turned off it took me a while to notice the pattern.  It only happened after I had installed something in virtualbox and it didn't happen every time.  I love the idea of virtual box.  I don't want to give it up.  This last time I had run the new version of Linux Mint on VB but on previous times it did it when I tried Ubuntu, and Kubuntu.  I get no error messages.  The Virtual box runs fine.  Ubuntu runs fine.  No new programs are installed.  Then suddenly I can't boot.  I have found no other complaints about this online.  I don't even know for certain that it's VB causing the problem.  Has anyone ever heard of this or have any idea how I can fix my OS without having to reload.  I have a backup but I don't want to set my computer back a month if it is a simple fix.  I know Ubuntu uses Grub for loading but i know nothing about it.

---

### Post by snowpine on 2012-02-07
Maybe a GRUB problem? (do you see the "grub>" prompt?)

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by CharlesA on 2012-02-07
Virtualbox doesn't mess with anything on the physical drive that would prevent the host OS from booting.

I'd see if grub got hosed somehow, as snowpine suggested.

---

### Post by Adam745 on 2012-02-07
I don't know what the grub prompt would look like.  There is a cursor visible on the screen for about 3 seconds then the monitor puts up a box saying "input not supported".  That is normal for the computer.  Normally this stays on the screen for about 15-20 seconds and the input returns when the login screen is available.  Now though it just stays there.  There is no hard drive activity.  The power button turns of the motherboard immediately like it does when there is no boot device.  At first I thought it was a hardware issue because I could think of no reason VB would interfere and I found no other similar complaints.  I stopped using VB because I didn't really have anything I needed it for and it didn't happen again.  Then a month or two later I reloaded VB and eventually it happened again within about 2 weeks.

---

### Post by CharlesA on 2012-02-07
What happens if you hit:

ctrl + alt + f1 ?

It should drop you to a login prompt.

---

### Post by japzone on 2012-02-07
What happens when you hold down Shift during boot? Also check your Bios to make sure the Boot order isn't messed up.

---

### Post by Adam745 on 2012-02-07
I install ubuntu on a different hard drive to allow me to use the computer but I haven't wiped the old one so I can fix it if I need to.  I already checked the bios to make sure the boot order wasn't messed up and it wasn't.  Also when I bring up the boot menu and attempt to load from that hard drive the same thing occurs.

Ctrl + Shift during boot I see the cursor says GRUB loading.  Then the screen says input not supported and I wait forever with nothing happening.  But now I know how to get to GRUB.  I didn't know that before.  I tried it with the new installation and the same thing occurred except after a few seconds it continued booting.  That tells me that for whatever reason my monitor can't show me the GRUB menu.  Is it possible my monitor's not compatible somehow?  I remember the input not supported screen came up before my windows xp installation also.  I just figured there was no signal to show until the computer finished booting.

Ctrl + Alt + F1 can only be done on the new installation.  It drops the image on the screen and shows the same input not supported.  I couldn't figure out how to get out of that once I got to it so I had to do a hard shut down.

---

### Post by japzone on 2012-02-07
What kind of Computer are you using? CPU, Model #, RAM, ect...

---

### Post by Adam745 on 2012-02-07
ASRock N68C-S UCC AM3/AM2+/AM2 NVIDIA GeForce 7025 / nForce 630a Micro ATX AMD Motherboard
 AMD Athlon(tm) 7750 Dual-Core Processor × 2 
 

 3.2 GB RAM
 

 Hitachi 160GB HD

---

### Post by japzone on 2012-02-07
There is the possibility that it has something to do with being installed to a Secondary Harddrive while the first one still exists. It may be a good Idea to wipe each drive and Reformat the Partition Table of each then install Ubuntu to the First Drive. Or simply Swap the Drives and then Reformat the Ubuntu one with a New MSDOS Partition Table and an ext3/4 Filesystem. Install Ubuntu to the Newly formatted Drive and see what happens.

Obviously I'd suggest you back up any important data to an External Drive.

---

### Post by Adam745 on 2012-02-08
I didn't install ubuntu on the new hard drive til after it happened.  That was just to get my computer working.  I think I'll just load my backup, take of VB and see if it happens again.  I don't know what else to do. Might try one of the other virtual machine programs if it doesn't happen again.

---

