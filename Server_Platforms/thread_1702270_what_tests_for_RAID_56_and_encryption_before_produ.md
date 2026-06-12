---
title: "what tests for RAID 5/6 and encryption before production?"
date: 2011-03-07
forum: Server Platforms
---

### Post by alfonso78 on 2011-03-07
Hi,

I'm planning to install a box for NAS + HTPC so I can't use dedicated solutions and I chose to install ubuntu on it.

The box will have an unencrypted SSD for / and a RAID5 or RAID6 array with encryption for data. Before I trust all my data to the new system, I'd like to run a couple of tests.

I'd like to test a failure of a disk and test also what would happen if the OS disk would fail. what should I save from the OS to be able to access the encrypted disk from a new installation?

do you have any suggestion?

thanks,

---

### Post by Vegan on 2011-03-07
If you are going that route make sure your RAID card is a better quality model.

Also make sure you realize that you will still need a backup strategy.

---

### Post by alfonso78 on 2011-03-07
> **Vegan said:**
> If you are going that route make sure your RAID card is a better quality model.

Also make sure you realize that you will still need a backup strategy.

Hi and thank you!

Which route?

I plan to use software RAID, not HW.

---

### Post by supremedalek on 2011-03-07
If you are doing what I am thinking, the encrypted partition is on the top of the array. So, if array looses up to the max allowed number of drives, you can slap new ones and tell it to rebuild. If you are moving raid to new machine, you just have to make sure to get array back up and running first. Then you can worry about the encrypted stuff; after all, all you need to know is the encrypted passwd and the commands you need to unlock it. 

What Vegas was saying is that it is harder to retrieve data from the raid if you also have encryption on the top of it. So, you better have a backup. Raid != backup.

---

### Post by alfonso78 on 2011-03-07
> **supremedalek said:**
>  you just have to make sure to get array back up and running first. Then you can worry about the encrypted stuff

yes, that is exactly my point. I'd like to familiarize myself with that procedure now that the disks are empty and I'm not sweating, rather than when something will go wrong and I'll be under pressure.

is there any link or howto you can suggest?

My plan is to build the RAID + encryption system and to the following two tests:

- remove/format one disk and test the RAID rebuilding process

- backup the needed files (??) from the OS disk, wipe it and then reinstall the system and try to restore the RAID + encryption to access the data.

and yes, I will have a backup for critical stuff. Either an external usb drive or a crashplan account...

thanks!

---

### Post by YesWeCan on 2011-03-07
If your priority is data safety use RAID10. Do not use RAID 5. If you insist on using distributed parity then use RAID6.

Making sure you can recover from a failure before you risk your data is a very wise approach. Many folks just assume that RAID guarantees recovery.

Some suggested tests:
- multiple power failures while writing
- disconnect a sata disk while writing
- disconnect more than one disk while reading

---

### Post by alfonso78 on 2011-03-07
> **YesWeCan said:**
> If your priority is data safety use RAID10. Do not use RAID 5. If you insist on using distributed parity then use RAID6.

Making sure you can recover from a failure before you risk your data is a very wise approach. Many folks just assume that RAID guarantees recovery.

Some suggested tests:
- multiple power failures while writing
- disconnect a sata disk while writing
- disconnect more than one disk while reading

thanks!

can you elaborate why you think RAID10 is better than RAID6?

---

### Post by YesWeCan on 2011-03-07
It is arguable. Correlation is the enemy of distributed parity systems. The fewer the drives the more reliable RAID6 is and can be more reliable than mirroring if the likelihood of drives failing is low and independent.

A couple of things worry me. One is that correlation of errors can be high if there is an undetected write corruption of a parity block followed by a resync. Another thing is that if the array does fail it is much trickier to recover data than it is for a mirror. In a mirror, even if two drives have errors the odds of those errors occurring in the same sectors is low so the original data can be reconstructed relatively easily. Another thing with mirroring is that only one drive needs to be read and some brief experiments I have done with mdadm indicated that it always chooses the same one of a pair and this is good for decorrelating failures.

