---
title: "[SOLVED] Building RAID 1 from CLI (Help?)"
date: 2008-09-06
forum: Server Platforms
---

### Post by madhartigan on 2008-09-06
Hi

I have an Ubuntu 8.04LTS server box that I've just built following the howtoforge.com "The Perfect Server" Tutorial.

I followed it to the "t" except substituted my domain "circlezero.net" for all occurences of "server1.com"

My question is how do I create two RAID drives from the two 320GB drives and two 1TB drives I have also in this box.  I want the (2)320GB drives to be RAID1 and be my /var/www drive so anything I do with my website is mirrored in case I have drive failure.  I want to use the (2)1TB drives as data drives in RAID0 for my media content that will be populated by torrent and usenet downloads.

I don't have them mounted because I don't know how my server sees them.  I don't even know if they've been recognized by the server.  I know I need to use gparted or something in order to set their filesystems to linux raid.

Then I use mdadm to create the software RAID drives.

If anyone can provide some detailed directions, I'd really appreciate it.

TIA!!

---

### Post by erwall on 2008-09-06
I've found an easy way to do RAID stuff is through Webmin.

---

### Post by fjgaude on 2008-09-06
> **erwall said:**
> I've found an easy way to do RAID stuff is through Webmin.

Can you tell us about its **mdadm** managing capability, menu based?

---

### Post by Krupski on 2008-09-06
> **madhartigan said:**
> Hi

I have an Ubuntu 8.04LTS server box that I've just built following the howtoforge.com "The Perfect Server" Tutorial.

I followed it to the "t" except substituted my domain "circlezero.net" for all occurences of "server1.com"

My question is how do I create two RAID drives from the two 320GB drives and two 1TB drives I have also in this box.  I want the (2)320GB drives to be RAID1 and be my /var/www drive so anything I do with my website is mirrored in case I have drive failure.  I want to use the (2)1TB drives as data drives in RAID0 for my media content that will be populated by torrent and usenet downloads.

I don't have them mounted because I don't know how my server sees them.  I don't even know if they've been recognized by the server.  I know I need to use gparted or something in order to set their filesystems to linux raid.

Then I use mdadm to create the software RAID drives.

If anyone can provide some detailed directions, I'd really appreciate it.

TIA!!

If you think you have already created your RAID drives, you can check by seeing if their device names exist.

They should be named '/dev/md0' and '/dev/md1'.

To check, type this:

```

sudo ls /dev/md* | sort

```

If they exist, great. Now, did you FORMAT them? If not, format the RAID drives like this:

```

[COLOR="Red"]**# WARNING! FORMAT ERASES THE DRIVE - USE CAUTION!**[/COLOR]
sudo mkfs.ext3 /dev/md0

```

Note, substitute YOUR RAID drive name for '/dev/md0' in the example.

Now that they are formatted, you should be able to mount them.

Assume a RAID drive is /dev/md0 and you created a mount point (an empty directory) called '/mnt/new-drive'.

To mount it, type this:

```

sudo mount /dev/md0 /mnt/new-drive

```

To make it auto mount, add it to your /etc/fstab file, like this:

```

/dev/md0  /mnt/new-drive   auto   defaults   0   2

```

Hope this helps...

-- Roger

---

### Post by madhartigan on 2008-09-06
OK I get

```

ls: cannot access /dev/md*: No such file or directory
```


So, obviously I have not set the drives as RAID drives.  How do I do that?

I did an ls /dev/sd* and I got:

```

/dev/sda   /dev/sdb  /dev/sdc1  /dev/sdc5  /dev/sdd1
/dev/sda1  /dev/sdc  /dev/sdc2  /dev/sdd   /dev/sde

```

I hope that helps you suggest what to do next.  I know I want to do something to some of the sd* devices but I don't know how to tell which one to do what to.

Thank you for the feedback!!

---

### Post by erwall on 2008-09-07
> **fjgaude said:**
> Can you tell us about its **mdadm** managing capability, menu based?

