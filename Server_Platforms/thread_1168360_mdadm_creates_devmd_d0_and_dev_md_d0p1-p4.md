---
title: "mdadm creates /dev/md_d0 and /dev md_d0p1-p4"
date: 2009-05-24
forum: Server Platforms
---

### Post by spectre_25gt on 2009-05-24
I recently set up a software raid1 array and instead of seeing /dev/md0 as I expected, I saw /dev/md_d0 and /dev/md_d0p1-p4 show up. Had I only seen md_d0, I would guess that the addressing had just changed since the last time I set up software raid (ubuntu 6.06). The other entries leave me wondering, though. 

Could anyone shed some light on this apparent change? I haven't seen any information on it no matter how hard I look.

---

### Post by fjgaude on 2009-05-25
Do you recall what command you used to create the array?

---

### Post by grantemsley on 2009-05-25
> 
Could anyone shed some light on this apparent change? I haven't seen any information on it no matter how hard I look.

That looks like the format for a partitionable raid array.  If you created it with -a or --auto options, you might get that.

I'm not sure what the pros or cons are of setting up the array that way.

---

### Post by spectre_25gt on 2009-05-26
I can't believe my history goes back this far. It should have been:

```

sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```

It looks like I tried it a couple of times in different ways, though... I had gotten some errors saying that /dev/sdb1 or /dev/sdc1 were busy and couldn't be opened. I'm guessing the raid had already started syncing and I wasn't aware.

At any rate, those were the only switches I used. That I know for sure.

---

### Post by fjgaude on 2009-05-27
Were the drives, partitions ever used in a raid array before? If so, were the superblocks zeroed before you used the --create command?

Can you simply start over?

---

### Post by spectre_25gt on 2009-05-28
I zeroed the superblock a couple of times, but it just kept coming out that way.

I was able to use /dev/md_d0 as the raid device. I'm really more interested in finding out what's behind this than coming up with a resolution. There's obviously something going on that could be really useful to know about.

Thanks for all of the input so far, btw.

---

### Post by grantemsley on 2009-05-28
What's in /etc/mdadm/mdadm.conf?

---

### Post by fjgaude on 2009-05-28
What version of OS are you using? What version of mdadm?

---

### Post by spectre_25gt on 2009-05-28
> **fjgaude said:**
> What version of OS are you using? What 
version of mdadm?

I'm on Ubuntu 9.04. I'm not sure how to check the version of mdadm. raidutils version info below:

Package: raidutils
State: installed
Automatically installed: no
Version: 0.0.6-8ubuntu1
Priority: optional
Section: universe/admin
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 36.9k
Depends: dpt-i2o-raidutils
Description: Transition Package for raidutils rename to dpt-i2o-raidutils
 The package previously named raidutils, used for manipulating some Adaptec I2O
 RAID hardware, has been renamed dpt-i2o-raidutils.  This package helps ease
 that transition.