I do not claim to be an expert in matters of RAID.

I have been told by experienced users that RAID5 & 6 systems should be used with UPS because of the risk of undetected parity block corruption.

---

### Post by alfonso78 on 2011-03-07
Hi and thanks for sharing!

> **YesWeCan said:**
> In a mirror, even if two drives have errors the odds of those errors occurring in the same sectors is low so the original data can be reconstructed relatively easily.

I'm not sure I follow this point. In a RAID10, if I need to reconstruct it means one drive has failed, so I will copy the content of one drive to an other one, so all problems described here [http://www.zdnet.com/blog/storage/why-raid-5-stops-working-in-2009/162](http://www.zdnet.com/blog/storage/why-raid-5-stops-working-in-2009/162) equally apply. But then again, I'm not an expert either so I might be wrong.

> **YesWeCan said:**
> Another thing with mirroring is that only one drive needs to be read and some brief experiments I have done with mdadm indicated that it always chooses the same one of a pair and this is good for decorrelating failures.

wow that sounds scary... what if when you decide to read the other disk you finally realize something went wrong?

I guess the point in understanding if RAID5 is safe or not for my needs depends on what the software RAID does when it finds an unrecoverable read error (URE) when rebuilding the array with a new disk after a disk failure.

if it prompts an error and keeps rebuilding the array, I'm quite happy knowing what file has been damaged. If it exits the procedure and doesn't allow me to rebuild the RAID array, then I'm not that happy.

---

### Post by YesWeCan on 2011-03-07
> **alfonso78 said:**
> I'm not sure I follow this point. In a RAID10, if I need to reconstruct it means one drive has failed, so I will copy the content of one drive to an other one, so all problems described here [http://www.zdnet.com/blog/storage/why-raid-5-stops-working-in-2009/162](http://www.zdnet.com/blog/storage/why-raid-5-stops-working-in-2009/162) equally apply. But then again, I'm not an expert either so I might be wrong.
The thing is, if a single drive fails in RAID10 (as in 1+0) then you just need 1 disk to rebuild from. If that disk has a bad sector then you stand a good chance of manually getting all your sectors back between it and its mirror. With RAID5, recovering a disk requires all the other drives to be readable. If any has any problem mdadm will abort the rebuild.

> I guess the point in understanding if RAID5 is safe or not for my needs depends on what the software RAID does when it finds an unrecoverable read error (URE) when rebuilding the array with a new disk after a disk failure.

if it prompts an error and keeps rebuilding the array, I'm quite happy knowing what file has been damaged. If it exits the procedure and doesn't allow me to rebuild the RAID array, then I'm not that happy.
I believe it is quite basic. It will just abort and the whole array will be unreadable. It cannot do otherwise with a RAID5 or RAID6 because it needs all the parity blocks and data blocks to be readable.

I certainly would not use RAID 5 myself. Choosing between RAID10 and RAID6 requires more thought. Another consideration if you are using the array for continuous service is that a RAID6 will take a lot longer to rebuild than a RAID1+0 and the performance of the array during the rebuild will be worse. Obviously, the benefit of RAID 6 is higher capacity efficiency.

---

### Post by alfonso78 on 2011-03-07
> **YesWeCan said:**
> If that disk has a bad sector then you stand a good chance of manually getting all your sectors back between it and its mirror.

sorry, maybe it's just too late at night, but this is where I lose you. you say "between it and its mirror" but its mirror is gone (otherwise you would be recovering the array in the first place). While rebuilding an array after a drive has been lost in RAID10, each cluster that is copied to the new drive added to the array can be found only in an other drive and as such a URE will be as deadly in RAID10 as in RAID5.

