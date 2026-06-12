---
title: "Ubuntu Server | MDADM | Power Management"
date: 2013-01-26
forum: Server Platforms
---

### Post by SAngeli on 2013-01-26
Hi,
I run Ubuntu server 12.04.1 LTS with mdadm and two RAID-1 SAta HD.
I wish to set this server that if there is no access to the HDs it will go into power saving so that I can save electricity.
I use this server as a NAS but there are long hours of inactivity during the 24h. Sometimes, I do not access it even in 2 days.

Can someone please instruct me on how to implement this? Internet references, step by step, is also welcomed if needed.

My BIOS handles Power managment as well as my HDs being two Seagate 1.5TB HD ST31500341AS

Thank you,
Spiro

---

### Post by SAngeli on 2013-01-26
Hi,
i run Ubuntu server 12.04.1 LTS on my LAN as a NAS.
I wish to setpu MDADM in a way that if something goes wrong with the array or the physical discs I am notified by email being, I assume, the only way to let the server comunicate with me.
My LAN has this server and two PC desktops runing Windows 7.

Is it possible to set the MDADM system use an existing email account with existing SMTP so that the email gets properly delivered? I ask this because if I set up local mail I fear that it will be blocked as it could be considered by other Admin systems as "an open relay email server".

How to accomplish my task?

thank you,
Spiro

---

### Post by rubylaser on 2013-01-26
I cover this in my tutorials for mdadm. [http://zackreed.me/articles/60-spin-down-idle-hard-disks]("http://zackreed.me/articles/60-spin-down-idle-hard-disks")

---

### Post by rubylaser on 2013-01-26
I use mdadm's monitor functionality + smartmontools to monitor my disks and arrays.  Then, I use sSMTP + my gmail account to send me emails. [Here's how I set it up]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp").

---

### Post by SAngeli on 2013-01-26
Hi,