Homepage: [http://i2o.shadowconnect.com](http://i2o.shadowconnect.com)

---

### Post by irishdunn on 2009-05-31
Having the same issue, I just did a fresh install with some new drives. I can create the array fine, but when I restart I get those silly devices.

---

### Post by milli on 2009-06-08
I found the same problem after an upgrade to linux-image-2.6.28-11-server (Jaunty, 9.04) when the /etc/mdadm/mdadm.conf file inside the initrd image had information that did not match the UUIDs of the real arrays, thus auto-start failed leaving me with /dev/md_d0, /dev/md_d1 and /dev/md_d2 instead of /dev/md0, /dev/md1, and dev/md2 as expected.

I then ran "mdadm --stop /dev/md_d0", then on md_d1, etc, to clear the bad assemble attempt (check /proc/mdstat to see), then ran "mdadm --auto-detect", mainly to just see what the issue was with auto-starting of the arrays, however it created them again but properly this time.  I then let it finish the boot process at that point.  All seemed fine.  After the system was up, I then force-recreated the mdadm.conf file so the UUIDs matched...  "/usr/share/mdadm/mkconf force-generate /etc/mdadm/mdadm.conf"  (copy your mdadm.conf to /var/tmp or something first, if you want to diff it later).  Then ran "update-initramfs -u" to re-build the initrd images.  Then I rebooted.

Reboot went fine.  All arrays recognized and auto-started properly.  No leftover /dev/md_d0 and friends, so I have to assume that when the arrays auto-start properly, at some point they are renamed to match what's in /etc/mdadm/mdadm.conf.  *shrug* YMMV.

---

### Post by littlegreiger on 2009-06-08
I'm getting the same problem, however when I run the command you gave "mdadm --auto-start" it says command unrecognized, what version of mdadm are you running?

---

### Post by milli on 2009-06-09
Sorry, it's "mdadm --auto-detect".  I corrected it in my last post too.

---

### Post by ubuntastic on 2009-06-10
milli,
 
Just wanted to say thanks for your post.  It solved my issues with a new raid array I created and I'd been scratching my head for days on this...

Daniel

---

### Post by ShadowDncr01 on 2009-07-27
I'm not going to say RTFM ;) because it's not straight forward if your not used to reading man pages ... For a detailed explanation please see the man page for mdadm under the heading "For create, build, or grow" option "--auto".  Relevant quotations below.  If you need anything else on this topic please reply and I'd be happy to go further in depth :).  Best of Luck!

-a, --auto{=no,yes,md,mdp,part,p}{NN}[INDENT]..."yes" requires the named md device to have a ’standard’ format, and the type and minor number will be determined from this.   See  DEVICE  NAMES below. 

... If --auto is not given on the command line or in the config file, then the default will be --auto=yes.
[/INDENT][INDENT] ... For partitionable arrays, mdadm will create the device file for the whole array and for the first 4 partitions.  [/INDENT]and under DEVICE NAMES:[INDENT]The standard names for non-partitioned arrays (the only sort of md array available in 2.4 and earlier) are either of
[/INDENT][INDENT][INDENT]/dev/mdNN
              /dev/md/NN[/INDENT][/INDENT][INDENT]where NN is a number.  The standard names for partitionable arrays (as available from 2.6 onwards) are either of
[/INDENT][INDENT][INDENT]/dev/md/dNN
              /dev/md_dNN[/INDENT][/INDENT][INDENT]Partition numbers should be indicated by added "pMM" to these, thus "/dev/md/d1p2".
[/INDENT]

---

### Post by iLLNiSS on 2009-10-24
im also having the same issue.

ive got 7x 1TB hdds and ive just created a new raid5 array
> sudo mdadm --create /dev/md0 --level=5 --raid-devices=7 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdh

right after that, my cat /proc/mdstat shows:
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda[0] sdh[6] sdf[5] sde[4] sdd[3] sdc[2] sdb[1]
      5860574976 blocks level 5, 64k chunk, algorithm 2 [7/7] [UUUUUUU]
      [>....................]  resync =  0.0% (178544/976762496) finish=455.6min speed=35708K/sec
      
unused devices: <none>


this seems odd since its a new array. ive zero'd all the superblocks many times.. examine shows no traces of being in an array before i create it. either way, i let it sync up overnight. i came back this morning and after a reboot"
> 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdb[1](S)
      976762496 blocks
       
unused devices: <none>

if i ignore it format it, after reboot sdb1 still ends up in md_d0.. i stop md_d0, and reassemble md0, then it adds a drive as a spare, tries rebuilding gets to about %5 then fails. degrading the array and making it unusable.

this md_d0 keeps showing up no matter what i do. mdadm --auto-detect shows absolutely nothing. and i also couldnt hot remove sdb1 from md_d0
> sudo mdadm /dev/md_d0 --remove /dev/sdb1
mdadm: cannot get array info for /dev/md_d0


any ideas?

---

### Post by iLLNiSS on 2009-10-24
well it looks like i got everything working the way its supposed to now

i just had to recreate it with the assume clean flag.. and then remove md_d0 again after reboot and again update my initramfs

```
/dev/md0:
        Version : 00.90
  Creation Time : Sat Oct 24 11:31:18 2009
     Raid Level : raid5
     Array Size : 5860574976 (5589.08 GiB 6001.23 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 24 12:04:44 2009
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : c2fd3d25:1045e221:65a04b8d:362531ae (local to host SERVER)
         Events : 0.2

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8      112        1      active sync   /dev/sdh
       2       8        0        2      active sync   /dev/sda
       3       8       16        3      active sync   /dev/sdb
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf
       6       8       48        6      active sync   /dev/sdd

``````
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdf[5] sde[4] sdd[6] sdh[1] sdb[3] sdc[0] sda[2]
      5860574976 blocks level 5, 64k chunk, algorithm 2 [7/7] [UUUUUUU]
      
unused devices: <none>
```

---

### Post by milli on 2009-10-25
Glad you figured it out.

Yeah, don't forget the --assume-clean flag so it doesn't resync...  sure, there will be block differences, but thats all unused space and you're going to wipe it with a new filesystem anyway.

The final trick is to make sure you update /etc/mdadm/mdadm.conf with the correct (new) UUIDs and then run 'update-initramfs -k all -u' to copy that new config file into the initrd image(s) so auto-detection and assembling of the arrays happens properly at boot time.

---

### Post by hollinch on 2009-11-29
Hello all,

I am having the exact same problems, trying to create a mirror called /dev/md0, all of a sudden the /dev/md_d0 and their siblings appeared, even claiming the secondary disk of the first array, leaving md0 degraded with a single disk.

I followed the instructions given above, and created the mdadm.conf file, followed by the update to initramfs. I hope that fixes it.

What I am very much interested in is not only how to fix it (and thanks by the way for the instructions and comments), but _**why**_ this happens. Is there a reason for this behaviour, is there anyone that can explain why these devices appear, why it steals one of my disks? Is it a bug perhaps?

Many thanks for any additional insight.

---

### Post by mikedep333 on 2010-05-11
I upgraded to Ubuntu 10.04.

I created my raid array back in 9.04. I used the entire block device (drive) as the raid members, rather than partitions.

I then went to re-create the array in 10.04
```
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb /dev/sdc
```
I then added the mount point to /etc/fstab (note that I created the partition on /dev/md0 previously in 9.04. You can create your's in palimpsest disk utility)
```
/dev/md0p1  /media/backups ext3 errors=remount-ro 0 1
```
Next thing I knew, it wouldn't let me mount the raid filesystem/partition (/dev/md0p1) on startup
```
device already mounted or mount point busy
```
After running cat /proc/mdstat, I found the following
```

md_d0: inactive md0p1[0](S)
md0: active raid1 /dev/sdc[1] /dev/sdb[0]

```
I had the following devices:
```

/dev/md/d0p1
/dev/md/d0p2
/dev/md/d0p3
/dev/md/d0p4

```
and the links to them:
```

/dev/md_d0p1
/dev/md_d0p2
/dev/md_d0p3
/dev/md_d0p4

```
Apparently this /dev/md_d0 device was stopping me from mounting my real md partition /dev/md0p1. I fixed it with the following command:
```
mdadm --stop /dev/md_d0
```
I then rebooted and it mounted my /dev/md0p1 fine. In fact, GNOME even hid /dev/sdb1 and /dev/sdc1, so I didn't actually mess with the underlying drives in the raid array. Thus, all was good.

---

### Post by chapmangeo on 2010-05-24
Try the "--auto=md" switch when creating the array (ie, "mdadm --create --auto=md).  That specifies a non-partitionable RAID device (ie, usable as a standard partion, not a pseudo-drive).

You can also specify auto=md as an option in the mdadm.conf file.

---

### Post by rytec on 2010-12-17
> **milli said:**
> I found the same problem after an upgrade to linux-image-2.6.28-11-server (Jaunty, 9.04) when the /etc/mdadm/mdadm.conf file inside the initrd image had information that did not match the UUIDs of the real arrays, thus auto-start failed leaving me with /dev/md_d0, /dev/md_d1 and /dev/md_d2 instead of /dev/md0, /dev/md1, and dev/md2 as expected.

I then ran "mdadm --stop /dev/md_d0", then on md_d1, etc, to clear the bad assemble attempt (check /proc/mdstat to see), then ran "mdadm --auto-detect", mainly to just see what the issue was with auto-starting of the arrays, however it created them again but properly this time.  I then let it finish the boot process at that point.  All seemed fine.  After the system was up, I then force-recreated the mdadm.conf file so the UUIDs matched...  "/usr/share/mdadm/mkconf force-generate /etc/mdadm/mdadm.conf"  (copy your mdadm.conf to /var/tmp or something first, if you want to diff it later).  Then ran "update-initramfs -u" to re-build the initrd images.  Then I rebooted.

Reboot went fine.  All arrays recognized and auto-started properly.  No leftover /dev/md_d0 and friends, so I have to assume that when the arrays auto-start properly, at some point they are renamed to match what's in /etc/mdadm/mdadm.conf.  *shrug* YMMV.

Milli, thanks also for this useful post, this worked for me too and after a few reboots still can see my raids and mounts.

---

### Post by gilligan8 on 2011-03-03
I know this is old... but I'm experiencing this.

I have no problems following these instructions and I'm grateful they are here.

But I really want to know what is going on here... why is this happening... why did it not happen in my 8.04 system?

---

### Post by gilligan8 on 2011-03-03
For the record I didn't have to do the initrd stuff.

I think we all should have just forced the rebuild of the mdadm.conf file.

I just wonder why it changed from my last server to this one.  My mdadm.conf looks default on my 8.04 server.

---

### Post by dtfinch on 2011-03-03
As I understand it (non-authoritative):

At some point Ubuntu switched from using startup scripts to using much simpler udev rules to assemble mdadm raids, which brought a lot of new bugs, as can be expected whenever redoing something from scratch. 
[https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)

The specific udev rule is in /lib/udev/rules.d/85-mdadm.rules

An --incremental option was added to mdadm to speed up udev autoassembly, which Ubuntu started using in 9.10. But it had a bug when multiple instances of itself are trying to add devices at the same time, confusing it and causing these phantom raids to sometimes appear.
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/157981](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/157981)
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/615186](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/615186)

---

### Post by gilligan8 on 2011-03-03
Wait a second... does the failure notification NOT work at this point?!?

> 4. No notification of users/admins about raid events, i.e. disk failures (email question suppressed during install without any buzzer/notify-send replacement.) 

535417 mdadm monitor feature broken, not depending on local MTA/MDA or using wall/notify-send

If I read that correctly, and I hope I'm not, then this makes the raid practically useless.

Anyone know?

---

### Post by Regenpak on 2011-03-16
FWIW- I'm experiencing similar issues with my 20-disk 33TB XFS RAID6 array. I *did* find that the UUID in mdadm.conf did not match the actual UUID. After running mdamd --auto-detect it started up with one disk (/dev/sdr, pretty random) in the dreaded /dev/md_d0. After stopping that and (re-)adding the disk to the array it started rebuilding in degraded mode but mounted just fine. Now I'm looking at a 3376.6 minute rebuild (at 3.1%)...

This server clearly is not yet ready for prime time.

---

### Post by rubylaser on 2011-03-16
> Wait a second... does the failure notification NOT work at this point?!?
Notification works fine.  The problem is that Ubuntu doesn't setup the local email portion for you as part of the initial setup as is done on Debian.  If you've setup Postfix, exim4, or some other MTA, and verified that it can send you emails, you're all set as long as you have a line like this in your /etc/mdadm/mdadm.conf file.
```
MAILADDR me@gmail.com
```
or like this if you want it to go to the local user...
```
MAILADDR root@localhost
```


You can verify that it works by sending yourself a test message like this...
```
mdadm --monitor -m me@gmail.com /dev/md0 -t
```

---

### Post by rubylaser on 2011-03-16
>  I did find that the UUID in mdadm.conf did not match the actual UUID
How did you create your /etc/mdadm/mdadm.conf file?

---

### Post by gilligan8 on 2011-03-16
Negative.

I was sending out mail just fine with `mail` on the command line.  But mdadm would not send out emails.

What about that link I posted?

---

### Post by rubylaser on 2011-03-16
I might have missed it, but all I see is a quote from you.  Do you have a link that that quote came from? I upgrade my mdadm to the newest stable version (3.1.4), but in this case it shouldn't make a difference. I use Postfix on my machine, and everything works great.  Here's an email to my gmail...
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

Edit: noticed you said you are able to send email with mail to a local user.

---

### Post by gilligan8 on 2011-03-16
Sorry, it was a link above me that I quoted.

[https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)

I have since rebuilt the system as a debian system but I BELIEVE that test messages worked but pulling power on a device never sent out an email.

---

### Post by rubylaser on 2011-03-16
I just read this part...
> mdadm package was patched to suppress the debconf email question, without setting up mdadm --monitor to use wall or notify-send as an alternative.
So, upgrading mdadm to a newer version could potentially fix this for you.

Edit:
Nevermind.  I need to read the rest before I post :)  It's just not pulling in an MTA/MTD as a dependency, so installing / configuring Postfix should be all you need to do.
> To send out notifications mdadm needs a sendmail command (MTA mail transport agent ).

