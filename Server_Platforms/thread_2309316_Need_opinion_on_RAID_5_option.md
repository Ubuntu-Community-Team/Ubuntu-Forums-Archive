---
title: "Need opinion on RAID 5 option"
date: 2016-01-09
forum: Server Platforms
---

### Post by kevdog on 2016-01-09
I've never installed a software raid system -- I have used a hardware RAID card with linux before, however once you buy the RAID card it never seems like the firmware gets updated.
I've read up on the mdadm options, and it doesn't look all that intimidating (this said from a person who has never used it before).

My question really however is more of an opinion.
My old hardware RAID 5 system worked great for a while, until a lot of drives started failing.  I never had simaltaneous failures, however after I was on my third failed hard drive, the array refused to build on the newly installed drive -- and I tried several. I became frustrated since after about the 5th hard drive, I knew I was going to have to start over installing the system.  My goal is to try to prevent this mess -- and yes I understand things are supposed to work better than my experience.

I currently have a 1.5 Tb drive acting as my backup server running 14.04 Ubuntu Mate.  Unfortunately the machine is setup to act as an afp server which functions as a Time Server to backup a lot of the MAC systems I have running.  I'm quickly finding 1.5 Tb is not anything remotely close to what I need for a backup server.  I'm not only using Time Machine as a backup option, but also using rsync as a duplicate backup system which rsyncs the users home directories nightly.  Yes redundancy, however I've found you can't be too cautions with on-site backup options, since I've had many drives fail. 

My question is simple -- am I better off just buying a very large HD -- 3Tb perhaps, of deploying a RAID solution.  In theory the RAID solution is great because I think I can just add more hard drives to the equation if I need more space, however I'm very concerned how robust this solution is.  For example -- is mdadm very reliable -- does it survive upgrades from LTS to LTS? Should the root or base file system be placed on a non-RAID partition and the user directories by placed only a the RAID volume? Does it matter?  If everything crashes and I need emergency backup -- if I installed an Ubuntu base system on a separate drive, could I easily recover the data on the RAID system?  

Any opinions would be very helpful since I have no real world experience using mdadm, particularly when failures begin to occur.

---

### Post by lile001 on 2016-01-10
A lot of silence here - nobody wants to weigh in?.  I had absolutely no luck with software RAID - endless frustration.  Hardware RAID was cheap and was a snap.  That's what I'd go with.

---

### Post by QIII on 2016-01-10
Perhaps there is a lot of silence because people are spending the weekend with their families?

---

### Post by Bucky Ball on 2016-01-10
> **lile001 said:**
> A lot of silence here - nobody wants to weigh in?.  I had absolutely no luck with software RAID - endless frustration.  Hardware RAID was cheap and was a snap.  That's what I'd go with.

Your other thread regarding how simple raid is doesn't seem to mention anything about RAID5 or software RAID, which is what the OP is wanting support with. Please address the support request. Thanks.

Hardware RAID is cheap and a snap? Perhaps, but you haven't explained to the OP how to use RAID5 with it.

---

### Post by CharlesA on 2016-01-10
> **kevdog said:**
> I've never installed a software raid system -- I have used a hardware RAID card with linux before, however once you buy the RAID card it never seems like the firmware gets updated.
I've read up on the mdadm options, and it doesn't look all that intimidating (this said from a person who has never used it before).

I have mdadm running on my backup server and while there is a bit of a learning curve, I found this page to be a tremendous help.
[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm)

> My question really however is more of an opinion.
My old hardware RAID 5 system worked great for a while, until a lot of drives started failing.  I never had simaltaneous failures, however after I was on my third failed hard drive, the array refused to build on the newly installed drive -- and I tried several. I became frustrated since after about the 5th hard drive, I knew I was going to have to start over installing the system.  My goal is to try to prevent this mess -- and yes I understand things are supposed to work better than my experience.

