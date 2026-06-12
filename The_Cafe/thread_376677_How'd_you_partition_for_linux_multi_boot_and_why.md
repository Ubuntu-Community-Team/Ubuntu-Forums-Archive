---
title: "How'd you partition for linux multi boot and why?"
date: 2007-03-05
forum: The Cafe
---

### Post by halfvolle melk on 2007-03-05
What would your partition plan be for lets say 3 different distro's?

I've got 2 extra partitions for experimenting and edutainment:

128 MB /boot for all kernels
10GB Ubuntu root
5GB extra distro
5GB extra distro
210GB /home Ubuntu only
1GB /swap

The extra distro's will have their /home on the root partition.
In hindsight I'd probably have set it up differently but I'm not exactly sure how.

Slightly off topic but after reading the Slackbook I wonder:
- Why would you have a separate /usr/local partition?
- How can a separate /var partition enhance performance?

---

### Post by macogw on 2007-03-05
if they have /home on the / partition, they'll need a lot more than 5gb unless they're damn small linux and uh...vector? puppy?  something like that.

mine is set up like this:
10gb fedora /
15gb sabayon / (the os is huge)
7gb ubuntu 6.10 /
7gb ubuntu 7.04 /
70gb /home
2gb swap

they all share /home which means i can get all my files regardless of what i'm using and once i set one of them to have the panels and everything how i want them, they're like that in all of them

---

### Post by celsofaf on 2007-03-05
I have about...

hda1: 25GB for Windows XP (nfts)
hda2: less than 0.5GB just for GRUB stuff, as well as to backup my config files like xorg.conf (ext3)
hda3: 2GB for swap
hda5: 30GB for Kubuntu 6.10 (yes, too much empty space) (ext3)
hda6: 15GB for Arch (ditto) (reiserfs)
Plus unused space at the end of hda, for future to be decided use.

hdb1-hdb3,hdb5: 15GB each for testing random distros
hdb6: 60GB for personal files (ext3)

My hdb6 is mounted inside every /home directory. It's much better to do this than to separate /home itself into another partition!

---

### Post by macogw on 2007-03-05
> **celsofaf said:**
> 
My hdb6 is mounted inside every /home directory. It's much better to do this than to separate /home itself into another partition!
Why's that?  Is it because of the sort of problems I ran into where RH-based uses 500 and Debian uses 1000 for UID?  I had to go into tty and sudo vi /etc/passwd and /etc/group to make the /home play nice

---

### Post by FyreBrand on 2007-03-05
If I were to partition for 3 different Linux installs it would be like this:

**Boot:** MBR (hd0)

**Partition 1(sda1):**
[INDENT]type: primary
file system: ext3 or reiserfs
size: <size of drive sda> minus <size of parts 3,4,5 & 6>
mount point: /documents /files (or whatever you want)
notes: This is a shared data directory.  This is where you can store photos, music, web sites, or any other files that you would want to access from any of your OS installs.  It's _not_ a home partition.  This is so you don't have conflicting hidden configuration directories and files.  This allows you to have exactly the same user name and permission scheme in all your OS installs and you don't have to create a complex "sharing" group to see, use, or modify your files.
[/INDENT]

**Partion 2 (sda2):**
[INDENT]type: extended
[/INDENT]

**Partion 3 (sda3):**
[INDENT]type: logical
file system: ext3 or reiserfs
size: 10 to 15GB
mount point: / (root)
notes: This will have it's own /home directory within this partition.
[/INDENT]

**Partion 4 (sda4):**
[INDENT]type: logical
file system: ext3 or reiserfs
size: 10 to 15GB
mount point: / (root)
notes: This will have it's own /home directory within this partition.
[/INDENT]

**Partion 5 (sda5):**
[INDENT]type: logical
file system: ext3 or reiserfs
size: 10 to 15GB
mount point: / (root)
notes: This will have it's own /home directory within this partition.
[/INDENT]

**Partition 6 (sda6):**
[INDENT]type: logical
file system: swap
mount point: none
size: 1 - 1.5GB
[/INDENT]