To deliver mail localy you need a mail delivery agent (MDA)

I thought you just told me your box didn't send out the test email from the mdadm --monitor command?  If it can't send out a test email, of course it's not going to work when you "test" it for real :)  Test messages and failed disk messages all work on my Ubuntu 10.04 fileserver at home.

---

### Post by rubylaser on 2011-03-16
Have you verified that the monitoring daemon is running?
```
root@fileserver:~# ps aux | grep mdadm
root      1678  0.0  0.0   4516   496 ?        Ss   Mar08   0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog

```

If it shows, up, you should be able to verify your email was generated and sent by viewing  /var/log/syslog Here's the test email I sent earlier.

```
root@fileserver:~# tail -n 200 /var/log/syslog | grep postfix | tail -n 5
Mar 16 15:22:42 fileserver postfix/pickup[7655]: A8BFB58027B: uid=0 from=<root>
Mar 16 15:22:42 fileserver postfix/cleanup[13898]: A8BFB58027B: message-id=<20110316192242.A8BFB58027B@fileserver.example.net>
Mar 16 15:22:42 fileserver postfix/qmgr[1476]: A8BFB58027B: from=<root@fileserver.example.net>, size=878, nrcpt=1 (queue active)
Mar 16 15:22:46 fileserver postfix/smtp[13900]: A8BFB58027B: to=<me@gmail.com>, relay=smtp.gmail.com[209.85.225.109]:587, delay=3.8, delays=0.09/0.32/0.91/2.5, dsn=2.0.0, status=sent (250 2.0.0 OK 1300303296 xi12sm726487icb.6)
Mar 16 15:22:46 fileserver postfix/qmgr[1476]: A8BFB58027B: removed

```