it seems like I am unable to get mdadm to work. :(
After I installed all and mount the array succesfully, when I reboot I do get problems at boot time and also am unable to mount.

Here is what I get as error:
fsck da util-linux 2.20.1
fsck da util-linux 2.20.1
/dev/mapper/ubuntu-root: clean, 176010/4331248 files, 1718890/18632776 blocks
/dev/sdc1 non è stato smontato in maniera corretta, controllo forzato.
Controlle degli errori nelle unità disco. Potrebbe richiedere qualche minuto.
Premere C per annullare tutti i controlli in corso
[   21.500021] irq 18: nobody cared (try booting with the "irqpool" option)
[   21.500233] handlers:
[   21.500272] [<ffffffff81493b90<>] usb_hcd_irq
[   21.500359] Disabling IRQ #18
/dev/sdc1: 237/124496 files (4,6% not contiguous), 67105/248832 blocks
mountall: fsck /boot [284] terminato con stato 1

L'unità disco per /mnt/array_0 non è ancora pronta o non è presente.
Attendere oppure premere S per omettere il mount o M per il ripristino manuale.

Whant on hearth is happening?

/dev/sdc1 is the partition of the hd of ubuntu OS
/mnt/array_0 is the mount point of the mdadm array.

Please help.

Thank you,
Spiro

---

### Post by cariboo on 2013-01-26
Merged three threads on mdadm, in order to get all the answers in one place.

---

### Post by rubylaser on 2013-01-27
> **SAngeli said:**
> Hi,

it seems like I am unable to get mdadm to work. :(
After I installed all and mount the array succesfully, when I reboot I do get problems at boot time and also am unable to mount.

Here is what I get as error:
fsck da util-linux 2.20.1
fsck da util-linux 2.20.1
/dev/mapper/ubuntu-root: clean, 176010/4331248 files, 1718890/18632776 blocks
/dev/sdc1 non è stato smontato in maniera corretta, controllo forzato.
Controlle degli errori nelle unità disco. Potrebbe richiedere qualche minuto.
Premere C per annullare tutti i controlli in corso
[   21.500021] irq 18: nobody cared (try booting with the "irqpool" option)
[   21.500233] handlers:
[   21.500272] [<ffffffff81493b90<>] usb_hcd_irq
[   21.500359] Disabling IRQ #18
/dev/sdc1: 237/124496 files (4,6% not contiguous), 67105/248832 blocks
mountall: fsck /boot [284] terminato con stato 1

L'unità disco per /mnt/array_0 non è ancora pronta o non è presente.
Attendere oppure premere S per omettere il mount o M per il ripristino manuale.

Whant on hearth is happening?

/dev/sdc1 is the partition of the hd of ubuntu OS
/mnt/array_0 is the mount point of the mdadm array.

Please help.

Thank you,
Spiro

What's the output of these commands?

```
cat /etc/mdadm/mdadm.conf
```
```
cat /proc/mdstat
```
```
cat /etc/fstab
```

---

### Post by SAngeli on 2013-01-27
> **rubylaser said:**
> What's the output of these commands?

Hi,

here are the answers:

```
**cat /etc/mdadm/mdadm.conf**
DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f name=ubuntu:0
```

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active (auto-read-only) raid1 sdb1[1] sda1[0]
      1465006336 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

```
**cat /etc/fstab**
# /etc/fstab: static file system information.
# ============================================================================================
#
# <file system> <mount point>   <type>          <options>                       <dump>  <pass>
#
# Updated last: Jan, 26th, 2013 Time; 02:35PM
#
# ============================================================================================


proc            /proc           proc    nodev,noexec,nosuid                     0       0
/dev/mapper/ubuntu-root /       ext4    errors=remount-ro                       0       1

UUID=5be45eae-b83c-4ff8-8a29-a3d322cba241 /boot           ext2    defaults      0       2
/dev/mapper/ubuntu-swap_1 none  swap            sw                              0       0

/dev/sdc        /media/cdrom    udf,iso9660     user,noauto,exec,utf8           0       0
/dev/md0        /mnt/array_0    ext4            relatime,acl,errors=remount-ro  0       1
```

Here is some additional info, if helpful:
```
root@ubuntu:~# mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory

root@ubuntu:~# mdadm --detail --scan
ARRAY /dev/md/ubuntu:0 metadata=1.2 name=ubuntu:0 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f

root@ubuntu:~# mdadm --examine --scan
ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f name=ubuntu:0

root@ubuntu:~# mdadm --brief --detail --verbose /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
```

I have two questions:
**1.** is it possible to assign a name to the mdadm array or is it irrelevant?
This is what I refer to (what is in boldface):
*ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f **name=ubuntu**:0*

**2.** After creating the mount point "mkdir /mnt/array_0" I have to assign proper ownership. What do I assign? User Name or root or what?
Currently I assigned "chown sangeli /mnt/array_0" as I access the server with this credential.
Can you please elaborate more on what options do I have here?

Thank you,
Spiro

---

### Post by rubylaser on 2013-01-27
> **SAngeli said:**
> Hi,

here are the answers:

```
**cat /etc/mdadm/mdadm.conf**
DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f name=ubuntu:0
```

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active (auto-read-only) raid1 sdb1[1] sda1[0]
      1465006336 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

```
**cat /etc/fstab**
# /etc/fstab: static file system information.
# ============================================================================================
#
# <file system> <mount point>   <type>          <options>                       <dump>  <pass>
#
# Updated last: Jan, 26th, 2013 Time; 02:35PM
#
# ============================================================================================


proc            /proc           proc    nodev,noexec,nosuid                     0       0
/dev/mapper/ubuntu-root /       ext4    errors=remount-ro                       0       1

UUID=5be45eae-b83c-4ff8-8a29-a3d322cba241 /boot           ext2    defaults      0       2
/dev/mapper/ubuntu-swap_1 none  swap            sw                              0       0

/dev/sdc        /media/cdrom    udf,iso9660     user,noauto,exec,utf8           0       0
/dev/md0        /mnt/array_0    ext4            relatime,acl,errors=remount-ro  0       1
```

Here is some additional info, if helpful:
```
root@ubuntu:~# mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory

root@ubuntu:~# mdadm --detail --scan
ARRAY /dev/md/ubuntu:0 metadata=1.2 name=ubuntu:0 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f

root@ubuntu:~# mdadm --examine --scan
ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f name=ubuntu:0

root@ubuntu:~# mdadm --brief --detail --verbose /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
```

I have two questions:
**1.** is it possible to assign a name to the mdadm array or is it irrelevant?
This is what I refer to (what is in boldface):
*ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f **name=ubuntu**:0*

**2.** After creating the mount point "mkdir /mnt/array_0" I have to assign proper ownership. What do I assign? User Name or root or what?
Currently I assigned "chown sangeli /mnt/array_0" as I access the server with this credential.
Can you please elaborate more on what options do I have here?

Thank you,
Spiro

The reason your array is not mounting is that it's presenting itself as /dev/md/0 instead of /dev/md0.  The name line is unnecessary for proper assembly, so you can leave that out. I would do the following.

```
sudo -i
```

Remove everything from /etc/mdadm/mdadm.conf and paste this.
```
DEVICE partitions
HOMEHOST fileserver
MAILADDR youruser@gmail.com
ARRAY /dev/md0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f

```

You do not need to explicitly name your devices or name the array.  Right now, your mdadm.conf is contradicting your actual array and is causing problems. Your devices are /dev/sd[ab]1 not /dev/sd[ab]. Just use partitions, and mdadm will figure it out. mdadm is smart, it will automatically assemble the array correctly.

You can leave your /etc/fstab as is.  In regards to permissions, you can set them to whatever level of security you'd like.  If this is just a home fileserver and you want it wide open, just.

```
chmod -R 777 /mnt/array_0
```

Finally, you need to update your initramfs
```
update-initramfs -u
```

Finally, reboot, and it should come up correctly.
```
reboot
```

---

### Post by SAngeli on 2013-01-27
Excellent job. I do thank you for your help!

I have few follow-up questions so I can learn and understand.
*There is a difference between knowing things and following guides. Unfortunately, I am a guide follower :-(*

**1. **> DEVICE partitions
HOMEHOST fileserver
MAILADDR [email]youruser@gmail.com[/email]
ARRAY /dev/md0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f
HOMEHOST can I put my hostname being "ubuntu" ?

array_0 ownership.
When I created the dirctory, during setup, I typed:
```
chown sangeli /mnt/array_0
```
but now that the mount is available if I ls -la I see:
```
drwxr-xr-x  3 root root 4096 gen 26 19:29 array_0
```

should it be sangeli?
Can you please explain what should I do?

**2.** Watching a guide on [**YouTube**]("http://www.youtube.com/watch?v=mee9l1aNZdc") I was told to do the followings:
1. run "sudo mdadm --examine --scan"
2. than copy the output into clipboard
3. edit "/etc/mdadm/mdadm.conf"
4. type "DEVICE /dev/sda1 /dev/sdb1"
5. paste the mdadm output, being in my case:
ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f name=ubuntu:0

But this is wrong as you corrected me two parts:
From "ARRAY /dev/md/0" to "ARRAY /dev/md0"
and you removed "name=ubuntu:0"

Can you please elaborate for future install so I make corrections on my guide.

**3. **You also mentioned that I need to update your initramfs.
i have no clue on this. Can you please explain what is it for and when should I run it during the entire process of mdadm installation/configuration?

**4.** Lastly, is there a complete manual for beter learning mdadm?

thank you,
Spiro

---

### Post by rubylaser on 2013-01-27
> **SAngeli said:**
> 
HOMEHOST can I put my hostname being "ubuntu" ?


Yes, it can be whatever you'd like.  That's the name that will show up in logs and in emails from mdadm in the event of an issue.  Personally, I like to use a slightly more descriptive name. Also, when you chown'd the mount point, you didn't change the owner of the mdadm array.  You'd need to run this at this point.

```
chown -R sangeli /mnt/array_0/
```

> **SAngeli said:**
> 
**2.** Watching a guide on [**YouTube**]("http://www.youtube.com/watch?v=mee9l1aNZdc") I was told to do the followings:
1. run "sudo mdadm --examine --scan"
2. than copy the output into clipboard
3. edit "/etc/mdadm/mdadm.conf"
4. type "DEVICE /dev/sda1 /dev/sdb1"
5. paste the mdadm output, being in my case:
ARRAY /dev/md/0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f name=ubuntu:0

But this is wrong as you corrected me two parts:
From "ARRAY /dev/md/0" to "ARRAY /dev/md0"
and you removed "name=ubuntu:0"

Can you please elaborate for future install so I make corrections on my guide.


Those directions aren't bad, but newer versions of mdadm will include the name stanze and will write out the device line as you've seen.  It's easier to simplify the mdadm.conf as I've shown.  Also, the DEVICE line with partitions is more flexible then statically naming the disks.  If you add more hard drives to your computer in the future, this tutorial method presents the possibility to fail.

> **SAngeli said:**
> 
**3. **You also mentioned that I need to update your initramfs.
i have no clue on this. Can you please explain what is it for and when should I run it during the entire process of mdadm installation/configuration?

This does a good job of explaining the [initramfs]("http://en.gentoo-wiki.com/wiki/Initramfs").

The mdadm mailing list has lots of good info, and you can always read the manpage.
```
man mdadm
```

---

### Post by SAngeli on 2013-01-29
Hi,
so far I reached excellent results and am quite pleased. Finally I escaped FreeNas project and can rely on Ubuntu server and use the serer for different tasks rather than just for NAS services.

I wish to ask few follow-up questions regarding power management and disk management.
Yes, I followed the link provided me with and I have to say it is very well written.

1. how to manually check on hdparm and smart for when I wish to see/know how my server is doing? Let's say I wish to know if the HD is already in sleep mode or not and similar info.

2. smartd_opts="-q never -i 7200" takes care every two hours to check the HD but if they are idle it will not check. How to understand how to customize the time (7200). 7200 is for two hours. How to calculate for different hours?
Also, if smart has to check every two hours but the hd is idle for 10 hours (as an example), than it becomes operting for 10 minutes and after 1 hour it becomes ide again and does not spin anymore when would smart perform the check? Can someone please give me a hint?

3. I did not understan the last 4 commands of [**this guide**]("http://zackreed.me/articles/60-spin-down-idle-hard-disks"):
can someone please elaborate them? In particular the parameters I do not understand like (nano +22)

4. I will post my HD specs. I wish to know if you find this values valid or if is there room for enhancement as I wish to obtain maximum performance in transfer rate between the NAS server and my PC when I perform backups or move files around.
This is a Seagate 1.5TB SATA-II HD connected to a SATA-I controller (onboard IBM entry level server):

```
$ hdparm -i /dev/sda
======================================================================
/dev/sda:

 Model=ST31500341AS, FwRev=CC1H, SerialNo=9VS4AW5C
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=2930277168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

$ hdparm /dev/sda
======================================================================
/dev/sda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 182401/255/63, sectors = 2930277168, start = 0

$ hdparm -Tt /dev/sda
======================================================================
/dev/sda:
 Timing cached reads:   2304 MB in  2.00 seconds = 1151.90 MB/sec
 Timing buffered disk reads: 372 MB in  3.01 seconds = 123.53 MB/sec
```

Thank you,
Spiro

---

### Post by rubylaser on 2013-01-29
1. You can check using smartctl like this.
```
smartctl --nocheck standby -i /dev/sdb
```
Output should look like this...
```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-36-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Device is in STANDBY mode, exit(2)

```
2. The 7200 is in seconds.  There are 3600 seconds in one hour, so 3600x2=7200, or 2 hours.
3. nano +22 starts editing file on line 22 (this was the location of the DEVICESCAN line in 10.04).  Just comment out the existing DEVICESCAN line and replace with one as I've shown.
4. You should search for Samba tuning on this forum.

---

### Post by SAngeli on 2013-01-30
Hi,

the "smartctl --nocheck standby -i /dev/sda" command does not tell me if the drive is idle or active. Here is what it reports (I post the relevant info):
```
Power mode is:    ACTIVE or IDLE
```
How to know exactely which one is it?

I do not understand this section of the final instruction:
```
nano +22 /etc/smartd.conf

Comment this line out
bash

DEVICESCAN -m root -M exec /usr/share/smartmontools/smartd-runner

And add this below the commented out line.
bash

DEVICESCAN -S on -o on -a -I 194 -m username@gmail.com -s (S/../.././02|L/../../6/03) -n standby,q
```

Yes, I don't want to spin up idle hard drives but I do not understand all the above commands. Moreover, what does the email address have to do with this?

Can someone break down the listing and explain what is strictly needed for no spin up idle hd. Then, the rest.

After this implementation, I received this mail:
```
/etc/cron.daily/mdadm:
mdadm: excess host name on HOMEHOST line: NAS - ignored
mdadm: excess host name on HOMEHOST line: Server - ignored
```

How to interpret and what do to?


Lastly, I did not get a reply for what I asked in my previous post:
*Also, if smart has to check every two hours but the hd is idle for 10 hours (as an example), than it becomes operting for 10 minutes and after 1 hour it becomes ide again and does not spin anymore when would smart perform the check?*
Basically, if the HD spins down after 1 hour of inactivity and SMART is scheduled to run every 2 hours but not inspect idel hd when will it ever chech on hd? Perhaps when the HD is not idle for logher than 2 hours?

Thank you,
Spiro

---

### Post by rubylaser on 2013-01-30
Your hard drive is still spun up if it says ACTIVE or IDLE.  It would show as in STANDBY like my example if it was spun down.

There is an existing DEVICESCAN line in your smartd.conf file.  I'm asking you to comment that line out, by putting a pound (#) sign in front of the line and replacing with the line I have shown.  This revised line schedules Short and Long tests periodically on your disks, and includes the options to prevent smartd from preventing your drives from spinning down.  It contains an email address, because it will email you if smart values change on your disk (early warning or failure notice). 

The mdadm email is telling you the problem right in the message.  You have redundant HOMEHOST lines in your mdadm.conf file.  You need to only have only HOMEHOST entry in that file.

> Also, if smart has to check every two hours but the hd is idle for 10 hours (as an example), than it becomes operting for 10 minutes and after 1 hour it becomes ide again and does not spin anymore when would smart perform the check?

With the setup I have offered smart will not check the disk if it's in standby mode, irregardless of time spun up/down.  If the disk is spun up, and it's scheduled to check it, it will.

---

### Post by SAngeli on 2013-01-31
Hi,

> There is an existing DEVICESCAN line in your smartd.conf file. I'm asking you to comment that line out, by putting a pound (#) sign in front o

What you require was already done. Here is my existing config file:
```

# Smart Mon. Tools "smartd.conf" configuration file
# Home page is: http://smartmontools.sourceforge.net

# DEVICESCAN -d removable -n standby -m root -M exec /usr/share/smartmontools/smartd-runner
#
# Added by Spiro Angeli
DEVICESCAN -S on -o on -a -I 194 -m username@gmail.com -s (S/../.././02|L/../../6/03) -n standby,q

```


> The mdadm email is telling you the problem right in the message. You have redundant HOMEHOST lines in your mdadm.conf file. You need to only have only HOMEHOST entry in that file. 

Again, here is what I have.
```
DEVICE partitions
HOMEHOST ubuntu NAS Server
MAILADDR xxx.xxxx@gmail.com
ARRAY /dev/md0 metadata=1.2 UUID=b6afc2db:04e80120:5f5f83c7:5c81958f

```

Note: I xxx my email address for privacy.
Please let me know if is there something wrong I did

Thank you,
Spiro

---

### Post by rubylaser on 2013-01-31
> **SAngeli said:**
> 
```

DEVICESCAN -S on -o on -a -I 194 -m **user@gmail.com** -s (S/../.././02|L/../../6/03) -n standby,q

```
Note: I xxx my email address for privacy.


You'll want to remove your email from this line too:)  Have you waited a while and then checked if your disks are spinning down?  If they are not spinning down, have you verified that the disks support advanced power management?  If they don't, the -S flag won't spin them down.  You can try to set them up to spin down by hand like this.

```
hdparm -S 241 /dev/sdb
```

Your HOMEHOST line cannot contain spaces, or it interprets it as 3 different HOMEHOSTS.
```
HOMEHOST ubuntu NAS Server
```
could be modified to just
```
HOMEHOST NAS
```
or
```
HOMEHOST ubuntu-nas
```

---

### Post by SAngeli on 2013-01-31
> You'll want to remove your email from this line too
Could you please change the quoted email address to [email]username@gmail.com[/email] ?

Thank you a bunch for pointing this out. This was indeed important.

> Have you waited a while and then checked if your disks are spinning down?
Yes, I did a test and it does work as you properly say.
This is the message I get after they went to bed:
**Device is in STANDBY mode, exit(2)**
Thanks for checking on this too!

I know this is simple but can you please tell me how you obtained 242 for being exactely 60 minutes before it goes into standby? I know it is explained but I fail to identify the multiplier that would need for determining any kind of time.
Let's say I wish to how to find out for 2 hours or for 3 hours or for 3 1/2 hours.

Lastly, as for the HOMEHOST I percepted I was unable to add spaces but I was not sure.

Now, that the server is properly set, I need to focus on:
- email management
  [I]gmail and also through other providers as I wish to
  use the smtp for web development testing and for my
  mail needs[/I]
- disk performance
  see if it is properly set to get max performance
- webserver

For these topics I will start individual Threads.
See if you can keep an eye on them.

Thank you for your kind time and help.
Spiro

---

### Post by SAngeli on 2013-02-05
Hi,

after I completed mdadm install all is properly working (thanks  to forum for this), I realized that ext4 would not be the correct filesystem because I only use this array from Windows and I have few missing features, like icon customization for directories, no NTFS permission memorization, lost+found not usefull,...

So, after reading on the Internet I decided to move to ntfs (even if many users say it is perfeclty working and many others discourage from using it). It is the ntfs-3g

So, I first umount the array and than formatted "mkfs.ntfs /dev/md0" Considering that I have 1.5TB HD it took me almost 8 hours I assume to completely format the disks (I do not know if this is correct).
After turning my Windows PC on, I ssh to the server and I tried to mount the disk but it fails.

I get this error when I try to " mount -t ntfs-3g /dev/md0 /mnt/array_0". I also tried "mount -t ntfs /dev/md0 /mnt/array_0"

The error is:
```
NTFS signature is missing.
Failed to mount '/dev/md0': Argomento non valido
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

What do I have to do? What did I do wrong?

Here is some useful data if needed:

```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
81 testine, 63 settori/tracce, 574226 cilindri, totale 2930277168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x809d0a82

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  2930277167  1465137560   fd  Autorilevamento raid di Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
81 testine, 63 settori/tracce, 574226 cilindri, totale 2930277168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x125584aa

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2930277167  1465137560   fd  Autorilevamento raid di Linux

Disk /dev/md0: 1500.2 GB, 1500166488064 bytes
2 testine, 4 settori/tracce, 366251584 cilindri, totale 2930012672 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xb62432ae

Dispositivo Boot      Start         End      Blocks   Id  System

Disk /dev/mapper/ubuntu-root: 76.3 GB, 76332138496 bytes
255 testine, 63 settori/tracce, 9280 cilindri, totale 149086208 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00000000

Il disco /dev/mapper/ubuntu-root non contiene una tabella delle partizioni valida

Disco /dev/mapper/ubuntu-swap_1: 5364 MB, 5364514816 byte
255 testine, 63 settori/tracce, 652 cilindri, totale 10477568 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x00000000

Il disco /dev/mapper/ubuntu-swap_1 non contiene una tabella delle partizioni valida

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[1] sda1[0]
      1465006336 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

I also created a **[ubuntu forum thread]("ubuntuforums.org/showthread.php?p=12484777#post12484777")** nobody wants to anser and it is directly related to this issue.
Please see if you can also answer it.

Thank you,
Spiro

---

### Post by Cheesemill on 2013-02-05
If you are accessing the drive over the network then the filesystem you use has no impact at all, Windows won't know or care what the filesystem is.

In fact I would highly recommend not using NTFS on a server that only has Ubuntu installed. If you ever have problems that need fixing on an NTFS drive then the only way to fix them is from Windows. Any NTFS problems may be impossible to fix with your current setup.

---

### Post by SAngeli on 2013-02-05
moved the content of this specific tread to other thread

Thannk you,
Spiro

---

### Post by SAngeli on 2013-02-07
Hi,

suddently, hdparm seems not to be working anylonger as I noticed that my HD never go into sleepmode anylonger.
This is what I did so far:
1) I wanted to change filesystem frome ext4 to NTFS but it did fail.
2) I formatted again the array md0 to ext4. Now all functions properly.
3) I noticed that I had an excessive use of hte HD and determined that this was due to thef act that ext4 even if performed a quick format in the background it keeps formatting the disk (this is what I learned).
Now I do not see the excessive activity on the server but noticed that when I run smartctl --nocheck standby -i /dev/sdb the drive is always Active.

Is there anything that I did (between changing filesystem) affected hdparm from functioning?
How to find out if is there anything that prevents the 2 disks to spin down?

thank you,
Spiro

---

### Post by SAngeli on 2013-02-15
Hi,
I noticed that the server, after being with my two HD in spin down mode suddenly the drives started being active but I did not access them.
Is there a way to find out or trace who accessed them?
this to understand if something from the OS is interfering with current settings.

Thank you,
Spiro

---

