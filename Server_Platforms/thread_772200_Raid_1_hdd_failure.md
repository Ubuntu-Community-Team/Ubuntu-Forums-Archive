---
title: "Raid 1 hdd failure"
date: 2008-04-28
forum: Server Platforms
---

### Post by HereInOz on 2008-04-28
I am experimenting with a server installation with 2 HDDs in a software raid 1 configuration, setting up the raid during installation.  

I find that if I fail either one of the HDDs, then I am not able to boot from the one good HDD.  I was given to understand that with a raid 1, the system could continue working in the event of a hard drive failure.  Is this not the case in this instance, or am I missing something.

I guess the other possibility is that the system is not bootable, but one can introduce another hdd to the raid using a recovery cd, get the thing synchronised again and re-boot from the raid, so is it possible if someone can enlighten me about what one can actually expect from a software raid 1 configuration when a hdd fails.

---

### Post by Oldsoldier2003 on 2008-04-28
you can expect that things will continue to operate as long as your other disk is operational. all you would have to do in event of a failure is hot swap the bad disk and keep going. a reboot isnt necessary,

[http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

---

### Post by bigal99 on 2008-04-28
How does one tell which of the drives has failed? mdadm?

---

### Post by BadAstronaut on 2008-04-28
Is it possible that HereInOz's problem is that GRUB was not installed on the second drive in the mirror?

I've only been running Ubuntu for 3 weeks now, but I also chose a RAID 1 configuration for my boot drive, with assistance from this site:

[INDENT][http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)[/INDENT]

See the section "Making every drive bootable"

---

### Post by sudo_sk0 on 2008-05-10
Take a look here
http://ubuntuforums.org/showthread.php?t=788713

There seems to be a problem with RAID1 under Ubuntu 8.04

Please post in that thread to get this issue more attention,
so that it can be resolved.

missing raid1 functionality is shameful for an LTS release

---

### Post by windependence on 2008-05-11
Keep in mins that with RAID1, if you have corruption on one drive, it will be immediately mirrored to the other drive, same with viruses or intrusions.

-Tim

---

### Post by Ubuntu Warrior on 2008-05-12
Today one of our UltraSCSI drives failed on an HP ProLiant DL385 server (running 7.04). It was part of a RAID 1 volume with RAID provided by standard HP controller shipped with the server. Theoretically the problem should have been shielded from the OS, HOWEVER, the server was brought down (together with 120 Linux clients depending on the server for /home shares) :(

My question is: Why does the failure of one disk in a two-disk RAID 1 mirror cause the server to fail? In addition, the server cannot be rebooted as it seems to have lost grub???

MAJOR disappointment to see that my much loved Ubuntu Linux OS doesn't handle the basics of RAID all that well. Just to rub salt into our wounds, a similar disk failure on an HP ProLiant DL360 running Windows Server purrs along without a problem - it flagged the drive as failed (flashing red light on the disk and entry in event log), we hot-unplugged, replaced by hot-plugging and the server didn't miss a beat. Is this where M$ claims to be a more cost-effective option against Linux?

---

### Post by geertn on 2008-05-12
You have different types of RAID:
- Software raid
Apart from having to configure everything right, a drive can fail in several ways. Especially with IDE or SATA 1, if a drive fails, you can get into problems on the hardware layer (locked bus, controllers). Nothing linux (or windows) can do about this.

- Fake hardware raid
Several raid controllers do fake hardware raid. This means that they have support for offloading some RAID operations onto hardware but you still need a driver (proprietary) to operate the RAID array. Stay away from these solutions! This will give you extreme headache with regards to setting up, operating and performance is extremely bad (in my experience, at least).

Drivers for these solutions tend to be better on the windows side. But overall, it is still a bad and ugly solution.

- Real hardware raid
More expensive raid controllers will do real hardware raid. They have a chip onboard which handles all of the RAID operations and will present your arrays as a normal drive to your OS. These are cards like the Areca cards (know to be one of the fastest cards around), 3ware and adaptec. This will give you the most flexibility with regards to hot swapping, failure handling and so on.

---

### Post by songshu on 2008-05-12
if you look for something more sturdy and tested you might as well try debian, there is a disadvantage to predictable releases.

mind that you would have to set up grub on both disks, i'm not sure if the installer does that by itself because i never tried it that way.

you can set up mdadm to send you e-mail notifications in case of drive failures.

additionally you could have a look at smartmontools to send you regular reports, its not a 100% guarantee but it can give you some indication.

---

### Post by AlexanderDGreat on 2009-11-07
On my Ubuntu 9.04, I have Raid1 2 x 36gb Seagate Cheetah. When I unplug 1 of the hard disks during boot, simulating a failed drive, it drops me to a shell with initramfs, and Ubuntu will not boot. I'm confused, this is NOT suppose to happen right?

So what do I do now? Thanks.

---

### Post by fjgaude on 2009-11-08
> **AlexanderDGreat said:**
> On my Ubuntu 9.04, I have Raid1 2 x 36gb Seagate Cheetah. When I unplug 1 of the hard disks during boot, simulating a failed drive, it drops me to a shell with initramfs, and Ubuntu will not boot. I'm confused, this is NOT suppose to happen right?

So what do I do now? Thanks.

You likely don't have **grub** on both of the drives, only on the one that you pulled out.

---