---

### Post by gilligan8 on 2011-03-16
Negative... I only said mdadm wasn't sending out emails... that is a ambigious statement but I honestly can't remember.  I think the test email DID get sent but the real message wouldn't send.  I could be mistaken.

I have no way to test this now as I rebuilt it under Debian and moved forwards... I did all the same steps with Debian (established an MTA first and tested before installing mdadm) and everything "just works".

---

### Post by rubylaser on 2011-03-16
> everything "just works"
Good that's the main point.  Debian works great.  I manage a large number of Debian servers at work, and that's what I normally use for our webservers.  I'm glad to hear it's working.  To put anyone else's mind to rest, it works fine on Ubuntu if you set up the MTA, and make sure you have the relevant entries in /etc/mdadm/mdadm.conf.

---

### Post by gilligan8 on 2011-03-16
I like Ubuntu for their package support being this is my personal server and I sometimes try things that aren't typical for production servers but I just had to move forward with this project.

Have you tried a "real" test and pulled power on a drive?  I'm just concerned that test work but real notifications don't.

---

### Post by rubylaser on 2011-03-16
Sure, I have.  I've been running mdadm for a few years now.  I've even experienced a SATA port dying on one of the servers at work.  Everything is pretty easy to recover from. For example, here's a thread I was posting in yesterday with a real world mdadm recovery issue.
[http://ubuntuforums.org/showthread.php?t=1707416]("http://ubuntuforums.org/showthread.php?t=1707416")

---

### Post by gilligan8 on 2011-03-16
On Ubuntu Server 10.4 LTS?

I had it working fine on 8.04 also.

---

### Post by rubylaser on 2011-03-16
Yup, on Ubuntu 10.04 (as the OP was running in the link I just gave you).
```
root@fileserver:~# cat /etc/issue
Ubuntu 10.04.2 LTS \n \l
```

Since 10.04 only came out April of 2010, I haven't been running on this version of Ubuntu for years (if that's what you meant). My original array came from Debian Etch and was a RAID5.  I've since reshaped the array to RAID6, and migrated it Ubuntu Server 10.04.

