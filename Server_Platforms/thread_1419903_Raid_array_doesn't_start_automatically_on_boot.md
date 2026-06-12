---
title: "Raid array doesn't start automatically on boot"
date: 2010-03-02
forum: Server Platforms
---

### Post by needhelpplease on 2010-03-02
I have a strange question.

I have an Ubuntu 9.10 office server machine set up.  I have RAID mirroring with two disks.  I configured it all using Palimpsest, and it was quite easy to do.

But what's strange is it doesn't start automatically on boot.  I need to start Palimpsest every time, click on the RAID device, and use the "start" menu item to get it to start.

This is really strange ... I always want the RAID array to start.  Surely there's some way to get it to run automatically?  If power goes down, no one else in the office here is going to know how to get it started.

Thanks

---

### Post by needhelpplease on 2010-03-02
Well, I got it working by adding a line in /etc/mdadm/mdadm.conf.  It took me a little bit to get that line right.  It would be nice if Palimpsest did that automatically or had an option to do it, otherwise it's quite confusing.  mdadm.conf itself is pretty easy, capable of auto-detecting most stuff.

---

### Post by Technophobia on 2010-03-30
And that line was?

---

### Post by rabidfruitbat on 2010-05-26
The line I used to create my array was:

sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 --spare-devices=1 /dev/sda4 /dev/sdb2 /dev/sdc1

sudo mdadm --detail /dev/md0 gives

/dev/md0:
        Version : 00.90
  Creation Time : Thu May 27 09:40:22 2010
     Raid Level : raid1
     Array Size : 78148096 (74.53 GiB 80.02 GB)
  Used Dev Size : 78148096 (74.53 GiB 80.02 GB)
   Raid Devices : 2
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu May 27 12:34:56 2010
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

           UUID : 3d37b024:eba80adf:62e5881a:7af1fa37 (local to host thomasd-ubuntu)
         Events : 0.18

    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       18        1      active sync   /dev/sdb2

       2       8       33        -      spare   /dev/sdc1

So with that info I added the following line to my mdadm.conf file:

ARRAY /dev/md0 devices=/dev/sda4,/dev/sdb2,/dev/sdc1 spares=/dev/sdc1

Rebooting my machine automatically starts up the array with the spare drive.

Hope this helps.  Thomas D.

---

### Post by raraki on 2010-06-04
same issue with 10.04 LTS on a RAID created with Disk Utility 2.30.1; manually adding ARRAY definition to /etc/mdadm/mdadm.conf was required. I agree it would be great to have Disk Utility do it automatically, or at least provide a checkbox option.

---

### Post by bohemier on 2010-08-02
Raraki, I second that suggestion... The Disk Utility's new raid function are a great addition. Although they are still basic, they do the most common task quite well... it just needs to have an option for automatically bringing the array online at boot.

Thanks for your post, it helped me figure out this step.

---

### Post by arrrghhh on 2010-08-02
Are either "Disk Utility" or "Palimpsest" provided by Ubuntu or mdadm?  

If not, it's probably best to stick with mdadm to configure.  Adding another program to configure something just adds another layer of complexity - and something else to fail.  Just my .02.  

I don't use software RAID, so I don't really have experience with mdadm, but I assume it can be configured directly without these other software suites that have been mentioned.

---

### Post by jacekk015 on 2010-08-03
In mdadm.conf ALWAYS use UUID instead of disk names /dev/sda...
System sometimes like to mix drive names, and then you have a problem. UUID is unique.

To get needed line which you have to add to mdadm.conf use this:
```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```It will add needed lines to the end of mdadm.conf

Go there and edit this conf file to your needs. This command give a list of all raid arrays with UUID's.

---

### Post by llmc on 2011-01-21
> **jacekk015 said:**
> In mdadm.conf ALWAYS use UUID instead of disk names /dev/sda...
System sometimes like to mix drive names, and then you have a problem. UUID is unique.

To get needed line which you have to add to mdadm.conf use this:
```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```It will add needed lines to the end of mdadm.conf

Go there and edit this conf file to your needs. This command give a list of all raid arrays with UUID's.


For anyone looking to fix this problem, this does work. 

However, if you have any spaces in the name of your raid array. You will need to edit mdadm.conf by adding quotes to the value for the "name" parameter as mdadm doesn't spit these out. Otherwise, mdadm will not properly parse the file for later operations.

---

