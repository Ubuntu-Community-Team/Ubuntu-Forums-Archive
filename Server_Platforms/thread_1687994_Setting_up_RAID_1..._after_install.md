---
title: "Setting up RAID 1... after install"
date: 2011-02-14
forum: Server Platforms
---

### Post by TechSupportx86 on 2011-02-14
Ok so i've decided to go with software RAID for 2 IDE drives. from what i read it's possible, but nothing i found is for what i want specifically. The problem is all the guides i found are for setting up RAID *_BEFORE_* installation of the OS, and to clone the boot disk... this isn't what i want. 

[COLOR=Red]_**Short Version**_[/COLOR]: **I have a home server running 10.10 server and i want to setup RAID 1 on sdb and sdc. Both drives are 80GB IDE, one WD and one Seagate (i know, i know). Everything must be done via SSH, So where do i begin? google hasn't offered much in the way of post-installation storage-only RAID setup for ubuntu server using command-line only.**

Further reading: These drives are for storing my music collection (which i have already lost once), and thought it would be a nice solution to my problem. I am using samba to share my drives as extra space and DLNA down the road (when i have a use for it). I have a 20GB IDE drive for boot, and these 2 80GB IDE drives for (hopefully) RAID 1. I plan on adding a 1TB in about a month, and later replacing the 2 80GB with 2 500GB SATA.

---

### Post by dtfinch on 2011-02-15
Wikipedia has a quick reference with all the important stuff, oddly enough: [http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)

Create the raid: (if your raid drives are sdb and sdc, and you've partitioned them)
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 /dev/sdc1

Append array details to mdadm.conf:
mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf

After which the boot ramdisk should be updated:
update-initramfs -u

Create the filesystem:
mkfs.ext4 /dev/md0

Add it to /etc/fstab:
/dev/md0 /store ext4 defaults,nobootwait 0 2

"/store", or whatever you use, must already exist as a directory. The nobootwait is to prevent startup from halting if it can't mount it for some reason. I also add "barrier=1,nodelalloc" to reduce risk of loss in a crash at the cost of performance, and "noatime" to gain a small bit back.

Mount with "mount -a"

Another option is to use LVM, which has some mirroring support on its own, and it makes growing and moving volumes much easier, or you can use it in combination with mdadm.

---

### Post by TechSupportx86 on 2011-02-15
Well that's certainly enough to get me started, Thanks!

Will report back with results ;)

---

### Post by YesWeCan on 2011-02-15
> **TechSupportx86 said:**
>  Both drives are 80GB IDE, one WD and one Seagate (i know, i know). 
What do you know? It seems to me that the data protection of a RAID is improved the less correlated the failures of the disks. So in this regard is it not beneficial to use disks from different manufacturers?

---

### Post by TechSupportx86 on 2011-02-15
> **YesWeCan said:**
> What do you know? It seems to me that the data protection of a RAID is improved the less correlated the failures of the disks. So in this regard is it not beneficial to use disks from different manufacturers?

Yes, It's just when it comes to RAID almost everyone (well, atleast the guides i've read) will tell you that using the same exact drive (we're talking same brand, same model and same family) is sort of a rule, But i disagree for the same reason. The "i know i know" was just to disregard the differences of the disks and get to the setting up of the array, to keep those "you should use the same blah blah blah" from voicing their opinion. 

The same would have been said if working with 2 brand new 1TB drives, one hitachi and the other WesternDigital (WD is just my pref). Was really just a "i know the so-called 'risk', just get to the point".

My personal opinion is to use 2 different brands. The chances of 2 hitachi, seagate, wd, or IBM drives failing if in RAID for the same exact amout of time has a far greater chance of losing both disks before you can replace the bad one.

---

### Post by disabledaccount on 2011-02-15
> **TechSupportx86 said:**
> Yes, It's just when it comes to RAID almost everyone (well, atleast the guides i've read) will tell you that using the same exact drive (we're talking same brand, same model and same family) is sort of a rule, But i disagree for the same reason. This rule comes from experience and knowledge about HDDs. Array made of different drive models will work ofc, but the main disadvantage will be lower to very poor performance. This is true for every stripe-based array - the only exceptions are JBOD and special configurations of Raid1, like "Write-mostly" variant in md. It would need a lot of writing to explain why, but using simple words - it's similar to what happens when partition/stripe/chunk alignment is wrong, but produces much worse results, nemely huge delays that are periodical function of HDD's head position.

HDD is not a gaming die - You can't estimate probability of failure that way, because there are *hundreds* of factors and many of them are independant of HDD model, like PSU output voltage quality, ambient temperature, humidity, etc.

---

### Post by TechSupportx86 on 2011-02-15
> **dtfinch said:**
> Wikipedia has a quick reference with all the important stuff, oddly enough: [http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)

Create the raid: (if your raid drives are sdb and sdc, and you've partitioned them)
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 /dev/sdc1

Append array details to mdadm.conf:
mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf

After which the boot ramdisk should be updated:
update-initramfs -u

Create the filesystem:
mkfs.ext4 /dev/md0

Add it to /etc/fstab:
/dev/md0 /store ext4 defaults,nobootwait 0 2

"/store", or whatever you use, must already exist as a directory. The nobootwait is to prevent startup from halting if it can't mount it for some reason. I also add "barrier=1,nodelalloc" to reduce risk of loss in a crash at the cost of performance, and "noatime" to gain a small bit back.

Mount with "mount -a"

Another option is to use LVM, which has some mirroring support on its own, and it makes growing and moving volumes much easier, or you can use it in combination with mdadm.


Well i followed the instruction, had to improvise a tad, BUT i think i did it :)
The only problem i had was a permissions error with the command:

```
mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf
```Which i just opened mdadm.conf with nano and added:

```
mdadm -Es | grep md0
```I added md0 to fstab to be mounted at /media/Music, restarted and got _**zero**_ errors so i think i'm good. Shows up on my desktop as a samba share (just sharing /media/Music) with 69.4GB free (just need to run tune2fs). so pretty much i'm all setup! Thank you very much, hopefully someone else will find this useful.

;)