I can definitely relate to this. While my situation was similar - it was not exactly the same. I ran into issues with the RAID card I was using where the driver wouldn't build properly via DKMS, so I would have to compile the kernel modules from scratch whenever a new kernel was released. It worked, but it was a pain and after I migrated away from that card (new server, new card, new drives), I didn't even bother using that card in my backup server. I just stuck with mdadm because I thought it would be less of a headache and it was.

> I currently have a 1.5 Tb drive acting as my backup server running 14.04 Ubuntu Mate.  Unfortunately the machine is setup to act as an afp server which functions as a Time Server to backup a lot of the MAC systems I have running.  I'm quickly finding 1.5 Tb is not anything remotely close to what I need for a backup server.  I'm not only using Time Machine as a backup option, but also using rsync as a duplicate backup system which rsyncs the users home directories nightly.  Yes redundancy, however I've found you can't be too cautions with on-site backup options, since I've had many drives fail. 

Kinda similar to my setup - I have one server that handles backups from the desktop machines here, but I mostly use it to backuip my Steam folder and any movies I have. It basically acts as a NAS and media server for me. I run RAID cuz I did not want to trust my data to a single disk - even with backups. Granted, I mostly got it so I didn't have as much downtime in the event a drive went out, but it has also allowed me to pool more storage than I would be able to with just a single disk.

> My question is simple -- am I better off just buying a very large HD -- 3Tb perhaps, of deploying a RAID solution.  In theory the RAID solution is great because I think I can just add more hard drives to the equation if I need more space, however I'm very concerned how robust this solution is.  For example -- is mdadm very reliable -- does it survive upgrades from LTS to LTS? Should the root or base file system be placed on a non-RAID partition and the user directories by placed only a the RAID volume? Does it matter?  If everything crashes and I need emergency backup -- if I installed an Ubuntu base system on a separate drive, could I easily recover the data on the RAID system?  


I can only speak for myself, but I have always had the OS drive as a separate single drive, but if you want, you can add that to the array as well, but the set up gets a bit more complicated. I also have images of the OS drive, so even if that drive goes out, I can reimage it and be ready to go with the same configuration as before. Even if you start from scratch, mdadm can detect the type of array from the superblocks of the drive, but it is also a good idea to back up your configuration files so you can just tell mdadm which order the drives should be assembled in and whatnot.

As far as having a hardware card goes, everything should be fine even if you reinstall the OS from scratch. You will likely have to add an entry to fstab to get the array to mount where you want it, but all data should be preserved since the OS only sees one huge drive, rather than a bunch of smaller ones that need to be assembled.

I cannot speak to how well mdadm handles a LTS to LTS upgrade directly, but mine survived the upgrade from Wheezy to Jessie with no problems.

FWIW, I've been running a RAID6 array off an LSI MegaRAID 9260-8i for uh.. ages. I had to check and it looks like I put it into place in mid-2013 and so far it's been running strong.

---

### Post by SeijiSensei on 2016-01-10
> **kevdog said:**
> I've never installed a software raid system -- I have used a hardware RAID card with linux before, however once you buy the RAID card it never seems like the firmware gets updated.

What kind of hardware RAID are we talking about here?  Cards that use [SAS]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022629&IsNodeId=1&bop=And&Order=PRICE&PageSize=90") are well-supported in the Linux kernel.  The technology is old enough to be reliable without needing firmware upgrades.    They're not cheap, but we're talking servers here.

> Is mdadm very reliable -- does it survive upgrades from LTS to LTS? Should the root or base file system be placed on a non-RAID partition and the user directories by placed only a the RAID volume? Does it matter?  If everything crashes and I need emergency backup -- if I installed an Ubuntu base system on a separate drive, could I easily recover the data on the RAID system? 

The Linux MD system resides in the kernel and has been there for many years now.  So it will certainly survive upgrades.  I generally put the root file system outside the RAID array and assign /home and /var to RAID.  Those are the places where a lot of disk activity takes place.  