This way you have 3 independent operating systems that are totally atomic and won't be interfering with each others settings or parameters.  You will have a shared data drive that will have consistent permission settings between all operating systems.  You will have a boot sector in the Master Boot Record.  Your swap partition will be in the extended partition at the end of your hard drive.

If you absolutely can't or don't want your boot in the MBR then I would make a 100MB boot partition in sda1 and bump up each of the remaining partition numbers by one.

---

### Post by rsambuca on 2007-03-05
Here is mine.  I use one large extended partition with a bunch of logical partitions for the different distros, along with a common swap.  I have another separate partition for my data (docs, music, videos, etc.).

---

### Post by halfvolle melk on 2007-03-06
Thanks for your insights.

[quote=macogw]if they have /home on the / partition, they'll need a lot more than 5gb unless they're damn small linux and uh...vector? puppy? something like that.[/quote]
All big data such as music files etc. goes in the Ubuntu /home and would get mounted in the dist2 and dist3 /home so the latter 2 would only have to hold the hidden config files.

FyreBrand, that makes sense. Looks like a good scheme. Though I don't think I understand the choice between a /boot partition or MBR. Why do I have a /boot partition? :lolflag:

---

### Post by FyreBrand on 2007-03-06
If I can I always use the MBR because that leaves one more primary partition available and really that's were boot applications were intended to live.  There is this one style of machine that has some odd SATA setup that doesn't like being installed to the MBR so I install to a /boot partition because it's easier.  Someday I'll be a grub wizard and understand how to manually configure it.

As someone pointed out above some distributions have different user/group defaults.  I think Fedora numbers some group id's differently.  In K/X/Ubuntu our primary group is also our user name (which I really like), but Sabayon, on the other hand, creates a User group instead.  This really messes with my permission scheme so the first thing I do is create a user group that mirrors my K/X/Ubuntu primary user group.  I never realized how different distributions can be even though they're using the same kernel and desktop environment.

---

### Post by johnlvs2run on 2008-06-21
> **FyreBrand said:**
> **Partion 3 (sda3):**
type: logical
file system: ext3 or reiserfs
size: 10 to 15GB
mount point: / (root)
notes: This will have it's own /home directory within this partition.

How do you set up the /home directories within each / partition?  
For example, is all of the 15gb allocated for each /home? 
 
A photo of this would be helpful if possible.  Thanks.

---

### Post by cardinals_fan on 2008-06-21
10 GB Arch
35 GB Slackware
200 GB data partition

---

### Post by Can+~ on 2008-06-21
/dev/hda:
[ntfs Windows Xp [COLOR="RoyalBlue"]40gb[/COLOR]]

/dev/sda:
[ext3 Ubuntu 8.04 (/) [COLOR="RoyalBlue"]20gb[/COLOR]] [-------NTFS: /common------ [COLOR="RoyalBlue"]220gb[/COLOR]] [SWAP 1gb]

That way I can format any of them and just backup to the common partition. Windows is there because I sometimes need it (rarely though, like 4 months without booting into it).

Also, here's a tip for gparted; use gparted /dev/??? (where ??? is the hard disk) to force it to open that hard disk, instead of wasting a whole hour scanning everything (even non-existent devices)

---

### Post by johnlvs2run on 2008-06-21
> **FyreBrand said:**
> notes: This will have it's own /home directory within this partition.

Is it something like this?
```

/sda1 ........ /boot ............ 100mb
/sda2 ........ swap-linux ....... 1gb
/sda3 ........ extended
... /sda5 ...... / root, /home ... 15gb
... /sda6 ...... / root, /home ... 15gb
... /sda7 ...... / root, /home ... 15gb
/sda4 ........ /shared .......... 150gb
```

---

### Post by -gabe-noob- on 2008-06-21
38 Ubuntu 38 Kubuntu/openbox    2 gig swaped

---

### Post by alwiap on 2008-06-21
18 GB Ubuntu partition and a 15 GB Windows XP partition on a Raptor 36.7 10,000 RPM hard drive, then a second internal 200 GB hard drive with data, and a 500 GB external for more data.

---