You can see a picture here:
[http://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_.28RAID_1.2B0.29](http://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_.28RAID_1.2B0.29)

---

### Post by YesWeCan on 2011-03-07
Yes. If one drive is totally unreadable and the other has any errors you are stuffed. But if both drives have bad sectors, but different bad sectors, then you should be able to reconstruct it. I have never tried this so I am just speculating. This is different to a RAID5 where any bad sectors on more than one drive will make the array unrecoverable.

---

### Post by disabledaccount on 2011-03-07
Raid10 of 4 HDDs has the same capacity and fault tollerance as Raid6, but is far better considering CPU load and overall performance (software raid).
MD can realocate damaged sectors automatically. Linux (unofficially) supports hot swap on every popular chipset, including many ATA controllers (I've tested many of them) - You can try it.
Don't forget to configure write-intent-bitmap - it saves HOURS of rebuilding time and to some level prevents data corruption in case of power outage.
Throw your SATA cables to trash, then buy SATA cables (almost every bundled cable is piece of sh... - seriously - it will fail sooner or later especially in 24h/7d operation).

edit: encryption: It's worth to consider using eCryptFS - filesystem based, provides protection **after mounting volume**, not only after removing HDD from PC (like truecrypt, dm-crypt, etc), besides it don't break FS structure - this gives better chances to recover files from final apocalypse :)

---

### Post by rubylaser on 2011-03-07
> But if both drives have bad sectors, but different bad sectors, then you should be able to reconstruct it.
This scenario really isn't any more promising than recovering from a catastrophic event on a RAID6 array.  Although, there is a minuscule possibility that a miracle will occur and the bad sectors will be in different locations :). Is RAID10 simpler to rebuild, yes.  Is it more fault tolerant than RAID6...maybe, depending on the number of disks.  The long and short is, if you want safety, backup, and verify your backup's quality.  

Finally, if I may ask, if this server is for home use, why bother encrypting the data?  This adds another potential layer of complexity in the event of recovery from a failure.  And, frankly if someone has physical access to your machine, no encryption is 100% fool proof.

---

### Post by rubylaser on 2011-03-07
If you do go with eCryptFS, make sure you backup your ~/.ecryptfs/wrapped-passphrase file.  Here's how to recover it in the event of a failure.  [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

Again, I think I'd avoid this unless you have a really compelling reason to add complexity to your setup.

---

### Post by Vegan on 2011-03-07
I will say it again, do not rely on a software RAID it will be your worst nightmare.

Get a real RAID card that is independent of the OS.

Anything less is risky in the extreme.

---

### Post by alfonso78 on 2011-03-08
Hi and thank you!

> **tomazzi said:**
> Raid10 of 4 HDDs has the same capacity and fault tollerance as Raid6

I'm sorry but I still don't understand this. Can you try to explain me?
I know that RAID6 can sustain two disk failures, but from the picture [here (link)]("http://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_.28RAID_1.2B0.29") it's clear to me that if two disks fail, you have good chances to lose half your stuff.

> **tomazzi said:**
> Don't forget to configure write-intent-bitmap - it saves HOURS of rebuilding time and to some level prevents data corruption in case of power outage.

Ok I'll look into it!

> **tomazzi said:**
> Throw your SATA cables to trash, then buy SATA cables (almost every bundled cable is piece of sh... - seriously - it will fail sooner or later especially in 24h/7d operation).

any suggestion of better cables? how do I know which one are the good ones?

> **tomazzi said:**
> 
edit: encryption: It's worth to consider using eCryptFS - filesystem based, provides protection **after mounting volume**, not only after removing HDD from PC (like truecrypt, dm-crypt, etc), besides it don't break FS structure - this gives better chances to recover files from final apocalypse :)

thanks I'll study this.

---

### Post by disabledaccount on 2011-03-08
> **Vegan said:**
> I will say it again, do not rely on a software RAID it will be your worst nightmare.

Get a real RAID card that is independent of the OS.