Recovery depends entirely on how bad the crash is.  If you lose two of the three drives in a RAID5 setup, you're toast.  Software RAID1 has the nice feature that you can mount the remaining drive of the pair as a normal device.  So if /dev/md0 binds /dev/sdc1 and /dev/sdd1 together, and /dev/sdd fails, you can still mount /dev/sdc1 directly.

---

### Post by MAFoElffen on 2016-01-10
I used to be a fan of hardware raid. I still have it here in "spots." It is spendee if you want cards with options and some flexibility. An IO card that just does RAIO... Is a trap. You have to be able to get to it to be able to use. And it has to have options to rebuild and do maintenance. Some of the drawback of some vendors cards, are cards that you have to use their software (from their optical disk) to use... find one that works from bus-add-on type BIOS extensions, not one that the system only sees from their drivers. Some cards you can only get to if you are in a Boot Sequence. Others have Win and Linux utilities to get to while running... I tend to stay with Adaptec and LSI based cards. Some cards do not do JBOD. You may not think much on that, until you need to add a native drive and find a card that can only do it-- by adding as a logical single RAID0!!! (That adds a RAID drive marker to the drive.)

I still have SCSI RAID towers here with 15k Ultra 360's ... that look neat as drives in the tower spin up in the round and the status lights start flashing. They sound like an airplane warming up. They are not as fast as modern drives. They do not stored as much as a single modern drive. They generate enough heat to heat a small house. They use a lot of electricity. Technology advanced. Now 7.6k and 10k SATA or SAS 6GB/s and plus faster throughput drives.

Note that above, I said used to be a fan of Hardware RAID...

I am a very big fan of mdadm Linux Software RAID. So much so ... that I became the project lead of a mdadm "gui wrapper" project. That project stalled when I went back to school, but it's a tell on how much I trust and believe in mdadm. All the things that I said to look for in flexibility and access with hardware RAID, is there with mdadm. It has been tested and proven to be trustworthy in production environments. The mdadm Linux RAID has now been around long enough to prove itself. Enough, that MS now has it's own version of software RAID that they push, that I feel that is still trying to emulate mdadm.

I learned from Zack Reed's tutorials, his blog and his answers to my questions here... from those, I created my own, played, and learned.

The drawbacks you mentioned, are present with all systems, whether RAID (HW or software) or not. Disks eventually fail. Nothing lasts forever, so have a Recovery plan that accepts that eventuality. RAID is not a replacement for a good backup plan. I tend to preferred RAID 6 over RAID 5. I do RAID 1 for samll system disks. I do not do RAID0. It's not a solve all and sometimes it's another layer that some people do not need. There is some cost to disk and performance. <-- you have to accept that and have enough benefit to need it to use it. Some say it's a blessing. Some will say it is cursed. 

I used to try to recover my failed RAID members. For uptime, I've learned tha sometimes it's just faster and easier to redefine and restore. There are times to recover, but there is a cost to weigh.

I also like using LVM... Their is a lot of flexibility in LVM. I was wary of it at first, until I learned it's in's and outs. Some servers I do LVM over RAID ... I've learn to trust it enough that some of my servers, I just use LVM (without RAID). On those, if any problems, it's faster for me to just redefine storage and restore what was there.

That's just my 2-cents.

---

### Post by kevdog on 2016-01-13
Not to get off topic -- but on a similar vain -- rather than mdadm and RAID 5/6 - does anyone have any real world experience with using ZFS? I'm aware ZFS was originally an Oracle Project and has been a BSD project for years, however OpenZFS has now been on linux for some time and I've read it's going to be included in the upcoming LTS release 16.04.  ZFS offers similar RAID 5 RAID 6 capabilities, however its implemented differently.  I'm well aware with running a ZFS system, the cost of this solution is going to be significantly higher -- ECC RAM, possible inclusion of 2 SSDs for l2arc and log, in addition to standard platter drives.  It seems like this system may be more robust -- but it definitely seems more complex.  On paper it seems doable, however I know no one who has actually set this up.

---

