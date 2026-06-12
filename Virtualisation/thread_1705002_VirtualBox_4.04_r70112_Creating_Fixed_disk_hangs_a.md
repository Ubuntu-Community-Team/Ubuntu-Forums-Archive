---
title: "VirtualBox 4.04 r70112: Creating Fixed disk hangs at 0%"
date: 2011-03-11
forum: Virtualisation
---

### Post by astrobob.tk on 2011-03-11
Hey guys,

I recently updated my virtualbox on Ubuntu 10.04. I had 2 boxes running, one of which was Win 7 with a 20GB dynamic disk & needed to expand it. AM not sure if there's a way to expand it at such time but anyhow I resorted to removing the box, updating VB OSE to the latest version 4.04 r70112 & trying to reinstall a new one.

I went through the wizard to create a 40GB fixed disk but when I start the creation process, it hangs at 0% & my CPU (Core 2 Duo) rises to 100%. I tried several times doing this & the same thing persists. I can't even stop it (not even by a kill command); I always have to reboot the system.

Could you please help me figure out what's going on ?

P.S.: I downloaded the latest version from VB's website.

thank you in advance

---

### Post by Hedgehog1 on 2011-03-11
***astrobob.tk; the path names are Unix/Linux style below, but this works in windows with windows paths.***

[SIZE="3"]Expand the hard disk size in Virtual Box:[/SIZE]

If I have a 10 gig **Ubuntu.vdi**, but I now need a 20 gig one; here is how to go about it.

First, create a new 20 gig **Ubuntu_20.vdi** using the Oracle VirutalBox Manager.

Second, use the: **VBoxManage clonehd &#8211;existing** to copy the contents of the smaller Ubuntu.vdi into the new larger Ubuntu_20.vdi

You must use the "--existing" option to copy the contents of one **vdi** into another.

```
VBoxManage clonehd &#8211;existing &#8220;/home/hedgehog/VirtualBox Vms/Ubuntu1010/Ubuntu.vdi&#8221; &#8220;/home/hedgehog/VirtualBox Vms/Ubuntu1010/Ubuntu_20.vdi&#8221;
```

Next, switch the virtual machine to the new **vdi** disk and start your 'cloned' OS.

Use Disk Management to extend the volume to occupy all free space.

***The Hedge***

:KS

---

