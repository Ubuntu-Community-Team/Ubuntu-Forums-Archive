---
title: "[SOLVED] Grub Error 18"
date: 2008-03-04
forum: Server Platforms
---

### Post by radioraheem on 2008-03-04
I have an older machine that I'm using as a server.  I previously installed server 7.04 on it without any problems.

Yesterday I decided to put the server back online, and I gave it a fresh format using server 7.10.  

Now, after the installation, Grub fails with Error 18 (basically means the disk is too big for what the BIOS will support).

What I don't get is why this wasn't an issue with the original setup.  I had no problems with the first installation and the server worked fine.

I have already tried the "install ubuntu with the hard drive in LBA mode and then switch the BIOS back to Auto" trick and it did not work.  Still get Error 18 when trying to start up.

The BIOS for this machine has LBA, Large, Normal, Match Partition Table, and Manual options available.  

Does anyone have any suggestions on how I can make this server work again?  I even tried another install using my server 7.04 disk and now it also has the same problem.

I'm very perplexed because nothing about the hardware has changed, and no BIOS settings were changed since the previously working install was on the server.

Thanks in advance for any help!

---

### Post by MJN on 2008-03-04
It's not so much that the disk is too big for the BIOS to support, but rather that the kernel has ended up in a position on the disk that the BIOS cannot access directly.
 
The solution (assuming this is the problem, Error 18 can arise in some other circumstances too) is to ensure that you have a small (say, 50MB) partition at the beginning of the drive - this can then be mounted as /boot and will contain your kernel. The BIOS will be able access this partition and load the kernel, which can then take over to access the rest of the disk.
 
I haven't gone through a fresh intall for years now so you may wish to dig around, or ask someone, for advice on the exact steps required in the installation process to put a boot partition at the beginning of the drive.
 
The reason you have only just now stumbled into this problem could well be that you were just lucky with where your kernel was positioned last time, or perhaps you are now using a different partitioning layout.
 
Mathew

---

### Post by radioraheem on 2008-03-04
Well, I created a 100MB partition at the start of the disk and had the setup cd auto-partition the rest of the drive.

Same problem, even after switching the drive in BIOS back to Auto from LBA.

How do I know for sure that it installed the kernel into the correct partition?  Is there a way I can check the partitions out considering grub won't complete the load and I can't reach a terminal?

Also, I'm not 100% sure I set the 100MB partition correctly with the install CD.  I set it to be bootable, mount on /boot, and that was it.  Are there any other partition options I need to select?

Sorry for the lack of knowledge here.  Normally (with desktop setups anyway) I just let the live cd auto-partition and then alter them once the install is done as needed.

---

### Post by MJN on 2008-03-04
You could boot with a 'LiveCD', mount the first partition, and see what's on it. The 100MB partition was the first partition right?

However, the installer should have made it pretty clear what it was going to use each partition for (e.g. where / was going, where your swap was going, and hopefully where /boot was going!)

Perhaps the cause of the problem is something else....

Mathew

---

### Post by radioraheem on 2008-03-04
MJN Please read over my previous response again, I think you were replying when I was updating it with more details.

---

### Post by MJN on 2008-03-04
Yeah it looks I did!

Try booting with the Ubuntu LiveCD and then you can inspect what's in your first partition.

Mathew

---

### Post by radioraheem on 2008-03-04
Well, I think I found a bug in the installer that I read about in another somewhat related forum post ...

When I loaded up a live CD the 100MB partition was no longer labeled as bootable, and the primary storage partition was made the boot partition.  It seems something in the installer changes this immediately after a manual partition scheme is setup or during the package installation process.

I made sure that the 100MB partition was set to be bootable and now the system is firing up without a problem.

Thanks a ton for all your help!!!  :)

---

### Post by MJN on 2008-03-04
Nice one - thanks for posting back as it'll be sure to help others.

Mathew

---