I've run/tested mdadm on Ubuntu 10.10, and Debian 4/5/6.  If I'm going to trust my data to something, I always test first.  There are lots of posts on this forum alone with people running mdadm on 10.10 and 10.04 that have had disks fail or power outages, that ask questions about getting their arrays back to a clean state.

---

### Post by gilligan8 on 2011-03-16
Cool... I just wanted to make sure we were Apples to Apples, you know.  I also didn't want you to be thinking since --test worked that a real failure would be caught when it wouldn't... luckily that isn't the case.

I wish you'd have come along before I switched but, it is what it is.

I knew it didn't make sense to release "server" where mdadm didn't actually work.

---

### Post by Regenpak on 2011-03-17
> **rubylaser said:**
> How did you create your /etc/mdadm/mdadm.conf file?
I don't remember if I used the method with the grep of /proc/mdstat (prolly not) but I think it was created when I created the 20-member RAID6 array. The new UUID was edited manually into it.

BTW- I also forgot some system details: Ubuntu Server 10.04.2 running on a consumer mobo (MSI 880GM-E41) with AMD 910e Phenom ii and 4GB DDR3 memory. System disk Corsair 32GB SSD. Disks connected via port multipliers to SB710 SATA1-4.

---

### Post by rubylaser on 2011-03-17
Can you post the output of the
```
mdadm -E /dev/sdx
```
for example...
```
root@fileserver:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d4e58776:640274d8:e368bf24:bd0fce41
  Creation Time : Sun Aug  1 16:26:04 2010
     Raid Level : raid6
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 5860558848 (5589.06 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Wed Mar 16 19:59:36 2011
          State : clean
Internal Bitmap : present
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 56a3b461 - correct
         Events : 16876

         Layout : left-symmetric
     Chunk Size : 512K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      129        5      active sync   /dev/sdi1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8       81        7      active sync   /dev/sdf1

```
on a couple of the disks in your RAID array.  Also, how did you partition the disks in your array?
Finally, this is how I set my mdadm.conf file up.
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