Anything less is risky in the extreme.
What?
Hardware raid is better due to lower CPU load and higher transfers (often lower IOPS) - but it has nothing to do with safety.
**MD is far more safe** because you'll get full logs about just everything, including SMART, and you can launch the array on ANY hardware in case your controller dies. Even top-shelve controllers are crappy when you compare logged informations - f.e. **none** of the best controllers will show you SAS/SATA cable failure. Very few top-shelve products have write-intent-bitmap functionality. And HW controllers have bugs, just like everything elese.

---

### Post by alfonso78 on 2011-03-08
> **rubylaser said:**
> 
Finally, if I may ask, if this server is for home use, why bother encrypting the data?  This adds another potential layer of complexity in the event of recovery from a failure.  And, frankly if someone has physical access to your machine, no encryption is 100% fool proof.

simply because I can live with the idea of some thief going away with my HW, but not with the idea of someone else getting hold of my data. I guess you can call it a "philosophical choice".

I agree that if someone wants **my** data it's hard to protect, but this doesn't stop you from locking your car at the end of the day, I guess... :)

---

### Post by alfonso78 on 2011-03-08
> **rubylaser said:**
> If you do go with eCryptFS, make sure you backup your ~/.ecryptfs/wrapped-passphrase file.  Here's how to recover it in the event of a failure.  [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

Again, I think I'd avoid this unless you have a really compelling reason to add complexity to your setup.

many MANY thanks. That's exactly the kind of stuff I was looking for. Is there a similar procedure on how to rebuild my RAID array in the event of fatal OS crash and rebuilt? I mean the OS will run on a separate disk, non RAID partition. Can I mount the RAID volume from the liveCD as well?

I understand it adds complexity, this is why I will test and prepare some quick howto of what to do if something goes wrong.

e.g. with truecrypt I know that if you backup the volume header you have done a good job.

---

### Post by disabledaccount on 2011-03-08
> **alfonso78 said:**
>  Can I mount the RAID volume from the liveCD as well? Yes you can :)

---

### Post by YesWeCan on 2011-03-08
> **alfonso78 said:**
> I'm sorry but I still don't understand this. Can you try to explain me?
I know that RAID6 can sustain two disk failures, but from the picture [here (link)]("http://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_.28RAID_1.2B0.29") it's clear to me that if two disks fail, you have good chances to lose half your stuff.
That Wikipedia description was surely written by someone who can read a sales brochure but has no mathematical skills. It says that RAID50 is more reliable than RAID10!!! RAID50 has got to be the ultimate nightmare - a demonic marriage of RAID5 and RAID0. :o "citation needed" no s**t.

RAID6 *can* recover from 2 dead drives. RAID1+0 *can* recover from 1 to n/2 dead drives, depending on which drives, where n is the total number of drives. Recovering a RAID6 requires that all drives are readable without error. RAID1+0 requires that just 1 drive is readable without error. It is easier to manually repair a mirror with non-overlapping bad sectors.

---

### Post by YesWeCan on 2011-03-08
> **rubylaser said:**
> This scenario really isn't any more promising than recovering from a catastrophic event on a RAID6 array.  Although, there is a minuscule possibility that a miracle will occur and the bad sectors will be in different locations :).
I would have thought the odds of two drives having read errors on the same sectors is virtually zero. That is not the same, of course, as both drives having the same error because the controller wrote the same bad data to both.

---

### Post by disabledaccount on 2011-03-08
Building reliable storage is very hard task, generally expensive. Assuring hard disk redundancy is the easiest part.
Some basic points to consider:
- typical PC PSUs are not designed to work 24h/365d - they are build of inexpensive (often low quality) components and have "economically reasonable" protection circuits (or none) - faulty/crappy PSU can kill all array members in less than second.
- HDD inrush currents: very big problem on servers. In home servers, depending on number of HDDs and PSU model, inrush currents can shorten PSU life, prevent proper booting and sometimes even kill aging PSU - fortunatelly most HDD's supports Power-on-in-standby mode.
- power surges: can kill everything, not only PC - and are very hard to elliminate. Most people's homes are not protected at all against power grid anomalies.
- electrically separated network interfaces: wired ISP network can easily kill your MB.
- air conditioning: every "big S" Server needs airconditioning. Home servers needs at least proper cooling and dust protection, because PSU, MB power sections and HDDs can't work reliable without this, except some very low-power applications. Things are getting complicated with ambient temperatures over 35deg. C. - You can either make a wind in the case or switch to water cooling.
- power outages ... thats obvious I think

