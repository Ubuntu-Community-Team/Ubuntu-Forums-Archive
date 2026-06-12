---
title: "Setting up Software RAID on Ubuntu Server 20"
date: 2020-05-21
forum: Server Platforms
---

### Post by cybercrypt13 on 2020-05-21
I've done this many times with earlier versions but version 20 install process is completely different and I'm confused.  I've searched for the steps to install a software RAID but when following them things don't work as suggested.  Here are my issues:

1) The install process for setting up disks in manual mode shows both disks and an option to setup software raid. 

2) When choosing software raid option and selecting both disks I get error stating that I can't create a raid with both drives because /boot won't have anywhere to boot from.

3) If I then back up and select to create /boot partition, the Software RAID option goes away.

So it would appear that any setup of partitions causes me to not be able to setup RAID and any setup of RAID causes problem with /boot.  So what gives and is there actual instructions to walk through this process that are correct?

I would assume both drives should have a /boot partition since it would need to boot the computer in the event the original drive crashes.

Any help would be appreciated.

---

### Post by slickymaster on 2020-05-21
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2020-05-21
From other threads here it looks like the new installer included in the -live-server- ISO has the same capabilities as the old one. Only that it looks and acts little different.

I still haven't had chances to use it too much. You have two options:

1. Play with the -live-server- installer and learn it.
2. Use the older style installer. They call it -legacy-server- now and you can find the ISO (or torrent if you prefer) hidden here: [http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/)

The -legacy-server- has the old type text installer that we are used to years ago. I have heard that for Ubuntu 22 they will not release this legacy. So I guess we will have to learn the new way then... :)

PS. That /boot warning might be from EFI boot point of view. For EFI boots you need the fat32 ESP partition (EFI system partition). In my opinion I always prefer legacy boot than efi boot, especially with mdadm.

In legacy boot you can have grub2 on each disk, so disk failure does not prevent you to boot (when raided).
In efi boot the ESP is only on one disk, so if that disk dies, no boot. Of course, you can have copy of the ESP on the other disk too, but it is additional task to keep them synced.

---

### Post by LHammonds on 2020-05-21
Have a [look here](https://ubuntuforums.org/showthread.php?t=2441984&p=13955557#post13955557).  I had same chicken-n-egg situation trying to setup LVM.

There is an awkward workaround which should work for you as well.

LHammonds

---

### Post by cybercrypt13 on 2020-05-21
Well, I would like the learn the new way but so far NOTHING is working.  I've gone through every way I can think of and any time I do any type of partition at all I lose option to do RAID. 

When you talk about EFI boot, is there a way to turn that off so it doesn't use it or is that a function of all new computers?

Thanks,

Glenn

---

### Post by cybercrypt13 on 2020-05-21
I don't see point in link you sent LHammonds.  It doesn't appear to be working with RAID or did I miss something somewhere?

Thanks,

---

### Post by cybercrypt13 on 2020-05-21
Going to try darkod's suggestion and downloading legacy install to see if I can get that to work.  At the moment I'd have to say the new install program Ubuntu is using is total junk.  I've gone through every scenario I can think of and absolutely nothing is letting me setup a software RAID.  Will report back when done.

---

### Post by LHammonds on 2020-05-21
> **cybercrypt13 said:**
> Well, I would like the learn the new way but so far NOTHING is working.  I've gone through every way I can think of and any time I do any type of partition at all I lose option to do RAID.
Then you did not read my post and understand the trick behind making the LVM/RAID option re-appear after adding a boot partition.

I just setup a VM and added two 25 GB hard disks and these are the steps I took to add a /boot partition and the rest in RAID:


[LIST=1]
[*]Select "Custom storage layout" 
[*]Select one of the available disks, add GPT partition, 1G, ext4, /boot 
[*]Select the same disk again, add GPT partition, add the max amount of space, set format to "Leave unformatted" 
[*]Select the next disk, add GPT partition, add the max amount of space, set format to "Leave unformatted" 
[*]Select "Create software RAID (md)" 
[*]Enjoy. 
[/LIST]

**EDIT #1**: I will edit the post in the thread I linked and include this explicit RAID example.

**EDIT #2**: Because the live installer throws off so many people wanting to use RAID/LVM, I will probably create a tutorial for the express purpose of showing how to configure the partitions for various situations.

LHammonds

---

### Post by cybercrypt13 on 2020-05-21
Legacy install worked perfectly.  So guess they need to take serious look at this new installer.

Thanks for assistance.

Glenn

---

### Post by cybercrypt13 on 2020-05-21
Thanks, I have a few servers to build so will try your method on the next server shortly.

Thanks for further explanation.

Glenn

---

### Post by darkod on 2020-05-21
Going back to the EFI question.

On most boards indeed you can control that in the BIOS. Usually there is setting to limit the boot to legacy instead of EFI (the wording might be different).

My personal preference for linux servers remains legacy boot + gpt partition tables on the disks. However I have seen cases where the BIOS doesn't allow that combination so it might depend on your board.

My desktop for example allows me to use only legacy boot with msdos partition table or EFI boot with gpt table. But not legacy boot with gpt table.

---

### Post by LHammonds on 2020-05-21
Be aware there are end-result differences between the "live" and "legacy" installers.  You won't get exactly the same server at the end of the process.

I started to document the differences in [this thread](https://ubuntuforums.org/showthread.php?t=2443047) but have focused my time on converting my 18.04 servers to 20.04 for the moment (using Legacy installer)

LHammonds

---

### Post by jfmckenna on 2020-08-16
> **LHammonds said:**
> Then you did not read my post and understand the trick behind making the LVM/RAID option re-appear after adding a boot partition.

I just setup a VM and added two 25 GB hard disks and these are the steps I took to add a /boot partition and the rest in RAID:


[LIST=1]
[*]Select "Custom storage layout" 
[*]Select one of the available disks, add GPT partition, 1G, ext4, /boot 
[*]Select the same disk again, add GPT partition, add the max amount of space, set format to "Leave unformatted" 
[*]Select the next disk, add GPT partition, add the max amount of space, set format to "Leave unformatted" 
[*]Select "Create software RAID (md)" 
[*]Enjoy. 
[/LIST]

**EDIT #1**: I will edit the post in the thread I linked and include this explicit RAID example.

**EDIT #2**: Because the live installer throws off so many people wanting to use RAID/LVM, I will probably create a tutorial for the express purpose of showing how to configure the partitions for various situations.

LHammonds

After I finished step 4 the option for "Create software RAID (md)" is grayed out. Any ideas? Did you ever put that tute together?

Regards.

---

### Post by mastablasta on 2020-08-17
this should be reported as bug/feature request on launchpad for installer. it is ridiculous that you can't have system disk in mdadm.
although i have separate system drive, so this shouldn't be an issue, i can see why this could be annoying for some. especially if it worked before.

---

### Post by darkod on 2020-08-17
Since it seems people have been able to do it successfully, I wouldn't go so far to call it bug/feature request. It might depend on specific setup and how each one has got the disk layout for his system.

Also, my 2 cents here are: ignore the new changes until you have no way out or unless you need them. By that I mean the new installer. The 'legacy server' image is still here, so simply use that and no problems. If they remove it for 22.04, we will tackle that problem in 2 years. :)

If you want to try this with the new installer, do you have /boot partitions on both disks or only one? A post on askubuntu seems to say they had success but with identical disk layout on both disks, that means /boot partition (raid1) on both disks. Link: [https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices](https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices)

---