From webmin documentation, Hardware section:

> Linux RAID
    Support for using the MDADM tools to manage RAID devices, instead of the standard Linux RAID programs. This also allows partitions to be added to or removed from a RAID device after creation.

---

### Post by fjgaude on 2008-09-07
Wow, that sounds very interesting... I'll give it a look-see, a try, observe how the GUI is compared to using CLI mdadm.

---

### Post by erwall on 2008-09-07
> **fjgaude said:**
> Wow, that sounds very interesting... I'll give it a look-see, a try, observe how the GUI is compared to using CLI mdadm.
Meant to include a screenie w/my post, here it is:

[IMG]http://i420.photobucket.com/albums/pp284/erwall/webminmdadm.png[/IMG]

---

### Post by fjgaude on 2008-09-07
Thanks again... wonder how the menu handles failed drives, adding them, etc?

I guess I'll have to load the package and see!

---

### Post by erwall on 2008-09-07
> **fjgaude said:**
> Thanks again... wonder how the menu handles failed drives, adding them, etc?

I guess I'll have to load the package and see!
Can't comment on what happens when a drive fails, fortunately that hasn't happened to me yet.  I can say that adding drives is very easy, a couple clicks and it's done.  

Another screenie:

[IMG]http://i420.photobucket.com/albums/pp284/erwall/webminadm2.png[/IMG]

---

### Post by fjgaude on 2008-09-07
Thanks, thanks! Now I wonder who will take that portion of **webmin** and make it a GUI frontend for **mdadm**?

Such would be for those who don't run server platforms. <smile>

---

### Post by madhartigan on 2008-09-07
Sorry to interrupt the threadjack ):P

 . . . but does anyone have any answers for my original question??

---

### Post by fjgaude on 2008-09-07
> **madhartigan said:**
> Sorry to interrupt the threadjack ):P

 . . . but does anyone have any answers for my original question??

To create a software raid array in Linux you use mdadm, like so:

Install **mdadm** from the repository, then:

Using cfdisk to each drive you are to use, set the type to "fd" which is auto detect Linux raid. Then:

```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sd[n1] /dev/sd[m1]
```

with level=0 for stripping (speed), =1 is for mirroring.

where the sd[n1 and m1] are the names of the drives to use. After that you install the filesystem:

```
sudo mkfs -t ext3 /dev/md0
```

and watch it build:

```
sudo watch cat /proc/mdstat
```

