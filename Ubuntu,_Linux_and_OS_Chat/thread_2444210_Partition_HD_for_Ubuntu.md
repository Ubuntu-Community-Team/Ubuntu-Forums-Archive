---
title: "Partition HD for Ubuntu"
date: 2020-05-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2020-05-26
I have searched the internet on this topic, only to find everyone tends to do this differently...

So, I must ask.  What do you find to be the best way to partition and setup a Hard drive (HDD or SDD) for use with Ubuntu?

---

### Post by rbmorse on 2020-05-26
384 Mb FAT32 for EFI

32Gb EXT4 for / (root -- system partition)

whateves for /home (in a separate EXT4 partition).  If the storage device is an SSD I'll size this so the total load on the device is something less than 80% of capacity.  Over provisioning may be chicken superstition left over from ancient gods, but I still do it. 

no swap partition -- use swapfile instead. 

separate physical storage device for primary backup (secondary backup stores are on external storage and off-site).

---

### Post by TheFu on 2020-05-26
i use LVM and fix stuff post-install before there's much stuff there.  Fairly easy w/ LVM.  Just have to get the real partitions correct - that's /boot and the one that holds all the LVM (or LUKS encrypted) stuff.  Things that go into the LVM can be fixed later. Mainly resized down to 25G and a few other LVs added for /home/ and swap and general storage.

My typical layout: [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

LVM is handy on servers for many reasons. Snapshots, providing block storage to VMs and Containers, changing to mirroring or moving the storage to a new HDD.  i suppose ZFS can do the same things?

---

### Post by oldfred on 2020-05-26
Everyone does it different based on needs & experience.

I find even my best, optimal layout a few years later is not so good. But by then I am not sure I want to rely on my main working drive and get a new drive, and can start over.

Dual boot, multiple boot, lots of media files (than may not change a lot but are large), data  you must backup more frequently (may be a bit easier in separate partition). But all your data needs good backups anyway.

---

### Post by mastablasta on 2020-05-27
i used only one partition + swap (so just / and /swap)
however the more i read the more i check thing it looks like the separate /home has more benefits that concern me than negatives.
so on my kids PC i setup about 50 GB root (/) and the rest is /home partition. works well and so far it even saved his PC from total crash.  Steam created huge error log file that covered the whole disk and wont' stop growing. But since it was confined to home i could still work on and reboot the PC and easily resolve the issue.

so separate home on single user PC is definitely a plus and i somehow need to get my single partition to separate home setup. maybe on the next upgrade...

otherwise, you can just leave it at default and it will be OK. defaults in installer make sense.

---

### Post by Perfect Storm on 2020-05-27
SSD: efi
SSD: ext4 root
HDD: ext4 home
No swap.

That's my setup on my Desktop.

---

### Post by Shibblet on 2020-05-27
And again, since everyone here is doing something different, it seems as if it **doesn't really matter how you partition your drive(s).**

Currently, I have a 512g SSD with:

512m for /boot/efi
32g for /
428g for /home
51.2g - over provision.

I also have a separate 4tb HDD that is used for my own personal storage.

I guess I was wondering if there was a specific way to set up the EFI partitions, and the /(root) directory.  I see different setups depending on the OS.  Fedora / Suse / Manjaro etc.
Windows 10 also has an odd EFI partition structure.

---

### Post by mastablasta on 2020-05-28
eh, i forgot about the EFI on the new PC. your setup is good.

there is no specific way. you can se it as you want. you can practically make any folder a partition. not that you should.

for spinning HDD the more accessed files benefit from being at the start of the disk since they are on the inner area of the actuall disk. well at least that was the case. but for SSD this doesn't matter at all i guess.

---

### Post by Shibblet on 2020-05-28
> **mastablasta said:**
> eh, i forgot about the EFI on the new PC. your setup is good.

there is no specific way. you can se it as you want. you can practically make any folder a partition. not that you should.

for spinning HDD the more accessed files benefit from being at the start of the disk since they are on the inner area of the actuall disk. well at least that was the case. but for SSD this doesn't matter at all i guess.

Yeah, it's amazing all of the information out there about how you are "supposed" to set up your hard drive.

People still stating that you need to have a certain amount of space set aside for swap, over partitioning for SSD's, having certain disks set aside for /home or /var... "/etc."  ;-)

And every distro seems to have it's own way of handling partitions by default.  Ubuntu (Kubuntu), by default, doesn't make different partitions on your SSD or HDD.  It just makes one big partition with all of the "/" directories on that part.  Which, IMHO, is one of the genius aspects of all Linux Distros...

---

### Post by TheFu on 2020-05-28
> **Shibblet said:**
> Yeah, it's amazing all of the information out there about how you are "supposed" to set up your hard drive.

People still stating that you need to have a certain amount of space set aside for swap, over partitioning for SSD's, having certain disks set aside for /home or /var... "/etc."  ;-)

And every distro seems to have it's own way of handling partitions by default.  Ubuntu (Kubuntu), by default, doesn't make different partitions on your SSD or HDD.  It just makes one big partition with all of the "/" directories on that part.  Which, IMHO, is one of the genius aspects of all Linux Distros...

There is a thread here from about 2 months ago about swap sizing. Basically, it depends on workload, RAM, storage. The old rules of thumb of 2-3x RAM size have been outdated for decades.  Those ideas were from a time when 32**MB** of RAM was huge.

Using separate LVs or partitions for /var/, /etc/ were from a time when 240MB HDDs were huge and running out of space was a problem, mainly. There are times, for highly secure systems that having specific mount options for /var, /etc, /tmp are required.  These days, those would be the only real reason that I know to have separate LVs or partitions for those areas - security.
I split LVs out mainly for backup purposes. Logwatch warns me when any storage devices on the network are nearly full, so running out of space seldom happens.  A few people get their systems into weird states that cause millions of repeated log entries, causing the log files to massively grow.  Limiting any log file to 10MB isn't hard. I don't understand why that isn't the default.  Should be easier under journalctl.

Many Linux distros do just 1 large / partition or LV just because it is easy and noobs wouldn't care or know any difference.  Experts will setup the storage in the way they want anyway, so why bother making the defaults too complex?  We know that pleasing everyone is impossible, so might as well keep it simple.  Genius or lazy. You pick.

I under commit SSD storage by 20%.  My SSDs are 500G or 512G ... really don't need more than 120G for most of my uses, so all the extra is just that - extra.  Sure, I can fill it, but that's what storage servers are for.  Having a laptop with 50% of the storage used is fine. It also means I don't need to backup all that extra useless storage.

But what do I know?  I'm just some guy on the internet, not being paid to provide advice.

---

### Post by Shibblet on 2020-05-28
> **TheFu said:**
> But what do I know?  I'm just some guy on the internet, not being paid to provide advice.

Hey, don't sell yourself short.  The advice I get on this particular forum is better than any tech support system out there.

I recently bought a WD My Cloud Home, and it wouldn't load the Plex Server software.  So I contacted WD to see if there was anything I happened to be doing wrong...
The first thing they asked me is if I could use a different browser.  They didn't even ask which browser I was using...  I about lost my cool.

---