mdadm works based off of UUIDs in the superblock, so the disk order should not matter for assembling the array.

---

### Post by gilligan8 on 2011-03-17
I personally used the --brief option and that gives you basically the line for your mdadm.conf.

---

### Post by rubylaser on 2011-03-17
How does that give you a mdadm.conf file with email MAIDADDR setup in the case of a  disk failure?  The brief output looks significantly different that what I posted.
```
root@fileserver:~# mdadm --brief --verbose --detail /dev/md0
ARRAY /dev/md0 level=raid6 num-devices=8 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41
   devices=/dev/sdb1,/dev/sde1,/dev/sdd1,/dev/sdc1,/dev/sdg1,/dev/sdi1,/dev/sdh1,/dev/sdf1


```

vs. what I posted

```
root@fileserver:~# cat /etc/mdadm/mdadm.conf 
DEVICE partitions
HOMEHOST fileserver
MAILADDR me@gmail.com
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41

```

Unless, I'm completely not understanding what you mean, there isn't enough info in the --brief syntax to alert you via email if a disk failed. And I like to use partitions as it's a little more flexible if for whatever reason the disk order changes and one of your mdadm disks is no longer using a little that explicitly mentioned in the DEVICE section. Also the line needs to read device, not devices to work properly.

---

### Post by gilligan8 on 2011-03-17
Sorry, I was only speaking of getting the ARRAY line.