---

### Post by ashikaga on 2011-02-15
> **TechSupportx86 said:**
> Well i followed the instruction, had to improvise a tad, BUT i think i did it :)
The only problem i had was a permissions error with the command:

```
mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf
```
Were you using sudo? If so, sudo doesn't apply to the redirect itself. If you want to use that syntax you need to temporarily switch to root ```
sudo -i
``` or another user that has permission to write to the file you're trying to redirect to.

---

### Post by YesWeCan on 2011-02-15
> **TechSupportx86 said:**
> My personal opinion is to use 2 different brands. The chances of 2 hitachi, seagate, wd, or IBM drives failing if in RAID for the same exact amout of time has a far greater chance of losing both disks before you can replace the bad one.
I agree. Should be fine with RAID 1.
I implemented a RAID 1+0 with different brands and didn't see any performance reduction.

Perhaps tomazzi will elaborate on the specific corner cases where performance suffers significantly.

---

### Post by TechSupportx86 on 2011-02-15
> **ashikaga said:**
> Were you using sudo? If so, sudo doesn't apply to the redirect itself. If you want to use that syntax you need to temporarily switch to root ```
sudo -i
``` or another user that has permission to write to the file you're trying to redirect to.

will keep in mind for next time, thanks.

> **YesWeCan said:**
> I agree. Should be fine with RAID 1.
I implemented a RAID 1+0 with different brands and didn't see any performance reduction.

Perhaps tomazzi will elaborate on the specific corner cases where performance suffers significantly.

Yeah, mine seems to be working fine. i mean the transfer rate went from about 11.4 to about 8mb/s, but it's 2 IDE drives, performance went out the window before i even started. I'm not expecting to run any programs off of it, or use it like and external HDD. The most stress this is going to see is copying my music folder over, and reading the 5mb songs to be played on iTunes or songbird (so reading 5mb every 3-4 minutes). 

I can see if i was hosting a content-rich website this could pose a problem and i WOULD want to gain any and all performance possible, but this is really only going to serv as basic storage with redundancy, and that's what i need ;)

So i think it's safe to say using two different disks of the same size, from different manufacturers isn't the *recommended* configuration if you are looking for performance, BUT it will work just fine for an 'average joe' home-server based storage setup, altho not an enterprise server setting where performance is necessary which i think tomazziis referring to. i'm not saying the performance loss isn't there, but i understand the trade-off to allow for redundancy.

---

### Post by dtfinch on 2011-02-16
> **TechSupportx86 said:**
> Well i followed the instruction, had to improvise a tad, BUT i think i did it :)
The only problem i had was a permissions error with the command:

```
mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf
```Which i just opened mdadm.conf with nano and added:

```
mdadm -Es | grep md0
```I added md0 to fstab to be mounted at /media/Music, restarted and got _**zero**_ errors so i think i'm good. Shows up on my desktop as a samba share (just sharing /media/Music) with 69.4GB free (just need to run tune2fs). so pretty much i'm all setup! Thank you very much, hopefully someone else will find this useful.

;)

Just adding the line "mdadm -Es | grep md0" to mdadm.conf won't work right. Since it booted anyway I'd guess that it quietly failed to parse it and relied on autoassembly.

The line returned by "mdadm -Es | grep md0" (if run as root) to add to mdadm.conf would have been something like "ARRAY /dev/md0 level=raid1 num-devices=2 UUID=0f53b37e:e16027fc:da7d92d4:3b69af05", but the UUID would be different on your installation.

If the right ARRAY line isn't added to mdadm.conf (then updated to the init ramdisk), it'll rely on auto-assembly instead which hasn't been entirely reliable in my experience (on 10.04, though maybe they've fixed it by now). It'd work for a few boots then fail to assemble, in my cases stealing a drive to create a new broken raid with a different autogenerated name like md_d0.

---

### Post by TechSupportx86 on 2011-02-16
yeah, i restarted and had another go at it. read the entire wiki page, read your guide again, formatted both drives and setup mdadm again. this time everything worked perfectly, no permission errors and from what i read everything went the way it's supposed to.


LOL, i can't believe i didn't see those were commands... 
**pro tip:** don't setup RAID when you're tired and *slightly* intoxicated. \\:D/

---

