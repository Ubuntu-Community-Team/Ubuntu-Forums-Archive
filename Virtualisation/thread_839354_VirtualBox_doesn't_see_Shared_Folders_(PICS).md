---
title: "VirtualBox doesn't see Shared Folders (PICS)"
date: 2008-06-24
forum: Virtualisation
---

### Post by Literati on 2008-06-24
Hi all,

I'm trying to run Windows XP in VirtualBox on my Ubuntu 8.04 PC
I'm doing this for the SOLE PURPOSE, of connecting my Zune to it, and transferring songs.

As shown in the screenshot, I've shared my home folder and am trying to view it in VirtualBox Shared Folders (I've enabled Guest Additions) but it's not showing up.

Any idea what I've done wrong? Or how to fix it?

I CAN however, view my /home folder over the network, it'll see it, and let me access it.
Just, I can't map that as a drive on my XP Guest, which I'd like to do (as it'd make things easier)

---

### Post by nelsencd on 2008-06-30
Try typing \\vboxsvr\home in Run.

---

### Post by prshah on 2008-06-30
> **Literati said:**
> 
Just, I can't map that as a drive on my XP Guest, which I'd like to do (as it'd make things easier)

To map the shared folder to a drive, in your guest Windows XP, open a command prompt: Start-Run-```
cmd
``` Enter. In the black box that comes up, give the command```
net use x: \\vboxsvr\home
``` Drives mapped in this fashion are persistent across reboots. (Replace x: with the drive letter you'd like to use.)

Note that giving Windows XP full access to your entire /home is a _bad_ idea; share just the specific folders you'd like, eg /home/user/Pictures or /home/user/Music, etc.

---

