---
title: "Virtualization plan-of-attack"
date: 2008-05-09
forum: Virtualisation
---

### Post by UnWarierMage224 on 2008-05-09
Hi folks, 

So I've read a bunch of stuff on how to get virtualization working and it's all just got me plain confused... I happened upon an idea, which I'm not sure will work but here it is anyway: 

My current setup: 1 NTFS partition for windows XP, 1 NTFS partition for my documents, linux partitions. 
I'm probably going to grab the non-OSE version of virtualbox. 

This question has probably been asked a lot of times but is there any way I can mount my existing NTFS partition in virtualbox? I've followed a couple tutorials but at the point which these tutorials say to switch the hard drive drivers to standard IDE drivers it hoses my windows installation and I can't boot natively into windows. 

What I was thinking about doing was backing up my windows installation to an acronis diskimage and wiping that partition clean... possibly reformatting it as EXT3, then installing virtualbox in linux with windows XP, then restoring my XP from the acronis image. 

will this work or is there an easier, more comprehensive way?

Thanks, 

-'Mage

---

### Post by MusicMastaMike on 2008-05-09
As far as I know, you cannot mount a partition into VirtualBox.  I've tried before.  If you do find a way, let me know!  An idea, just throwing this out there...

Could you possibly make an acronis image (.tib) of your existing partition, and then get VMware Converter ([http://www.vmware.com/download/converter/](http://www.vmware.com/download/converter/)) to convert it to a .vmdk image (can be used by VBox)?  The problem I see arising from this is that you would be completely switching hardware, as seen by the Windows VM, since VBox emulates its own set of hardware, it doesn't necessarily pass through what your computer actually has.  I don't believe Windows plays well with hardware switches.

I would say your best bet would be to either keep your existing Windows partition as a dual-boot if you really need your current config, or to remove the partition, let Ubuntu take up your whole hard drive (or however you want to do it), install VirtualBox, and then do a new install of Windows.

Best of luck!

---