### Post by darkod on 2016-01-13
ZFS is definitely more robust and I see it as directly designed for storage. I have used it as part of FreeNAS for a project, and I have not heard complaints so far. I think plenty of people use ZFS especially in large storage.

But like you said, it adds more costs and setup complexity if you want to include separate l2arc and log (in that FreeNAS project I did not). You should also consider if for a "home server" you need the additional SSDs etc.

I haven't looked directly at OpenZFS but there is a stable version of zfs for ubuntu years back. There is a repository you can add and use apt-get to install and update it. I don't know how Canonical will do it in 16.04, we have to wait and see. Or maybe check the daily builds for zfs packages.

People in general seem to comment zfs raidz and raidz2 are better than raid5 and raid6 (no write hole, etc), but that is also a question up to what point ZFS is really better than mdadm.

My personal experience with little testing and only one smaller project, is that I liked the principles of zfs and how it works. Gives flexibility too, especially when adding storage in future. No need to think about LVM to expand storage, you simply add new storage to the pool and that's it. With mdadm you can't join one raid5 to an existing one unless you use something like LVM... So you need to plan good in advance too.

---

### Post by CharlesA on 2016-01-13
I've heard about ZFS from FreeNAS but I haven't actually used it. I believe rubylaser uses RAIDZ2 on his systems.

---

### Post by MAFoElffen on 2016-01-14
Oracle inherited/acquired it's ties to ZFS when they bought up Sun Microsystems (Solaris). In some ways, LVM reminds me of ZFS pools. I used it with Solaris and OpenSolaris. At about the time that Oracle brought about the demise of OpenSolaris, I looked into the early versions of ZFS Fuse support in Linux. At the time it was still in it's infancy and a bit lacking (support from Linux). 

I still use it with Solaris. And ... Ubuntu 16.04  Xenial LTS (from the dailys) has ZFS utilities natively, in "universe" repository, so I've been installing and testing Xenial Server on a native ZFS root filesystem. It's a round about kind of install if done on fresh. When you get to the partitioner, then pop out to a prompt to install the tool set and set up your pool. Some say it's about a wash to alternately install into a small normal partition, setup things, mount it, then rsync into the new filesystem... then delete the old and add than into the pool. 

To do it, note a change from other peoples intructions for that:
```

sudo apt-get remove spl spl-dkms    # this is just to make sure it is not there -- I install it in the next line anyways...
sudo apt-get install spl spl-dkms      # then this, so the the source is there for zfs-dkms to compile
sudo apt-get install zfs-dkms           # once the order is straight, and the dependent source is there, then this will compile without errors and adds the modules
sudo apt-get install zfsutils-linux zfs-initramfs  # these have to be installed last
sudo modprobe zfs   # if this fails, then you didn't have the order above, in the right order...

```
The project was at GitHub ... Found it --> [Here it is]("https://github.com/zfsonlinux"). 
The project's wiki has some tutorials. But, look at my notes above to avoid compile errors on the install of the tool set and the kernel modules. I think they said to install the tools first, and do not mention spl at all. It tries to add spl and spl-dkms as dependencies, but in the wrong order.

So-- if you add spl and spl-dkms manaually first, then zfs-dkms next... then everything else falls into place nicely.

---

### Post by lukeiamyourfather on 2016-01-20
> **kevdog said:**
> ...does anyone have any real world experience with using ZFS?

Yes. If the primary purpose of the machine will be serving files then it's a no-brainer. Nothing else compares to ZFS in this regard. People online often refer to ZFS users as snobbish but if you use ZFS for a while you'll understand why (because it's awesome). I started using ZFS on Linux a few years ago both at work and at home. I taught an introductory class about it a while back which might be helpful.

[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

I'll be doing a refresher soon with updated information since ZFS will be included with Ubuntu starting with the next version. The underlying information is still the same though, like how to setup pools, what the advantages are, etc. If your question is does it work, should I use it, is it any good, then the answer in my opinion is yes.

---