---

### Post by alfonso78 on 2011-03-08
And here is a collection of idea / examples to test RAID:

[https://raid.wiki.kernel.org/index.php/Detecting,_querying_and_testing](https://raid.wiki.kernel.org/index.php/Detecting,_querying_and_testing)

---

### Post by disabledaccount on 2011-03-08
I suppose that is quite old article.
First of all: SATA and SAS links supports hot-swap on hardware layer - you can't damage interface or disturb other drives data flow (because it's point-to-point connection). Hot-swap support is advertised to be supported in "proffesionall" HW only, but that's how marketing works.
ATA and SCSI buses needed special procedure for hot-swap support, due to their vulnerability to electrical bus termination and electrical bus load value. ATA however can be hot-swapped if it's done properly.

Besides, if you remove HDD from powered-off system, then You are testing ability to boot from degraded state, not ability to keep array working after HDD fails.

Several months ago one of my R1 arrays gets degraded - one of HDD's had problem with actuator connector. I've hot-unplugged it, repaired and hot-plugged back. If you are interested I can show you logs from that time as well as damaged HDD photos.

---

### Post by rubylaser on 2011-03-08
> What?
Hardware raid is better due to lower CPU load and higher transfers (often lower IOPS) - but it has nothing to do with safety.
MD is far more safe because you'll get full logs about just everything, including SMART, and you can launch the array on ANY hardware in case your controller dies. Even top-shelve controllers are crappy when you compare logged informations - f.e. none of the best controllers will show you SAS/SATA cable failure. Very few top-shelve products have write-intent-bitmap functionality. And HW controllers have bugs, just like everything elese

I agree with this 100%.  Hardware controllers do lower CPU load, but with modern CPU's, this is far less of a concern.  Also, mdadm logging is fantastic, and the argument that hardware controllers are OS independent, is true, but what about the filesystem on the array?  Finally, the ability to mount my array with any live linux distro in any machine without the hefty cost of a RAID controller is a BIG bonus for home use.

---

### Post by alfonso78 on 2011-03-09
> **YesWeCan said:**
> That Wikipedia description was surely written by someone who can read a sales brochure but has no mathematical skills. It says that RAID50 is more reliable than RAID10!!! RAID50 has got to be the ultimate nightmare - a demonic marriage of RAID5 and RAID0. :o "citation needed" no s**t.

RAID6 *can* recover from 2 dead drives. RAID1+0 *can* recover from 1 to n/2 dead drives, depending on which drives, where n is the total number of drives. Recovering a RAID6 requires that all drives are readable without error. RAID1+0 requires that just 1 drive is readable without error. It is easier to manually repair a mirror with non-overlapping bad sectors.

Hi!

I know, I'm too stubborn, but I found this in the [official MD RAID FAQs (link)]("http://git.debian.org/?p=pkg-mdadm/mdadm.git;a=blob_plain;f=debian/FAQ;hb=HEAD"):

> In a RAID10 configuration, if one disk is already dead, the RAID can only survive if any of the two disks in the other   RAID1 array fails, but not if the second disk in the degraded RAID1 array fails 

is this your point?

---

### Post by alfonso78 on 2011-03-09
> **rubylaser said:**
> If you do go with eCryptFS, make sure you backup your ~/.ecryptfs/wrapped-passphrase file.  Here's how to recover it in the event of a failure.  [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")

Again, I think I'd avoid this unless you have a really compelling reason to add complexity to your setup.

do you advice eCryptFS over dm-crypt/LUKS?

For some reason I like (from wikipedia) that LUKS specifies a platform-independent standard on-disk format for use in various tools.