The rest was good default... obviously I edited the MAILADDR to reflect my address vs root (default).

---

### Post by Regenpak on 2011-03-17
@rubylaser: I did not partition the disks at all, I let mdadm handle it for me. The rationale is that it needs to create stripes on the disks which negates the need for a partition. I also use the whole disks so it would not be necessary. mdadm is not complaining about it anyway.

The output for the failed disk is:
```
# mdadm -E /dev/sdr
/dev/sdr:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 49e79528:59c773e6:0f7276c9:c9ff80fb (local to host fileserver)
  Creation Time : Sun Mar 13 13:33:39 2011
     Raid Level : raid6
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 35163260928 (33534.30 GiB 36007.18 GB)
   Raid Devices : 20
  Total Devices : 20
Preferred Minor : 0

    Update Time : Thu Mar 17 15:16:54 2011
          State : clean
 Active Devices : 19
Working Devices : 20
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 35bc8ea6 - correct
         Events : 70

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this    20      65       16       20      spare   /dev/sdr

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8       64        4      active sync   /dev/sde
   5     5       8       80        5      active sync   /dev/sdf
   6     6       8       96        6      active sync   /dev/sdg
   7     7       8      112        7      active sync   /dev/sdh
   8     8       8      128        8      active sync   /dev/sdi
   9     9       8      144        9      active sync   /dev/sdj
  10    10       8      160       10      active sync   /dev/sdk
  11    11       8      176       11      active sync   /dev/sdl
  12    12       8      192       12      active sync   /dev/sdm
  13    13       8      208       13      active sync   /dev/sdn
  14    14       8      224       14      active sync   /dev/sdo
  15    15       8      240       15      active sync   /dev/sdp
  16    16      65        0       16      active sync   /dev/sdq
  17    17       0        0       17      faulty removed
  18    18      65       32       18      active sync   /dev/sds
  19    19      65       48       19      active sync   /dev/sdt
  20    20      65       16       20      spare   /dev/sdr
```

Other disks look pretty much the same, just not "spare". The array itself is now 40% done rebuilding.

It does bring me to another thought: should the "DEVICES" line in mdadm.conf not be "devices" instead of "partitions", since I didn't create them?

---

### Post by rubylaser on 2011-03-17
These are the acceptable values for the DEVICES section in your situation without partitions: It's either a comma separated list of device names (/dev/sdb,/dev/sdc,etc) or partitions.  
```
DEVICE /dev/sda,/dev/sdb,etc
```
Or with a wildcard...
```
DEVICE /dev/sd*
```
Alternatively, a DEVICE line can contain the word partitions. This will cause mdadm to read /proc/partitions and include all devices and partitions found there. So, in your case, partitions is still acceptable.

