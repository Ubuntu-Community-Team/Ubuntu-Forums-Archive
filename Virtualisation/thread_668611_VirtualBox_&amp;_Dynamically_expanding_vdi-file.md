---
title: "VirtualBox &amp; Dynamically expanding vdi-file"
date: 2008-01-15
forum: Virtualisation
---

### Post by olavjunior on 2008-01-15
I used the dynamically expanding drive option. But my xp soon got out of space, and the drive ain't growing. When I look at the hard-disk details, it's listed as 2 GB normal. Thought that was odd, so I created some new disks to check, and they all got listed as normal. I've got a feeling it should be dynamic or something like that. 

Anyone else having this problem?

---

### Post by john6six on 2008-01-15
The 2 GB is the size the disk can grow to. It is dynamic in size, but once you hit 2 gig it stops growing. 

The normal relates to whether the vdi is a normal image, immutable image or write through image.

---

### Post by olavjunior on 2008-01-15
Thanks! I started to suspect that that was the case... So now I have to do the windows-installation all over again? No way of expanding this image?

---

### Post by Jose Catre-Vandis on 2008-01-15
Try making a backup image of your existing vbox, then create a new larger virtual hard disk, attach it as your primary, then restore your image. Works on real hardware so should work in the virtual world too?

---

### Post by olavjunior on 2008-01-16
I'm gonna try that later on when I get home. 

But now another problem has araised. Maby I'll post it in a new post, but it's odd that it happened now that I installed VirtualBox. 

After reboot, Ubuntu din't find my display, even though xorg.conf is the same. i had to remove the nvidia driver and replace it with nv, and run metacity. Is this a familiar problem????

EDIT: Installed the latest nvidia driver, and fixed the xorg. Works fine now. Don't know what broke it though, maby WirtualBox, but whatever, it's working now :)

---

