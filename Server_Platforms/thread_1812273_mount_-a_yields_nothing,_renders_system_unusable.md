---
title: "mount -a yields nothing, renders system unusable"
date: 2011-07-26
forum: Server Platforms
---

### Post by donniezazen on 2011-07-26
Hello,

I formatted a 1.5 Tb western digital external usb drive to ext4 for media streaming on ubuntu-server. I tried FAT32/NTFS before but it keeps unmounting itself for no reason. I tried everything i could find on Google but no luck. Discussion is stalled on this thread.
> [http://ubuntuforums.org/showthread.php?p=10969653&posted=1](http://ubuntuforums.org/showthread.php?p=10969653&posted=1)

After formatting it to ext4, it worked OK for a while but for some reason it has stopped working. Running mount -a makes system unusable indefinitely. It works only if i restart it.

> UUID=db261dd6-2edf-4020-a0f5-17613a6e94ea  /media/wd  ext4 defaults 0  0

Is ext4 not a compatible format for external drive? Since, i have i tried different formats and Ubuntu keeps unmounting them. Should i try a different distro? Any suggestions?

Thanks.

---

### Post by Wayne_V on 2011-07-26
I would first check dmesg and see if you are getting errors from that drive.

Then, run fsck on the partition you are trying to mount and make sure the filesystem is good.

You could also run a read test on the drive with badblocks:  badblocks -sv /dev/sd[abcd?]

Some USB drives will also report SMARTD data.  Try this:

sudo apt-get install smartmontools

sudo vi /etc/default/smartmontools
>>>>> uncomment 'start_smartd=yes\


sudo /etc/init.d/smartmontools start


sudo smartctl -a /dev/sd[abcd?]

---

### Post by donniezazen on 2011-07-27
> **Wayne_V said:**
> I would first check dmesg and see if you are getting errors from that drive.

Then, run fsck on the partition you are trying to mount and make sure the filesystem is good.

You could also run a read test on the drive with badblocks:  badblocks -sv /dev/sd[abcd?]

Some USB drives will also report SMARTD data.  Try this:

sudo apt-get install smartmontools

sudo vi /etc/default/smartmontools
>>>>> uncomment 'start_smartd=yes\


sudo /etc/init.d/smartmontools start


sudo smartctl -a /dev/sd[abcd?]

> dmesg log

[15606.856008] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #12320769 offset 0
[15608.105264] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #12320769 offset 0
[15608.105734] EXT4-fs (sdb1): previous I/O error to superblock detected
[17992.382059] EXT4-fs error (device sdb1): ext4_find_entry: reading directory #12320769 offset 0
[17992.382530] EXT4-fs (sdb1): previous I/O error to superblock detected
[18178.031685] EXT4-fs (sdc1): recovery complete
[18178.032193] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[21911.973962] EXT4-fs (sdc1): mounted filesystem with ordered data mode

Full log can be found here. [http://pastebin.com/Yt3v6BK4](http://pastebin.com/Yt3v6BK4)

> fsck log

sudo fsck.ext4 -v /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)
wd: clean, 1406/91578368 files, 7587058/366284288 blocks

> sudo smartctl -a /dev/sd[abcd?]


smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD       15EADS External  Version: 1.75
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

Thanks for your help.

---

### Post by Wayne_V on 2011-07-27
[17992.382530] EXT4-fs (sdb1): previous I/O error to superblock detected
[18178.031685] EXT4-fs (sdc1): recovery complete
[18178.032193] EXT4-fs (sdc1): mounted filesystem with ordered data mode

I see the device changed from sdb to sdc - was this due to switching usb ports?

Are things working better now that fsck passed and you aren't seeing errors in dmesg anymore?  If not, try this:

In one terminal window, run "sudo tail -f /var/log/{dmesg,syslog,kern.log,messages} | tee ~/diskerrors.log"

Plug the drive in if it is not already.

Assuming the drive is sdc, run:

sudo smartctl -a -T permissive /dev/sdc
sudo smartctl -a -T verypermissive /dev/sdc
sudo badblocks -sv /dev/sdc
(this will take a long time on a 1.5T drive, you can ^C it at any time tho).

If you see any errors in diskerror.log or the smartctl/badblock output please post.

---

### Post by bakegoodz on 2011-07-28
Is it a external Seagate FreeAgent Drive? Sounds like a issue one of my coworkers was having were it would sleep during a large copy. He found out the drive had a sleep mode that Linux couldn't deal with. There is a fix here. [http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

---

### Post by donniezazen on 2011-07-28
I am running badblocks command. 9 hours and down to 66%. I will try if it stills unmounts after all the checks.

Should ext4 be more stable than ntfs or their will be no major difference? NTFS is preferable because of portability.

---

### Post by donniezazen on 2011-07-29
I ran badblock command and no error was found. I get following error when i try to run smart command. Let me see it works now. 

> donnie@ubuntu:~$ sudo smartctl -a -T permissive /dev/sdb1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD       15EADS External  Version: 1.75
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page

Error Counter logging not supported
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
Device does not support Self Test logging
donnie@ubuntu:~$ sudo smartctl -a -T verypermissive /dev/sdb1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Device: WD       15EADS External  Version: 1.75
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page

Error Counter logging not supported
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
Device does not support Self Test logging

---

### Post by bakegoodz on 2011-08-02
I looked up your hard drive model number, its one of those damn green drives. There are known issues with these drives and linux.
[http://kerneltrap.org/mailarchive/linux-kernel/2008/4/10/1396844](http://kerneltrap.org/mailarchive/linux-kernel/2008/4/10/1396844)

There is utility to fix this problem.
[http://forum.wegotserved.com/index.php/topic/18567-fix-for-wdeas-green-drives-intellipark-found/](http://forum.wegotserved.com/index.php/topic/18567-fix-for-wdeas-green-drives-intellipark-found/)

---

