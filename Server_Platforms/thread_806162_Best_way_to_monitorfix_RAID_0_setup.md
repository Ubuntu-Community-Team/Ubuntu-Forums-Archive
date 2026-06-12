---
title: "Best way to monitor/fix RAID 0 setup?"
date: 2008-05-24
forum: Server Platforms
---

### Post by nitts on 2008-05-24
I did some searching and wasn't able to find much (might be I don't know the words to use), so I'll pose this question as a new thread:

I have a personal webserver that I leave in a closet and want to have to manage as little as possible.  However, the data on there is fairly important to me, so I set up a fault tolerant RAID1 platform.

It occured to me that I don't know how I will know if one disk fails and even if I wanted to check, what is the best way to do so. 

As I was pondering this, I had to reboot and it forced a check and gave me this error:
"contains a file system with errors, check forced"
Then said I would have to run a manual FSCK because of RAID.  However, I'm not sure how to do that in a safe manner.

So my questions are:
1) How can I set up notification of failure
2) How can I monitor it manually (command?)
3) How can I fix the problems that it detected?

thanks!!
-Nitts

---

### Post by elvinatom on 2008-05-24
how did you set up your array?

---

### Post by nitts on 2008-05-24
I was afraid someone would ask that--it was about a year ago and I don't remember exactly.  I know that I followed the menus via the LiveCD.

Also, I made a typo earlier--it's a RAID 1 setup (mirrored drives).  I don't care about performance, only reliability.

If I run mdadm on the 3 I get the following output:

**mdadm --detail /dev/md0**
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Jun  9 16:48:39 2007
     Raid Level : raid1
     Array Size : 29294400 (27.94 GiB 30.00 GB)
    Device Size : 29294400 (27.94 GiB 30.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat May 24 14:54:51 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 8b76a38f:f1608cca:14993f08:5cf407e5
         Events : 0.47

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1






**mdadm --detail /dev/md1**
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Jun  9 16:48:45 2007
     Raid Level : raid1
     Array Size : 289088 (282.36 MiB 296.03 MB)
    Device Size : 289088 (282.36 MiB 296.03 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri May 23 16:27:49 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 2e18f3ae:5f0b671c:c277cc46:759c600b
         Events : 0.42

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2





** mdadm --detail /dev/md2**
/dev/md2:
        Version : 00.90.03
  Creation Time : Sat Jun  9 16:48:52 2007
     Raid Level : raid1
     Array Size : 263465920 (251.26 GiB 269.79 GB)
    Device Size : 263465920 (251.26 GiB 269.79 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sat May 24 07:36:13 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : f164b959:8b86af94:6821f1a6:1153f439
         Events : 0.68

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3

---

### Post by nitts on 2008-05-24
**from /proc/mdstat:**

more /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda3[0] sdb3[1]
      263465920 blocks [2/2] [UU]

md1 : active raid1 sda2[0] sdb2[1]
      289088 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      29294400 blocks [2/2] [UU]

unused devices: <none>

---

### Post by samosamo on 2008-05-24
when a disk fails, mdadm can notify you via email (which by your own means can then notify you by SMS, or phone call).  after you define your email address try using mdadm --manage to flag a drive as "failed" to test it, then when you see it works set it as active again.

from man mdadm.conf:

>        MAILADDR
              The  mailaddr  line  gives  an E-mail address that alerts should be sent to when is
              running in --monitor mode (and was given the --scan option).  There should only  be
              one MAILADDR line and it should have only one address.

       MAILFROM
              The mailfrom line (which can only be abbreviated to at least 5 characters) gives an
              address to appear in the "From" address for alert mails.  This can be useful if you
              want  to  explicitly  set  a  domain, as the default from address is "root" with no
              domain.  All words on this line are catenated with spaces to form the address.

              Note that this value cannot be set via the mdadm commandline.  It is only  settable
              via the config file.

---

### Post by windependence on 2008-05-24
One word of advice. Never, never, never subsitute RAID for backup. RAID is purely protection against hardware failure. You still need to set up regular backups if this data is important to you like you say. 

One more thing, remember that with mirrored drives when one drive gets corrupted, hacked, or attacked by virus, the other one does too, almost immediately. This is why you should have regular backups, preferrably several times a day if the data is important to you.

-Tim

---

### Post by nitts on 2008-05-25
I agree.  I do back it up to a USB drive about twice a month.

My comments was really meant to show
1) I value fault tolerance over performance or space
2) Despite backups, I don't want to have to use them.  I'd prefer the system to just run as long as possible with no intervention/restore by me.

Thanks for the comments so far.  I'm trying to make sure I know how to bring it back online once I mark it as faulty.  Don't want my "test" to turn into a self-induced failure!

---

### Post by acy76 on 2009-05-29
Hello all --

I've just built a system using software RAID and have it configured (via mdadm, cron job and smartmon or whatever it's called) to email me in the event of a failure. The trouble is that I didn't install any LAMP services as this is strictly a file server so I am not sure if I even have any sort of mail agent(s) installed.

Can anyone advise? The post above mentioned a method to test the email feature, but if that fails which agent is recommended? Or is it ok by default?

Thanks.

---

### Post by slick666 on 2009-07-06
Also looking for some raid monitor software. It seems like someone would have written a simple app that would sit in your gnome Panel and just give you the status. E-mail is nice but I would like some sort of visual feedback.

---

### Post by fjgaude on 2009-07-06
> **windependence said:**
> One word of advice. Never, never, never subsitute RAID for backup. RAID is purely protection against hardware failure. You still need to set up regular backups if this data is important to you like you say. 

One more thing, remember that with mirrored drives when one drive gets corrupted, hacked, or attacked by virus, the other one does too, almost immediately. This is why you should have regular backups, preferrably several times a day if the data is important to you.

-Tim

I tell you, Tim, you give good advise based upon experience. All thank you!

frank

---

### Post by windependence on 2009-07-06
Hehe, Frank, I've been there, done that, and got the T-shirt ya know? 

It doesn't matter how they do the RAID, it isn't a substitute for good IT practices as you and I both know. 

You should change your avatar to "Software RAID Guru"  :-)

-Tim

---