This whole process is so complex, please read, study:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
   [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Have at it. You might wish to use **webmin** as suggested, but still, there is lots of learning to go through.

---

### Post by madhartigan on 2008-09-07
Well I discovered I had to go a little more basic to start off.

Based on:

```

ls /dev/sd*

/dev/sda   /dev/sdb  /dev/sdc1  /dev/sdc5  /dev/sdd1
/dev/sda1  /dev/sdc  /dev/sdc2  /dev/sdd   /dev/sde

```

I realized I first had to figure out which drive was which.  After some research I found out that:

```

fdisk /dev/sda

```

then using option "p" I was able to see the size of each disk.  I tried this for all sd devices and I found out the following:

sda = 320GB
sdb = 1000GB
sdc = 74GB (system drive)
sdd = 320GB
sde = 1000GB

SO, I removed the extraneous drives on sda and sdd.

Now, I'm left following the directions you provided on the specific drives I need to modify.  Thank you VERY MUCH to all who took the time to help me out. I really appreciate it!!

---

### Post by madhartigan on 2008-09-07
Now, I made a mistake.  I created md0 as a RAID0 array and I meant to create it as a RAID 1 array so I did this:

```

root@server1:/home/darryl# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@server1:/home/darryl# mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda5 /dev/sdd5
mdadm: /dev/sda5 appears to be part of a raid array:
    level=raid0 devices=2 ctime=Sun Sep  7 22:08:24 2008
mdadm: /dev/sdd5 appears to be part of a raid array:
    level=raid0 devices=2 ctime=Sun Sep  7 22:08:24 2008
mdadm: size set to 312568512K
Continue creating array? yes
mdadm: array /dev/md0 started.

```

But now when I try to list the md devices I get this:

```

root@server1:/home/darryl# ls /dev/md*
/dev/md0  /dev/md1

/dev/md:
0

```

What do I do about the /dev/md: entry? and how do I know that the md0 array is RAID1 and the md1 array is RAID0?

TIA!

---

### Post by fjgaude on 2008-09-07
Well, there are many, many commands to get you here and there.

To see what an array is:

```
sudo mdadm --detail /dev/md0
```

This will show many things...

Please study the links:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

And also the **man mdadm** pages... I can't tell you all the things you need to know especially when mistakes are made. Take it slow and easy.

---

### Post by madhartigan on 2008-09-07
Thank you for the links.

I'll definitely read them in my free time.

I'm not sure what the:
```

/dev/md:
0

```

entry means but here's the output from the mdadm --detail command:

```

root@server1:/home/darryl# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Sep  7 22:20:06 2008
     Raid Level : raid1
     Array Size : 312568512 (298.09 GiB 320.07 GB)
  Used Dev Size : 312568512 (298.09 GiB 320.07 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  7 23:08:16 2008
          State : active, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 71% complete

           UUID : f5548450:aa6258c7:ca1c3085:0d92b5eb (local to host server1.circlezero.net)
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       53        1      active sync   /dev/sdd5

```

I'm guessing that perhaps since the array is rebuilding, it shows up as
 
/dev/md:
0

meaning "something" is happening to array "0"

I'm going to go and read the links you provided.  I'll repost if the result of ls /dev/md* changes once the array is done rebuilding.

Thank you for your help!!

---

### Post by Krupski on 2008-09-08
> **madhartigan said:**
> OK I get

```

ls: cannot access /dev/md*: No such file or directory
```


So, obviously I have not set the drives as RAID drives.  How do I do that?

I did an ls /dev/sd* and I got:

```

/dev/sda   /dev/sdb  /dev/sdc1  /dev/sdc5  /dev/sdd1
/dev/sda1  /dev/sdc  /dev/sdc2  /dev/sdd   /dev/sde

```

I hope that helps you suggest what to do next.  I know I want to do something to some of the sd* devices but I don't know how to tell which one to do what to.

Thank you for the feedback!!

OK, if you want to figure out which drive is which, try this:

```

sudo ls -la /dev/disk/by-id | sort

```

You will get an output that looks something like this (though not EXACTLY the same):

```

root@storage:/# ls -la /dev/disk/by-id | sort
drwxr-xr-x 2 root root 320 2008-09-06 22:07 .
drwxr-xr-x 6 root root 120 2008-09-06 22:07 ..
lrwxrwxrwx 1 root root  10 2008-09-06 22:07 ata-Sony_NCFC4G_011910H0207P2150-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-09-06 22:07 ata-Sony_NCFC4G_011910H0207P2150-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  10 2008-09-06 22:07 edd-int13_dev80-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-09-06 22:07 edd-int13_dev80-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  10 2008-09-06 22:07 scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  10 2008-09-06 22:07 scsi-1ATA_Sony_NCFC4G_011910H0207P2150-part2 -> ../../sdc2
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 ata-Sony_NCFC4G_011910H0207P2150 -> ../../sdc
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 ata-WDC_WD10EACS-00D6B0_WD-WCAU40312948 -> ../../sda
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 ata-WDC_WD10EACS-00D6B0_WD-WCAU40433302 -> ../../sdb
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 edd-int13_dev80 -> ../../sdc
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 md-uuid-433488b9:a6d1d00f:2e29483d:f114274d -> ../../md0
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 scsi-1ATA_Sony_NCFC4G_011910H0207P2150 -> ../../sdc
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40312948 -> ../../sda
lrwxrwxrwx 1 root root   9 2008-09-06 22:07 scsi-1ATA_WDC_WD10EACS-00D6B0_WD-WCAU40433302 -> ../../sdb

```

Note that I can see, for example, that the WDC drives are /dev/sda and /dev/sdb... the Sony "drive" (which I know is my compact flash card) is /dev/sdc.

Now, to MAKE a RAID drive, this example will assume that the drives you wish to use are called "/dev/sda1" and "/dev/sdb1". Note, substitute YOUR actual drive names for the examples:

```

sudo mdadm -C /dev/md0 -n2 -l0 /dev/sda1 /dev/sdb1

```

This means "mdadm **[COLOR="Red"]CREATE[/COLOR]** a device called **[COLOR="Red"]/dev/md0[/COLOR]** consisting of **[COLOR="Red"]2[/COLOR]** devices setup as RAID **[COLOR="Red"]level 0[/COLOR]** and use **[COLOR="Red"]/dev/sda1[/COLOR]** **[COLOR="Red"]/dev/sdb1[/COLOR]**.

Also of course, use the RAID level YOU want (0, 1, etc...)

Then, restart mdadm:

```

sudo /etc/init.d/mdadm restart

```

See if your new RAID drive got created:

```

sudo ls -la /dev/md*

```

If it did, you will see something like:

```

brw-rw---- 1 root disk 9, 0 2008-09-06 22:07 /dev/md0

```

Now, format the RAID drive:

```

**[COLOR="Red"]# CAUTION! FORMAT ERASES ALL DATA ON THE DRIVE![/COLOR]**
sudo mkfs.ext3 /dev/md0

```

If that works, lastly add it to your /etc/fstab file (see my previous post for that info). Adding it to fstab makes the drive auto-mount at bootup.

Hope this helps!

-- Roger

---

### Post by madhartigan on 2008-09-08
Thank you for the detailed directions!!

I'm wondering when I do this:

```

root@server1:/home/darryl# ls -la /dev/md*
brw-rw---- 1 root disk 9, 0 2008-09-08 10:51 /dev/md0
brw-rw---- 1 root disk 9, 1 2008-09-08 10:56 /dev/md1

/dev/md:
total 0
drwxrwx---  2 root disk    60 2008-09-07 22:18 .
drwxr-xr-x 13 root root 14660 2008-09-07 22:20 ..
brw-rw----  1 root disk  9, 0 2008-09-07 22:18 0
root@server1:/home/darryl#

```

What is the bottom part that says /dev/md: total 0 etc.

I'm glad that my two RAID Drives are created (md0 and md1) but I'm just wondering what the bottom part is.

Also, I went to edit my /etc/fstab file and I'm confused as to what section I should put the "/dev/md0  /mnt/new-drive   auto   defaults   0   2" line?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d483d31d-62b4-4ed4-995d-1b2769ec1e87 /               ext3    relatime,errors=remount-ro,usrquota,grpquota  0       1
# /dev/sda5
UUID=c2a354b0-532e-4db9-adc6-a8023498a856 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I see the /dev/sda1 line is commented out and the /dev/sda5 line is commented out.

Can I just delete those out of the file?

should I add the "/dev/md0  /mnt/new-drive   auto   defaults   0   2" line after the /dev/fd0 line?

Thanks!!

---

### Post by Krupski on 2008-09-08
> **madhartigan said:**
> Thank you for the detailed directions!!

I'm wondering when I do this:

```

root@server1:/home/darryl# ls -la /dev/md*
brw-rw---- 1 root disk 9, 0 2008-09-08 10:51 /dev/md0
brw-rw---- 1 root disk 9, 1 2008-09-08 10:56 /dev/md1

/dev/md:
total 0
drwxrwx---  2 root disk    60 2008-09-07 22:18 .
drwxr-xr-x 13 root root 14660 2008-09-07 22:20 ..
brw-rw----  1 root disk  9, 0 2008-09-07 22:18 0
root@server1:/home/darryl#

```

What is the bottom part that says /dev/md: total 0 etc.

I'm glad that my two RAID Drives are created (md0 and md1) but I'm just wondering what the bottom part is.

Also, I went to edit my /etc/fstab file and I'm confused as to what section I should put the "/dev/md0  /mnt/new-drive   auto   defaults   0   2" line?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d483d31d-62b4-4ed4-995d-1b2769ec1e87 /               ext3    relatime,errors=remount-ro,usrquota,grpquota  0       1
# /dev/sda5
UUID=c2a354b0-532e-4db9-adc6-a8023498a856 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I see the /dev/sda1 line is commented out and the /dev/sda5 line is commented out.

Can I just delete those out of the file?

should I add the "/dev/md0  /mnt/new-drive   auto   defaults   0   2" line after the /dev/fd0 line?

Thanks!!

The lines that you call "commented out" are really just comments.

For example, it is saying that "/dev/sda1" is being mounted as "UUID=d483d31d-62b4-4ed4-995d-1b2769ec1e87" (another way to describe that drive) and it's mount point is "/" (that is, the root).

The /dev/scd0, /dev/scd1 and /dev/fd0 are two CD/DVD rom drives and a floppy drive respectively. So, here's how your final /dev/fstab file should look:



```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d483d31d-62b4-4ed4-995d-1b2769ec1e87 /               ext3    relatime,errors=remount-ro,usrquota,grpquota  0       1
# /dev/sda5
UUID=c2a354b0-532e-4db9-adc6-a8023498a856 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[COLOR="Red"]/dev/md0        /mnt/drive-01   auto    defaults    0    2
/dev/md1        /mnt/drive-02   auto    defaults    0    2[/COLOR]

```

(note: new stuff in red).

The mount points in my example (/mnt/drive-01 and -02) are just examples. What you should do is create two empty directories anywhere you wish (maybe in /home?) and use them as mount points.

For example, you may want it like this instead:

(1) Create an empty directory in /home called "public".
(2) It ends up looking like this: '/home/public'
(3) In fstab, you would use a line like this to auto mount it to your first RAID drive:

```

/dev/md0        /home/public   auto    defaults    0    2

```


Note: BE SURE to leave alone the entries already IN fstab... specifically the ones with UUID's in them. They are your system (root) and swap drives, respectively. Remove or change THESE and your system won't boot!

Hope this helps!

-- Roger

---

### Post by madhartigan on 2008-09-08
Alrighty,  I've edited my fstab to:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d483d31d-62b4-4ed4-995d-1b2769ec1e87 /               ext3    relatime,errors=remount-ro,usrquota,grpquota  0       1
# /dev/sda5
UUID=c2a354b0-532e-4db9-adc6-a8023498a856 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md0        /var/www   auto    defaults    0    2
/dev/md1        /home/data   auto    defaults    0    2

```

I hope this is what I need in order to mount RAID1 drive md0 to /var/www.(the directory already existed from my Apache install)  I do this so whatever I do in terms of my website will be mirrored to the backup drive.

I've also mounted my 2TB RAID0 drive md1 to /home/data (a directory I created) so that I have that available for my multimedia content and .iso's.

THANK YOU SO MUCH EVERYONE FOR YOUR HELP!!

I'm wondering if there is a command to list the capacity of each directory.  I know I can type ls -lh /var/www to see the information about the size of that directory but how do I see how large the directory is?

TIA

---

### Post by Krupski on 2008-09-08
> **madhartigan said:**
> 
I'm wondering if there is a command to list the capacity of each directory.  I know I can type ls -lh /var/www to see the information about the size of that directory but how do I see how large the directory is?

TIA

Yuppers... try this:

```

sudo df -H /var/www

```

Here's how it looks on my server:

```

root@storage:/home# df -H shared
Filesystem             Size   Used  Avail Use% Mounted on
/dev/md0               993G   389G   605G  40% /home/shared

```

You can see that this mount point has about 1 TB available and about 390G used and about 600G free.

Here I look at all the mounted drives:

```

root@storage:/# df -H /home/*
Filesystem             Size   Used  Avail Use% Mounted on
/dev/md0               993G   389G   605G  40% /home/shared
/dev/sdb               249G    25G   224G  10% /home/usb0

```


Hope this helps!

---

### Post by madhartigan on 2008-09-08
Fantastic!!!

Great help and Great tips.  I learned VOLUMES of information just through this short excursion.

I'm sure I'll be back with more questions regarding other things on my Ubuntu Server but for now, I'm quite satisfied!!

Thank you again.

---

### Post by Krupski on 2008-09-09
> **madhartigan said:**
> Fantastic!!!

Great help and Great tips.  I learned VOLUMES of information just through this short excursion.

I'm sure I'll be back with more questions regarding other things on my Ubuntu Server but for now, I'm quite satisfied!!

Thank you again.

Here's something else you may want to do while playing around with mount points.

There have been times when I was experimenting and *thought* I had mounted a device to a mount point, but forgot to.

So, I do this:

(1) Create the mount point (i.e. the empty directory)
(2) Leave myself a "note" in the mount point:

```

sudo echo nothing-mounted-here > /home/usb0/nothing-mounted-here

```

This places a small text file called "nothing-mounted-here" into the mount point (/home/usb0 in my example) containing the text "nothing-mounted-here".

Now, if I mount a device to that mount point, the MOUNTED DEVICE root becomes available instead and "hides" my note.

So, if I forget to mount a device, I see my note. If I read the note (with 'cat' or 'more'), I also see the note.

This has saved me many "DARNIT!!!" moments!  :)

-- Roger

---

### Post by madhartigan on 2008-09-19
That's a great tip!!  Thank you for your continuing assistance throughout this.

I'm now wondering how I can do something else.

Currently my /home/ directory and my /var/ftp directory are located on my system drive which is where installation put them by default.

I'd like to place ("mount?") them both to the md1 drive that I created but I don't know how to move them both, with their contents, to that drive.  My guess was to modify the fstab file with those mount points but that, from my minimal understanding, would simply would not work.  The data that is already currently in the /home/ and /var/ftp directory would still remain on the drive (sdc1) that they were originally mounted on.

I'm rambling so I hope I've been clear in what I want to do.  In Windows terms, I want to cut the /home/ and /var/ftp directories out of sdc1 and then paste the directories, their structure and their contents into my md1 drive.

If anyone can help I'd appreciate it!!

Thank you!!

EDIT:  Found my own answers!!  It's nice when that happens.  The instructions are for a Gentoo install but, they are fully compatible with the Ubuntu install.  [LINK](http://www.gentoo.org/doc/en/articles/partitioning-p2.xml)

---

### Post by Krupski on 2008-09-19
> **madhartigan said:**
> That's a great tip!!  Thank you for your continuing assistance throughout this.

I'm now wondering how I can do something else.

Currently my /home/ directory and my /var/ftp directory are located on my system drive which is where installation put them by default.

I'd like to place ("mount?") them both to the md1 drive that I created but I don't know how to move them both, with their contents, to that drive.  My guess was to modify the fstab file with those mount points but that, from my minimal understanding, would simply would not work.  The data that is already currently in the /home/ and /var/ftp directory would still remain on the drive (sdc1) that they were originally mounted on.

I'm rambling so I hope I've been clear in what I want to do.  In Windows terms, I want to cut the /home/ and /var/ftp directories out of sdc1 and then paste the directories, their structure and their contents into my md1 drive.

If anyone can help I'd appreciate it!!

Thank you!!

I don't know if this is the RIGHT way to do it... but it's how *I* do it (select the FTP directory).

```

sudo userdel -r ftp
sudo useradd -d /new-directory/ftp -s /bin/false -r ftp

```

First command deletes the username "ftp" *and* removes it's directory and contents.

Second command recreates the username "ftp", set's it's home directory to "/new-directory/ftp", gives it a non-shell and creates the system account "ftp".

Your FTP server has (or probably has) a config option to specify an alternate FTP directory (vsftpd does for sure), but I prefer to do it as above.

Be careful... if your CURRENT FTP directory contains files, MOVE THEM before you issue the "userdel -r" command! The "-r" means "remove the files and directory of the removed user"!

As far as mounting "/home/" in a different place... why not just put it into fstab? It should work (I think... never tried it). 

Go ahead and try it... worst that can happen is it won't work!  :)

-- Roger

---

### Post by Krupski on 2008-09-19
> **madhartigan said:**
> EDIT:  Found my own answers!!  It's nice when that happens.  The instructions are for a Gentoo install but, they are fully compatible with the Ubuntu install.  [LINK](http://www.gentoo.org/doc/en/articles/partitioning-p2.xml)

Aren't you glad to be learning the CLI rather than being a GUI weeny?  :D

---

### Post by madhartigan on 2008-09-19
It takes a lot of "fortitude" to stick with it, but I definitely enjoy the feeling of pride when I find that not only am I able to execute these commands the first time but I can also feel confident that I can pull it off again and again.

It's most enjoyable when I'm able to practically apply what I learn in these simple steps to more complex steps later on down the road.  I know, at some point, my /var/mysql database is going to outgrow my drive and I think I'll be comfortable with moving it a larger drive when the time comes.

Thanks again for the encouragement.:-D

---

### Post by Krupski on 2008-09-19
> **madhartigan said:**
> It takes a lot of "fortitude" to stick with it, but I definitely enjoy the feeling of pride when I find that not only am I able to execute these commands the first time but I can also feel confident that I can pull it off again and again.

It's most enjoyable when I'm able to practically apply what I learn in these simple steps to more complex steps later on down the road.  I know, at some point, my /var/mysql database is going to outgrow my drive and I think I'll be comfortable with moving it a larger drive when the time comes.

Thanks again for the encouragement.:-D

Yes... there's a big thrill and a great feeling of accomplishment when one gets something to work after clawing up the learning curve.

Little off topic (sorry mods!) but I have a short story.

Years ago (late 1970's) a friend of mine and I built a little computer with an 8008 cpu, a video display generator of the Don Lancaster type and 256 BYTES of static ram.

We had no keyboard, no mouse, no compiler or assembler. We had TOGGLE SWITCHES for the address and data bus!

We spent three days in a basement, fueled with iced tea and sandwiches provided by my friend's wife. We only stopped for potty breaks and quit for the night when we got so tired we began fumbling.

After three days of looking up opcodes, converting them to binary, entering them into memory one byte at a time, we finally grabbed the cliplead, reset the CPU and SUCCESS!!! The ascii letter "A" appeared on the TV screen!

I jumped up, screamed "Oh Yeah!!!" with my fists above me and accidentally rammed my knuckles into the floor joists, drawing blood!

I'll never forget the thrill... three days of programming to put a single letter on a 9 inch B&W TV set!

THOSE were the great old days of computing.

After that, it all got easier!  :)

(edit to add) *I* could have been Bill Gates... could have... :(

---

### Post by madhartigan on 2008-09-19
I appreciate the story Krupski.  It definitely pre-dates me (being 32y.o.) but, I can certainly empathize with the feeling of "Eureka".   Perhaps not through quite as much painstaking and meticulous effort but, nonetheless . . .

Now . . . .

I'm having trouble with my Samba share.  Everything is configured just in the manner that I'd like.  The problem is that Windows Vista has saved my profile as "Darryl" and I need to use a login of "darryl"  I've successfully changed my Vista username to "darryl" but the user profile still has me registered as "Darryl"

Does anyone know any way that I can change (perhaps in the registry) the way Windows is documenting my user profile?

Here's what shows up no matter how many times I try typing in "darryl"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85839&stc=1&d=1221878022[/IMG]



TIA

---

### Post by Krupski on 2008-09-19
> **madhartigan said:**
> I appreciate the story Krupski.  It definitely pre-dates me (being 32y.o.) but, I can certainly empathize with the feeling of "Eureka".   Perhaps not through quite as much painstaking and meticulous effort but, nonetheless . . .

Now . . . .

I'm having trouble with my Samba share.  Everything is configured just in the manner that I'd like.  The problem is that Windows Vista has saved my profile as "Darryl" and I need to use a login of "darryl"  I've successfully changed my Vista username to "darryl" but the user profile still has me registered as "Darryl"

Does anyone know any way that I can change (perhaps in the registry) the way Windows is documenting my user profile?

Here's what shows up no matter how many times I try typing in "darryl"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85839&stc=1&d=1221878022[/IMG]



TIA

I don't use Vista... but in XP one can go into "My Network Places", then double click "Entire Network", then double click "Microsoft Windows Network", then double click "Workgroup" (or whatever your workgroup name is), then when you see your Samba share, double click on it. 

Pick any shared folder and RIGHT click on it.

Choose "Map Network Drive"

Then choose "Connect using a different username"

You should be golden (if Vista works the same way)....:confused:

Good luck

-- Roger

---

### Post by madhartigan on 2008-09-20
It does work the same way in Vista BUT that hasn't been the problem.  The problem is that whenever I enter in "darryl" with the first letter lower-case, Windows (Vista or XP) will automatically ignore the case of the letter and automatically grab the user profile with that letter sequence (case insensitive) and use it for the login.  Linux (which is brilliantly case-sensitive) will not accept the "Darryl" login.

I know I could easily create another user on my Windows Vista PC and the linux smbpasswd file and simply use that to login but, in my opinion that's sloppy and I hate the idea of having an extraneous user on my system just for logging in to the Samba share.

There has to be a way to go into the Windows registry and modify the way the User Profile stores my name.  I just don't know where that is.

---

### Post by Krupski on 2008-09-20
> **madhartigan said:**
> There has to be a way to go into the Windows registry and modify the way the User Profile stores my name.  I just don't know where that is.

Have you tried running regedit.exe and simply search for the string "Darryl"?

If you find it, look at the other registry entries around it to see if it's the right one. It *should* be obvious... (hopefully).

I have my Samba shares setup to require no authentication. Any user can connect to my shares without a Linux username or password.

In fact, the only usernames on my Linux machine are "root" and "ftp" (not counting internal process accounts of course).

Since my NAS box is simply a file server for my home Intranet (behind a hardware firewall), I have no need for security.

If you want, let me know and I'll post my "smb.conf" file for you... it's really small and simple.

-- Roger

(edit to add): Why not simply create a new Linux user named "Darryl"??? "darryl" and "Darryl" are two different things in Linux you know! :)

---

### Post by madhartigan on 2008-09-27
Well, I created the new user "Darryl" for linux and I added it to Samba.

Samba, evidently, views "Darryl" and "darryl" as the same user.  Here's the proof:

```
root@server1:/etc/samba# smbpasswd -a Darryl
New SMB password:
Retype new SMB password:
root@server1:/etc/samba# cat /etc/samba/smbpasswd
darryl:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:19F43BA5A0C5852294EF7FE5C9150882:[U          ]:LCT-48D4526A:
root@server1:/etc/samba#

```

So, now I think I'm going to reinstall my Vista box.  I needed to do some fall cleanout of extraneous apps anyway.  I just hope this solves my problem.


Here's my smb.conf in case you can see anything else that may cause problems once I get the user issue sorted out:

```

[Global]
        workgroup = WORKGROUP
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[Data]
        path = /home/data
        invalid users = root, admin
        valid users = user1, user2
        read only = No
        create mask = 0775
        directory mask = 0775

```

Thanks!!

---

