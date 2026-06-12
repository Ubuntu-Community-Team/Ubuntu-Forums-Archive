---
title: "Ubuntu won't boot with RAID array removed"
date: 2009-03-25
forum: Server Platforms
---

### Post by energyx on 2009-03-25
I have a 3 disk degraded mdadm RAID 5 array that I want to remove from my 8.04 server. It is on an add-in Promise card. I have tried removing just the drives, as well as the controller itself. When I boot into recovery mode, it hangs at **md: bind<sda>** and will eventually complain about the RAID being degraded and dump to a initramfs prompt.

I would like to keep the drives and array intact, but remove them from the server. How can I get past this md bind? It still thinks the drives are there for some reason and I can't get past this point without putting them back in.

I've tried removing the mdadm.conf, deleting mdadm from init.d and starting with raid=noautodetect, but it continues to load.

edit: I should note this array is a data only volume separate from the system drive.

Thanks
Chris

---

### Post by theDaveTheRave on 2009-03-25
hi

could you have inadvertently put part of the boot sector onto the raid device?

I am assuming that you have a separate drive that you should be able to boot into?

I have not experienced this issue with our server, and we are adding / removing disk on a semi regular basis!

I'm sure you should be able to "re-install" the boot procedure to the prinicple hdd, but you'll need to have a quick search on these forums for how to do so...I've not found anything that seems to relate to your problem yet... but also I'm not sat in front of your system and hence I don't know what you set up is.

Try serching for "re-install grub" on the wiki, as that may help also, here is one a [link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") that may give you some ideas, I recognise it doesn't really cover your problem... but, as I say, it may give you an idea for a solution.

David

---

### Post by Throwback on 2009-03-25
I have previously experienced a problem like this when using a system with a single system drive and an md raid 1. It came from Grub interpreting the ID of the system drive differently at boot when it did not have raid support enabled to when it was installed when the OS was running when raid support was enabled, in other words I had to manually specify which drive to boot from and state the ID the drive has ON BOOT rather than the one the system drive has when the system is running. Dunno how helpful that is but I thought I'd chip it in.

---

### Post by energyx on 2009-03-25
The RAID was from another ubuntu install and was added after I installed on the single boot drive. GRUB did have the boot drive set to 3,0 after the clean install, even though the drive was really on 0,0, and I had to fix that with just the one drive installed. GRUB is loading fine and I get the "Starting, please wait..." message once the kernel loads. It wasn't until I tried recovery mode that I saw it was hanging on a md bind command.

I don't know where it is still trying to call md from, and it still knows about the missing array somewhere in the config.

---

### Post by fjgaude on 2009-03-25
What's fstab file look like?

Did you remove the mdadm.conf file?

---

### Post by energyx on 2009-03-25
> **fjgaude said:**
> What's fstab file look like?

Did you remove the mdadm.conf file?

I renamed mdadm.conf to mdadm.old, should I try moving?

FSTAB (I commented out the md0 mount):
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=afcaeb0c-1a3e-426a-991f-5eac134c6406 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0da39982-07f6-4042-a136-1562e3623eb9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/md0      /mnt/oldstore   auto    defaults        0       0
```

---

### Post by fjgaude on 2009-03-26
I think I've lost track of your problem... 

Your UUIDs of the boot partitions are okay? Try using **blkid** to determine if they are. If you can't boot, then you will need to use a LiveCD with the raid array disconnected to get the UUID of the boot drive.

Likely blkid is not on the LiveCD so you will have to download it from the repository or whatever. Or maybe:

```
sudo vol_id --uuid /dev/sda1
```

I think **vol_id** is already on the LiveCD.

---

### Post by energyx on 2009-03-26
GRUB seems to be working since I am getting the kernel alive message at the bottom of the screen, right? I will try the vol_id thing and reinstall GRUB once I remove the RAID array using a LiveCD. It is essentially hanging on a md: bind<sda> command during startup, then it complains about the RAID array missing, and dumps to an (initramfs) prompt.

My RAID array is hde/hdf/hdg and my boot drive is sda, so I'm not sure what md is trying to to with sda to begin with.

---

### Post by fjgaude on 2009-03-27
Your grub should point to the boot drive, sda... I suppose from what you say it does.

Seems there is something not being understood. If your boot drive in the fstab file has the correct UUID and if your BIOS is pointing to that drive name then the system should boot, with or without the raid array.

Let us know as you learn things.

---

### Post by energyx on 2009-03-27
> **fjgaude said:**
> Your grub should point to the boot drive, sda... I suppose from what you say it does.

Seems there is something not being understood. If your boot drive in the fstab file has the correct UUID and if your BIOS is pointing to that drive name then the system should boot, with or without the raid array.

Let us know as you learn things.

Well, I removed the drives and controller and changed the GRUB menu from hd(0,0) to hd(3,0) before I rebooted and it came up fine. GRUB picks 3,0 whenever it updates the menu itself, so I tried that first. After it booted once like that, I had to change it back to hd(0,0) for it to boot thereafter. I think my BIOS is moving things around since I am using both SATA and PATA drives. Adding in the extra controller just confused things even more.

I would have never guessed GRUB was the root problem, but I guess it was. Thanks for all your help and I'll update if I run into any more problems booting.

---

### Post by networm1230 on 2009-03-27
question? what is raid? is raid some kind of hard drive configuration?

---

### Post by fjgaude on 2009-03-27
> **networm1230 said:**
> question? what is raid? is raid some kind of hard drive configuration?

Try this to get started on understanding:

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

Let us know if you have any questions.

---

### Post by fjgaude on 2009-03-27
> I would have never guessed GRUB was the root problem, but I guess it was. Thanks for all your help and I'll update if I run into any more problems booting.

Well, there's so many things to consider for all this truly is complex, eh?

Do let us know if you run into any other issues; we might be able to help.

---