And mdadm doesn't create stripes on a disc. It writes out a superblock.  Either using whole disks or partitioning the whole disk  are both acceptable.
[https://raid.wiki.kernel.org/index.php/Partition_Types]("https://raid.wiki.kernel.org/index.php/Partition_Types")

---

### Post by dtfinch on 2011-03-17
I use partitions, slightly smaller than the full disk size, out of fear that a replacement disk will turn out to be a few mb smaller than my original disks. Another fear is that something might unexpectedly overwrite the beginning or end of the disk, which really should never happen except for the the time it happened to me. One day I rebooted a server and it didn't come back up because the first sector of the disk had been zeroed somehow, and I had to use a livecd to fix it. I never figured out how it happened.

---

### Post by Regenpak on 2011-03-19
> **rubylaser said:**
> These are the acceptable values for the DEVICES section in your situation without partitions: It's either a comma separated list of device names (/dev/sdb,/dev/sdc,etc) or partitions.  
```
DEVICE /dev/sda,/dev/sdb,etc
```
Or with a wildcard...
```
DEVICE /dev/sd*
```
Well, I guess it doesn't really matter then. In fact, it could cause problems as the boot disk randomly shows up as /dev/sda or /dev/sdu. Must figure out why that is. Indeed /cat/partitions shows the unpartitioned disks (/dev/sda etc.) as partitions. Getting my fileserver properly tweaked will keep me off the streets for a while... :D

---

### Post by jokerejoker on 2011-03-20
Any effective way of simply clear out a raid array, so to start the setup over? I have been fighting with my setup for about a day now?

---

### Post by rubylaser on 2011-03-20
The easiest way is to stop and remove the array.  Next, you just need to zero the superblocks on the drives. Finally, remove your mdadm.conf file.

```
mdadm --stop /dev/md0
mdadm --remove /dev/md0
```

finally we can even delete the superblock from the individual drives:
```
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
```
You'll need to zero the superblock on each drive in the array. 

```
rm /etc/mdadm/mdadm.conf
```

Reboot, and your array will be gone.  Hope that helps.

---

### Post by jokerejoker on 2011-03-21
First I run the stop command
```

mdadm: stopped /dev/md0

```

When I run the remove command it tells me that /dev/md0 does not exists.
```

mdadm: error opening /dev/md0: No such file or directory

```

I have run the array directly to /dev/sda /dev/sdb /dev/sdc and /dev/sdd.
I think this is why it tells me while tring to zero the superblock:

```

mdadm: Couldn't open /dev/sda for write - not zeroing

```

Any ideas?

---

### Post by jokerejoker on 2011-03-21
I figured out the problem, or at least got it working. I don't know what was wrong with the /dev/sda disk, but got it cleared at last.

Turns out it was only necessary to stop the array and the zero the superblock, and finaly af reboot, and the array was gone.

Thanks for the help! You saved my day :)

---

### Post by Regenpak on 2011-03-24
Oh, this is just great. One of the four port multipliers of my 20-member RAID6 array decided to go phut. I lost /dev/sda through /dev/sde. I guess the superblocks on the remaining members got corrupted because after a reboot all members came back fine, only running:```
mdadm -E /dev/sdf
```
shows /dev/sda as "removed" and b-e as "faulty removed". /dev/sdc and sdd show all members and /dev/sda and sdd & sde show /dev/sdc and sdd as "faulty". Is there a way to restore the superblocks on the first five members or did I totally lose the array and need to rebuild from scratch? Even besides the point why the port multiplier failed? mdadm now only wants to start with 15 members...

Edit: will try [this link](http://arstechnica.com/civis/viewtopic.php?f=16&t=121767) first.

Edit2: I did:
```
mdadm --create /dev/md0 -v -l 6 -n 20 /dev/sd[a-t]
```
and now it's resyncing. 2889.7 minutes to go according to /proc/mdstat. I guess that's what you get when you build such large arrays.

---

### Post by rubylaser on 2011-03-24
I'm glad you where able to recover your array.  If you think about it, it's fairly amazing that you "lost" 5 disks from your RAID6 array, and where still able to recover.

---

### Post by gilligan8 on 2011-03-24
I've lost TWO from my 4 disc raid 5 and recovered!


Granted, I swapped boards on the drive and was able to make one working drive from the two bad ones.  I guess I'm just lucky that I was able to save the drive that went out last!

---

### Post by Regenpak on 2011-03-27
> **rubylaser said:**
> I'm glad you where able to recover your array.  If you think about it, it's fairly amazing that you "lost" 5 disks from your RAID6 array, and where still able to recover.
Amazing indeed! It's back online now and everything's OK. Now I've got to figure out why I lost the five members in the first place. Has to be a hardware failure (/var/log/messages is your friend...).

---

