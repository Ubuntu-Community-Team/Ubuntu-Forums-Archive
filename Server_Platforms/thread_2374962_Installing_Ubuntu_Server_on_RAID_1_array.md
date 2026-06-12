---
title: "Installing Ubuntu Server on RAID 1 array"
date: 2017-10-20
forum: Server Platforms
---

### Post by sandman874 on 2017-10-20
[COLOR=#111111][FONT=Ubuntu]Hello,

I'm currently working on installing Ubuntu Server on a Fujitsu TX1330 M3 server I recently purchased. The setup is as follows:
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]2 x 1 TB HDD for the OS (I know, waste of space, but I don't want to put data on Seagate drives, bad experience)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]2 x 6 TB HDD for data (WD Datacenter)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My plan is to run both pairs of HDD's in RAID 1 Linux softraid arrays, and install Ubuntu on the 1 TB array.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tried the instructions here: [https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)with the addition of creating a ESP partition which is not part of the raid array. As I understand, you can't RAID your GRUB :-P[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
However, I do have a few questions:[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]Can I create two ESP partitions, one on each HDD, not in a RAID array, and manually install GRUB on the second one after the installation? To preserve boot capability when one HDD fails.[/FONT]
[*][FONT=inherit]If this is indeed possible, should I label both partitions as "Use as: EFI System Partition", or will this confuse the installer?[/FONT]
[/LIST]
[COLOR=#111111][FONT=Ubuntu]
So far I have had little success when I tried completing the installer with this method. After the installer finishes without errors, and tells me to reboot and remove the installation media, the server goes straight to BIOS. None of the HDD's show up as bootable media, so I cannot force it to boot from the HDD.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
When I start a live version of Ubuntu, gparted tells me four times that the backup GPT partition table is corrupt. (one for each HDD) I have also tried yannubuntu's Boot Repair tool, which reports that GRUB has been repaired, but none of my drives shows up as bootable anyway. The log file for this repair can be seen at:

[https://paste.ubuntu.com/25780582/](https://paste.ubuntu.com/25780582/)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Does anybody have any tips for how I can make this boat anchor work as a proper server?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks

SandMan874[/FONT][/COLOR]

---

### Post by darkod on 2017-10-20
I can't help much with EFI boot because I am trying to stay as far away from it as possible.

If the server supports it, I would actually try to use legacy boot (disable UEFI boot in BIOS) and try it like that. Linux works with legacy boot and GPT disks, unlike Windows which needs UEFI boot to work with GPT. So in most cases you can use the old reliable legacy boot and still use your big disks with GPT in linux.

1TB is really a waste for the OS only. If you can manage to plan all the big data to reside on designated mount points, you can create 32GB partition on both 1TB disks for the OS with raid1. Then the rest of the 1TB disks will also be one big partitions for another raid1 array. And the 6TB disks will be another raid1 array.

You can use LVM to join the 1TB and 6TB arrays for a total of 7TB data array. Instead of wasting 1TB just for the OS.

---

### Post by sandman874 on 2017-10-21
Thanks a lot for the tip, I've disabled UEFI in the BIOS now, and also reinstalled Ubuntu again in legacy mode. This time with no EFI System Partition, only swap and /, both in RAID 1. Still no luck getting the server to accept the drives as bootable.

I've also run the Boot Repair tool again, this time in live Ubuntu, and it reinstalled GRUB on both /dev/sda and /dev/sdb.

As to the waste of space, I know I could have been clever with LVM to use the extra capacity, but I really don't want to put valuable data on the two 1 TB Seagate drives. Got some bad experience with Seagate drives in the past. The only reason I have them is that they came with the server, so I thought why not use them for the OS at least, and put the valuable stuff on Western Digital.

Anyway, do you have any other tips for things I should check?

SandMan874

---

### Post by darkod on 2017-10-21
One thing you do need for legacy boot and gpt disks is a small 1MiB partition on all disks, without any filesystem. DO NOT format it. You need to set the bios_grub flag on it. This is because grub v2 does not firt on gpt mbr and it needs small unformatted space to put the rest of it's files. I usually create the partitions from live mode with parted in advance, then just use them with the ubuntu server installer.

Grub install will fail if you don't have that small partition.

Does that fail or actually bios does not see any disk as bootable?

---

### Post by sandman874 on 2017-10-22
Well, now I've tried this method as well, but still no joy on getting Ubuntu to boot.

I've attached a couple of screenshots from Gparted and fdisk. Does this look right to you?

[ATTACH=CONFIG]277211[/ATTACH][ATTACH=CONFIG]277212[/ATTACH][ATTACH=CONFIG]277213[/ATTACH]

I created new GPT tables on all the drives in Gparted, then created the 1 MiB partitions, unformatted, but with the bios_grub flag set on both /dev/sda and /dev/sdb. Then I launched the installation for Ubuntu server, and created the swap and / partitions there. Following the instructions I linked to in my first post, I created the four raid volumes and linked them in RAID 1. I did not RAID the two GRUB partitions. The installer completes without any errors afterwards.

Since Ubuntu still refused to boot with this method, I also tried to reinstall GRUB using the Boot-repair tool, but this did not help either.

BTW, I see that you write that the GRUB install will fail if I don't create the 1 MiB partition for it, but that did not happen in my attempts after post #2. Both the Ubuntu installation and Boot-repair tool claimed to have successfully installed GRUB.

Also, these are the settings in my BIOS at the moment:

[ATTACH=CONFIG]277214[/ATTACH][ATTACH=CONFIG]277215[/ATTACH]


SandMan874

---

### Post by darkod on 2017-10-22
All looks good. Once I had similar unexplained issue with my intel nuc6 and at the end it turned out the bios didn't like using gpt with legacy boot. Might be something similar with your board.
The thing is you only need gpt for partitions bigger than 2TB. On your OS disks you can use msdos table too.
So try that combination, legacy boot with msdos table on the small disks and gpt table on the big ones. See if that works out...

---

### Post by sandman874 on 2017-10-22
Alright, I will give that a try then. Will I still need the 1 MiB GRUB partition, and does it need special flags like before? I see the flags under msdos are different than under gpt.

---

### Post by darkod on 2017-10-22
You don't need it on msdos disks in theory.

---

### Post by sandman874 on 2017-10-22
Well, I tried it, but didn't have any more luck with that.

I did however come up with another "theory". It seems that when I configure both drives as single RAID 0 arrays (1 drive in each), I get the option to boot from the "Embedded SATA RAID Controller". This option is not available unless the drives are configured as single RAID 0 or RAID 1 together. So maybe the FakeRAID controller is telling the BIOS there is no point looking for a bootloader on those drives, because it sees them as "unconfigured". 

However, if I configure them as RAID 0 **after **installing Ubuntu, the initialization destroys the gpt or msdos tables, rendering the installation useless. If I on the other hand configure them as two single RAID 0 arrays **before **installing Ubuntu, the installation program sees them as already configured SoftRAID arrays, where I cannot create more partitions, nor connect them together as a RAID 1 array.

Does this sound even remotely logical to you, or have I fallen off the wagon somewhere?

SandMan874

---

### Post by darkod on 2017-10-22
Yes, if the built-in BIOS (server) RAID is interfering, then it is very possible to create issues for you. I wasn't aware you have built-in raid. In many cases it creates problems and insists for that raid to be used.

You have to see if there is any way to disable it, otherwise you would have to stick with using the onboard raid.

For some chipsets you can search for information how to flash them to IT mode, which is what they call flashing an onboard raid controller to lose its raid settings and it simply passes the disks to the OS as standard SATA disks. Then you can freely use SW raid from the OS.

---

### Post by sandman874 on 2017-10-22
Well Darko, we got there in the end. That tip about disabling the built-in raid altogether was the answer to all my problems. 

Luckily, I could switch to AHCI mode without having to flash the chipset. As soon as I did that, all four disks showed up as simple SATA disks, and from then on it was a breeze to install Ubuntu server with the drives as a RAID 1 array. 

So now my server is finally up and running. Thank you so much for all your help with this. I'll buy you a drink if you ever find yourself in Norway... :-D

SandMan874

---

### Post by darkod on 2017-10-22
Wow, perfect. It is nice when it is that easy to disable the built-in raid. :)

Please mark the thread as solved, you can do that in Thread Tools above the first post.

---