But then I read [this bug report]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/531240") that states:

> When using luks encryption on top of software raid devices, it can eventually break because linux_raid_member devices get opened directly as luks instead of being assembled into md devices (Bug #531240), and all this happens silently because mdadm monitoring is not set up (Bug #491443). Additionally luks on raid root filesystems can not boot if the array is degraded (Bug #488317). It is advisable not to rely on luks on raid until a fix is released.

I can see people have different opinions but I'm not sure if it's a real issue.

In general, all this article makes me wonder if SW RAID in ubuntu is really a good idea...
[https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)

---

### Post by alfonso78 on 2011-03-09
> **YesWeCan said:**
> Making sure you can recover from a failure before you risk your data is a very wise approach. Many folks just assume that RAID guarantees recovery.

on this subject, have a look at this and shiver...
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/535417](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/535417)

---

### Post by rubylaser on 2011-03-09
Okay, I'll set some of your fears to rest.  All you have to do is enable mailing add a MAILADDR line to your /etc/mdadm/mdadm.conf file and setup email with Postfix or Exim.  Something like this...
```
MAILADDR name@gmail.com
```. You can test that the email works by doing this...
```
root@fileserver:~# mdadm --monitor /dev/md0 -t
mdadm: Monitor using email address "user@gmail.com" from config file

```

It will email you something like this...
```
This is an automatically generated mail message from mdadm
running on fileserver

A TestMessage event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [raid6] [raid5] [raid4] 
md0 : active raid6 sdb1[0] sdf1[7] sdh1[6] sdi1[5] sdg1[4] sdc1[3] sdd1[2] sde1[1]
     5860558848 blocks level 6, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]

unused devices: <none>
```

Also, I run the latest version of mdadm instead of the much older version that comes with 10.04.  You can install it like this..
```
wget http://ftp.us.debian.org/debian/pool/main/m/mdadm/mdadm_3.1.4-1+8efb9d1_amd64.deb
dpkg -i mdadm*.deb
```

SW RAID on Ubuntu or Debian is very reliable.  I've been running mdadm for years on many different systems, and never had a problem (other than the occasional hard drive failure), and I've recovered from all of these with the spare replacing the failed drive, and then I add a spare once I have a replacement.

I don't have any personal experience with an encrypted filesystem on top of mdadm, because I've never seen the point as I stated earlier.  In light of the bug reports eCryptFS looks to be the safer solution, but I personally would not even bother.  As you said earlier, you can deal with someone stealing your hardware, but not your data.  My point is, if they've stolen your hardware, they also have your data.

---

### Post by alfonso78 on 2011-03-09
> **rubylaser said:**
> Okay, I'll set some of your fears to rest.

thanks so much for taking the time. I appreciate it! :)

now to be honest I'm starting to get cold feet...

I was planning to build a powerful miniITX box (i3 550) to have a NAS + HTPC in a single box, but now I start to feel that a dedicated FreeNAS box might be more stable and tested. And I could save on energy bill and HW: instead of MB + CPU + heatsink, just embedded MB. From 260 eur to 130 eur.

In reality the money is not really the main concern, but spend more to have more trouble seems not so smart... :)

again, thank you for your help.

---

### Post by rubylaser on 2011-03-09
I've run and tested many different fileserver setups: Solaris and Opensolaris with ZFS, FreeNAS with ZFS, and even FreeBSD with ZFS besides mdadm.  I always end up back with a linux box and mdadm because of the speed, not being nearly as stringent with hardware (Solaris, etc), and much faster than FreeNAS (this was always had very slow throughput for me). Frankly mdadm has even let me down (knock on wood), and until btrfs is stable, I'll probably stay where I'm at.

I have a dedicated fileserver and  (3) Openelec.tv XBMC boxes (Shuttle XS35GT).  I have an AMD 240e processor in my fileserver, and I spin down the hard drives after being idle for an hour (finally got this working just recently).  With all of these boxes going into standby, and being energy misers, I don't see a big hit on my electrical bill.

