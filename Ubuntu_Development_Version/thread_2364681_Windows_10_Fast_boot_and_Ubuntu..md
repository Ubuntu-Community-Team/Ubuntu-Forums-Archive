---
title: "Windows 10 Fast boot and Ubuntu."
date: 2017-06-26
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-06-26
I am not sure where to post this, sorry if it's the wrong forum.  I have been dual booting with ubuntu 16.04.2 and now with ubuntu17.10.  Maybe I missed the news, but I did not realize until today that I forgot to uncheck fast boot in windows 10.  But for some reason grub2 boots up fine and I can run either os with no problems.  So when has this issue been implemented, or has it?.

Running windows 10 creator's update and ubuntu 17.10.

Henry.

---

### Post by howefield on 2017-06-26
You appear to have Ubuntu successfully installed, so "*Installation and Upgrades*" isn't the place.

Moved to the "*Ubuntu Development Version*" given the tenuous link to 17.10.

---

### Post by Hewjr100 on 2017-06-26
Sounds good to me.

Henry.

---

### Post by Chanath on 2017-06-27
> **Hewjr100 said:**
> I have been dual booting with ubuntu 16.04.2 and now with ubuntu17.10.  Maybe I missed the news, but I did not realize until today that I forgot to uncheck fast boot in windows 10.  But for some reason grub2 boots up fine and I can run either os with no problems.  So when has this issue been implemented, or has it?.

Running windows 10 creator's update and ubuntu 17.10.

Henry.

I believe the only problem you'd have with fast boot unchecked would be that you won't be able to access the files in the Windows install from Ubuntu. Windows is sleeping, and if you untick fast boot, it'd close fully. Then those files are accessible. At least that's what's happening in my laptop.

---

### Post by Hewjr100 on 2017-06-27
I see, gonna check that out in a while.  Thanks

Henry.

---

### Post by oldfred on 2017-06-27
UEFI fast boot or Windows fast start up? They are different settings.

I never understood why fast start up setting prevented grub from Booting Windows in UEFI boot mode. Windows boot file is in ESP - efi system partition and grub is just chaining to the Windows .efi boot file. I did not think the fast start up hibernated the ESP, but only all NTFS partitions.

I think I did see where grub had some updates to improve some Windows issues, but thought that was part of the official grub2 , not the beta we have been using for years.
[http://git.savannah.gnu.org/cgit/grub.git/tree/NEWS?utm_source=anz](http://git.savannah.gnu.org/cgit/grub.git/tree/NEWS?utm_source=anz)

---

### Post by Hewjr100 on 2017-06-27
I just reinstalled windows 10 with efi and gpt partition.  The previous install was legacy and it did in fact boot to grub2 while windows was in fast startup, and booted both without a hitch.
Now I have to try it in efi?
Heny.

---

### Post by Hewjr100 on 2017-06-27
hmm, I see google has a lot of hits to dual boot ubuntu with efi gpt setup, but most are for ubuntu 16.04 or older.  Any recent articles with ubuntu 17.04?

---

### Post by oldfred on 2017-06-27
It should all be the same.
Install for any Windows in UEFI mode (except Windows 7 in UEFI does not support UEFI secure boot) and all recent UEFI bootable versions of Ubuntu are the same. 

Generally newer version work better as improvements are made. Same with UEFI/BIOS versions from vendors.

With nVidia you need nomodeset manually added to grub menu to boot installer & first boot after install or until you install proprietary driver from repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

General UEFI install instructions and many links are in link below in my signature.

---

### Post by Hewjr100 on 2017-06-28
For the time being I am going to hold off installing Ubuntu 17.04.  I am down to my last flash drive, which has windows 10 creators update media.  Not going to delete it and install Ubuntu on it, in case dual boot fails.  Saturday I get my Social Security check and will buy a new flash drive

---