I wouldn't worry about mdadm's stability, it's been around for years, it's well tested, and you have an extensive community here to help you if you even do have a problem that you can't solve yourself.

---

### Post by alfonso78 on 2011-03-09
Thank you!

> **rubylaser said:**
> I have an AMD 240e processor in my fileserver, and I spin down the hard drives after being idle for an hour (finally got this working just recently).

Actually this is quite an interesting topic for me as well. I hear from a friend SMB makes spinning down disks tricky.
I guess it's /var/cache/samba/browse.dat as discussed here:
[http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/](http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/)

Which sharing method you use?

is there any other way except "listening" to the disks to understand if they are actually spinning down?

*Actually I found the command to check disk status:*

```
sudo hdparm -C /dev/sdX
```

---

### Post by rubylaser on 2011-03-09
Actually, I use NFS,SMB, and AFP (I have 2 Macbooks) all from my mdadm share.  The great thing about mdadm is the array isn't unmounted to spin down the disks, so you have a slight lag to spin them back up (if they're in standby mode), but they come right back up and start sharing with all three of the aforementioned protocols with no problem.  The only thing I had to tweak was the SMART daemon to prevent it from querying my disks if they where in standby.  Otherwise it would never let them go to sleep because it was querying them every 30 minutes.

I probably don't have an issue, because the main devices that connect to the shares are all using NFS.  I only use SMB to transfer files occasionally from my wife's laptop.

---

### Post by jhayes on 2011-10-17
> **rubylaser said:**
> Actually,    The only thing I had to tweak was the SMART daemon to prevent it from querying my disks if they where in standby.  Otherwise it would never let them go to sleep because it was querying them every 30 minutes.

what did you do to make SMART "smart"? and not bug the idle drives

---

### Post by alfonso78 on 2011-10-17
> **alfonso78 said:**
> Hi,

what should I save from the OS to be able to access the encrypted disk from a new installation?


sorry I didn't copy the commands, but I can state that at least for RAID and LUKS there is no special config file to save.

mdadm is very smart in finding which devices are part of the array and once the RAID is up and running you simply should issue the commands to open the RAID and your password.

EDIT: from a USB rescue disk the commands should be:

```
sudo apt-get install mdadm

sudo mdadm --examine --scan

sudo mdadm --assemble --verbose --run /dev/md0

sudo apt-get install cryptsetup

sudo cryptsetup luksOpen /dev/md0p1 big_raid
sudo mount -t ext4 -o noauto_da_alloc,nodelalloc,noatime,nodiratime,barrier=1 /dev/mapper/big_raid /mnt/big_raid
```

---

### Post by alfonso78 on 2011-10-21
> **rubylaser said:**
> Okay, I'll set some of your fears to rest.  

Thank you rubylaser!

> 
All you have to do is enable mailing add a MAILADDR line to your /etc/mdadm/mdadm.conf file and setup email with Postfix or Exim.  


well, "all you have to do" took me a few hours to setup postfix to send emails with gmail! But I managed and the test works!

> 
SW RAID on Ubuntu or Debian is very reliable. 


maybe mdadm on its own is reliable, but it seems there is a problem with LUKS:
[https://bugs.launchpad.net/bugs/531240](https://bugs.launchpad.net/bugs/531240)

But I hope now that I setup the email notification, I will see if something goes wrong!

thank you!

---

### Post by alfonso78 on 2011-10-23
Hi guys,

if you have time, could you have a look at this thread?
[http://ubuntuforums.org/showthread.php?p=11385184](http://ubuntuforums.org/showthread.php?p=11385184)

**[COLOR="Red"]My array failed.[/COLOR]** This afternoon two disks went offline and while they were re-syncing a 3rd disk went offline and so the array failed.

I don't know where to start in trying to find the problem and thus a solution...

any idea, test, suggestion is really appreciated.

---

### Post by alfonso78 on 2011-10-23
[sorry, wrong thread]

---

