---
title: "What's wrong with my fstab?"
date: 2008-12-06
forum: Server Platforms
---

### Post by yldouright on 2008-12-06
I created two L5 arrays with mdadm and watched /proc/mdstat as they were successfully created but for some stupid reason, I can't mount them. I get the [mntent] error telling me my fstab is bad on line 9 and 10 but for the life of me, I don't know what is wrong with it and several hours of searches for answers yielded me nothing but a headache. Will someone look at my fstab below and tell me what is wrong with it?

# /etc/fstab: static file system information.
#
# <file system> 		<mount point>			<type>	<options>			<dump>	<pass>	proc	/proc	proc	defaults	0	0
# /dev/sda1	UUID=ebe544be-f872-40e2-a6c9-08308ff289a9 /	ext3    defaults,errors=remount-ro	0	1
# /dev/sda5	UUID=6669472b-2c0b-4066-a9da-1a6f77da3f58 none	swap    sw				0	0
# /dev/sdb6	UUID=8b35ef5a-40be-407a-b602-7aca66e81fcb none	swap    sw				0	0
/dev/scd0       /media/cdrom0   					udf,iso9660 user,noauto,exec	0       0
/dev/fd0        /media/floppy0  				auto    rw,user,noauto,exec		0       0
/dev/md0	UUID=466fa0a4:f6e34a24:157ad407:f60bdcfa /Hold	ext3	defaults			0	1	auto	defaults			0	3
/dev/md1	UUID=f04435c5:38a9a54d:157ad407:f60bdcfa /Data	ext3	defaults			0	1	auto	defaults			0	4

---

### Post by samosamo on 2008-12-06
Did you really spend that much time figuring it out?  Lets strip the line down to the bare minimum.  Here is a working /dev/md line from my fstab

```
/dev/md0	/srv		ext3	defaults,relatime	1 2
```

---

### Post by yldouright on 2008-12-07
Unfortunately, the answer is yes. Forgive me in advance for my apparent stupidity. Please don't think I'm looking a gift horse in the mouth but why will removing the UUID and array detail help mount this array? You will notice that the root file system entry has it and the reason for the array in the first place is to make it my root file system. I will not boot from it, so are you saying that only swap and boot partitions need UUID entries? I'd like to know what I am doing before I do it. I think I should add that the fstab above has apparently replaced my typographical tab entries with spaces so it does not align neatly. The table header is:
<file system> <mount type> <type> <options> <dump> <pass> proc /proc proc defaults 0 0
Does the second part of the header (ie: proc /proc proc defaults 0 0) belong on the next line?

---

### Post by taurus on 2008-12-07
You can either use the device name or the UUID but you cannot use both at the same time.

```

/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
```
or
```

UUID=ebe544be-f872-40e2-a6c9-08308ff289a9 / ext3 defaults,errors=remount-ro 0 1
```

---

### Post by yldouright on 2008-12-07
taurus
That doesn't appear to be so. Look on the first three lines and you will see that the mounted /(root) and swap volumes have both the dev and UUID noted on the same line and it works perfectly. What entries should be made under the dump and pass headers given the following:
md0 3-disks?
md1 4-disks?

---

### Post by fjgaude on 2008-12-07
I can't see where your fstab file comes from, but here is mine:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=7c4eedc7-fd4d-4ce4-95c8-a52ee7b951ae /  ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f83af29f-46af-48fd-b057-9addd8765e65 none  swap    sw              0       0
# /dev/sdb6
UUID=651a17c2-aafa-4364-b83b-e0395149261f none  swap    sw              0       0
/dev/scd1     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8         0       0
usbfs         /proc/bus/usb   usbfs   auto                              0       0
/dev/md32     /home/raid      ext3    defaults,noatime                  0       2
# /dev/sdb2
LABEL=backup  /media/backup   ext3    defaults                          0       2
```

My raid is simply /dev/md32, never a need for the UUID.

Also the UUIDs you are using are not the device ID but the ones used by mdadm to identify the arrays, not for mounting.

---

### Post by yldouright on 2008-12-07
fjgaude
I think I'm beginning to understand. The /dev/xxx is commented out so only the UUID is read. I thought the values belonging under the <dump> and <pass> headers were the number of disks being used in the array. In Raidtools, it was necessary to describe these in the raidtab file but this may not be necessary with mdadm. I'm going to review the mdadm documentation while I wait for additional replies here. Thanks to all those trying to help.

---

### Post by Krupski on 2008-12-07
> **yldouright said:**
> I created two L5 arrays with mdadm and watched /proc/mdstat as they were successfully created but for some stupid reason, I can't mount them. I get the [mntent] error telling me my fstab is bad on line 9 and 10 but for the life of me, I don't know what is wrong with it and several hours of searches for answers yielded me nothing but a headache. Will someone look at my fstab below and tell me what is wrong with it?

# /etc/fstab: static file system information.
#
# <file system> 		<mount point>			<type>	<options>			<dump>	<pass>	proc	/proc	proc	defaults	0	0
# /dev/sda1	UUID=ebe544be-f872-40e2-a6c9-08308ff289a9 /	ext3    defaults,errors=remount-ro	0	1
# /dev/sda5	UUID=6669472b-2c0b-4066-a9da-1a6f77da3f58 none	swap    sw				0	0
# /dev/sdb6	UUID=8b35ef5a-40be-407a-b602-7aca66e81fcb none	swap    sw				0	0
/dev/scd0       /media/cdrom0   					udf,iso9660 user,noauto,exec	0       0
/dev/fd0        /media/floppy0  				auto    rw,user,noauto,exec		0       0
/dev/md0	UUID=466fa0a4:f6e34a24:157ad407:f60bdcfa /Hold	ext3	defaults			0	1	auto	defaults			0	3
/dev/md1	UUID=f04435c5:38a9a54d:157ad407:f60bdcfa /Data	ext3	defaults			0	1	auto	defaults			0	4


Your fstab seems awfully complicated. And, what's up with the last field in your entries (the fsck code)?

It's supposed to be "0=no fsck", "1=root" and "2=all others".

Here's a sample fstab (from one of my machines):

```

# /etc/fstab: static file system information.
#
# <file system>                 <mount point>  <type>  <options>         <dump>   <fsck>

# proc
proc                            /proc          proc    defaults          0        0
# root
/dev/disk/by-label/linux-root   /              auto    defaults          0        1
# swap
/dev/disk/by-label/linux-swap   none           swap    swap              0        0
# raid storage
/dev/disk/by-label/linux-raid   /home/shared   auto    defaults          0        2

```

---

### Post by yldouright on 2008-12-07
Krupski
Thanks for the explanation on <dump> and <pass>. I have modded my fstab again and pasted it below:
```
# /etc/fstab: static file system information.
#
# <file system>					<mount point>	<type>	<options>			<dump>	<pass>
proc						/proc		proc	defaults			0	0
# /dev/sda1
UUID=ebe544be-f872-40e2-a6c9-08308ff289a9	/		ext3    defaults,errors=remount-ro	0	1
# /dev/sda5
UUID=6669472b-2c0b-4066-a9da-1a6f77da3f58 	none		swap    sw				0	0
# /dev/sdb6
UUID=8b35ef5a-40be-407a-b602-7aca66e81fcb 	none		swap    sw				0	0
/dev/scd0					/media/cdrom0   	udf,iso9660 user,noauto,exec	0       0
/dev/fd0					/media/floppy0  auto    rw,user,noauto,exec		0       0
/dev/md0					/Hold		auto	defaults			0	2
# UUID=466fa0a4:f6e34a24:157ad407:f60bdcfa 	
/dev/md1					/Data		auto	defaults			0	2
# UUID=f04435c5:38a9a54d:157ad407:f60bdcfa
```

My mdadm.conf remains empty. I did not change the last field <pass> in the header. That was the way it came with my 7.10 Ubuntu install. The changes I made should only be cosmetic. I replaced spaces with tabs in order to align the table better. /procstat says the array is active and running but when I try to mount, I get an error stating the mount point can't be found.

---

### Post by fjgaude on 2008-12-07
Have you made mountpoints for /Hold and /Data?

---

### Post by yldouright on 2008-12-07
fjgaude
Thanks for your attention but I don't understand your question. I thought entering the device in the fstab WAS how you create the mount point. Where else do I need to make an entry? What should be in mdadm.conf and mtab?

---

### Post by fjgaude on 2008-12-07
No, it takes more than that. The entry in the **fstab** file means that it will be mounted at the mountpoint, but if there is no such point then it is ignored.

To make a mountpoint you simply have to make a directory like so:

```
sudo mkdir /Hold
```

and the other:

```
sudo mkdir /Data
```

After that you can manually mount but if you reboot the arrays should automatically mount and you are good to go.

Let us know how it goes.

---

### Post by yldouright on 2008-12-08
fjgaude
I ran the two commands and the only result was two folders on my root directory. Disk Usage Analyzer confirms that no new media was mounted. Rebooting changes nothing. Do I need entries in the mdadm.conf or mtab?

---

### Post by fjgaude on 2008-12-08
Okay, can you run this command:

```
sudo mount -a
```


If you don't see the two arrays come up then something is still not right.

Show this:

```
df -h
```

Have you tried to manually mount the arrays?

---

### Post by yldouright on 2008-12-08
fjgaude
The command sudo mount -a tells me that /Data and /Hold do not exist and 
df -h confirms that only the /(root) partition is mounted. I tried manually mounting the partitions as per your previous directions with no luck.

---

### Post by yldouright on 2008-12-08
fjgaude and all others who have contributed here:
After I rebooted with the /Hold and /Data directories /dev/md1 did mount at /Data. Disk Usage Analyzer now shows the additional capacity. I stopped /dev/md0 in anticipation of my next step. Step one is complete, now the challenging part: Moving my root to the /dev/md0 partition. Does this warrant a new thread?

---

### Post by fjgaude on 2008-12-08
I think it would be a good idea to start a new thread...

---

### Post by samosamo on 2008-12-09
Forgive me but if you couldn't figure out fstab without a 2 page thread, you have miles to go before you can attempt to move your root partition to a raid device. keep reading.

---

### Post by Krupski on 2008-12-09
> **yldouright said:**
> Krupski
Thanks for the explanation on <dump> and <pass>. I have modded my fstab again and pasted it below:
```
# /etc/fstab: static file system information.
#
# <file system>					<mount point>	<type>	<options>			<dump>	<pass>
proc						/proc		proc	defaults			0	0
# /dev/sda1
UUID=ebe544be-f872-40e2-a6c9-08308ff289a9	/		ext3    defaults,errors=remount-ro	0	1
# /dev/sda5
UUID=6669472b-2c0b-4066-a9da-1a6f77da3f58 	none		swap    sw				0	0
# /dev/sdb6
UUID=8b35ef5a-40be-407a-b602-7aca66e81fcb 	none		swap    sw				0	0
/dev/scd0					/media/cdrom0   	udf,iso9660 user,noauto,exec	0       0
/dev/fd0					/media/floppy0  auto    rw,user,noauto,exec		0       0
/dev/md0					/Hold		auto	defaults			0	2
# UUID=466fa0a4:f6e34a24:157ad407:f60bdcfa 	
/dev/md1					/Data		auto	defaults			0	2
# UUID=f04435c5:38a9a54d:157ad407:f60bdcfa
```

My mdadm.conf remains empty. I did not change the last field <pass> in the header. That was the way it came with my 7.10 Ubuntu install. The changes I made should only be cosmetic. I replaced spaces with tabs in order to align the table better. /procstat says the array is active and running but when I try to mount, I get an error stating the mount point can't be found.

MDADM.CONF should not be empty. If it's missing somehow (and you do have MDADM installed) you can recreate it like this:

First, cut-n-paste the following into "/etc/mdadm/mdadm.conf":

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays


```

Then ADD the array definition to the file like this:

```

sudo mdadm --detail --scan [COLOR="Red"]**[SIZE="4"]>>[/SIZE]**[/COLOR] /etc/mdadm/mdadm.conf

```

NOTE in red the DOUBLE "greater-than" redirection sign.

The first operation will create the bulk of the mdadm.conf file, the last operation will ADD the array definition(s) of your MDADM RAID arrays.

After you reboot, your RAID arrays should be available (assuming you are mounting them with fstab).

Good luck

-- Roger

---

### Post by Krupski on 2008-12-10
> **yldouright said:**
> fjgaude
Thanks for your attention but I don't understand your question. I thought entering the device in the fstab WAS how you create the mount point. Where else do I need to make an entry? What should be in mdadm.conf and mtab?

OK look you need to understand the basic IDEA of what's going on.

Linux has "devices" such as "/dev/sda" and other various names. These devices can accept data or provide data.

For example, a hard drive might be named "/dev/sda" and you can both write to it and read from it.

Directory names in Linux are just that... directories. And, the cool thing is that you can "connect" a directory to a hard drive and access the hard drive by just reading and writing the directory.

The "connecting" process is called "mounting".

So, let's say you install a new bare hard drive and it's called "/dev/sda".

Let's say you want to partition the drive 1/2 and 1/2, so you use fdisk or cfdisk to do it.

Each partition needs a name (a way to reference it), so they are called "/dev/sda ONE" and /dev/sda TWO" (actually "/dev/sda1" and /dev/sda2").

Now, let's say you want to access those partitions. Make a directory for each of them... the name is up to you.

Let's say you make a directory called "/first-part" in the root directory and "/second-part" in the root directory.

At this point, both those directories are just empty, worthless directories. So now let's CONNECT THEM to the hard drive:

```

mount /dev/sda1 /first-part
mount /dev/sda2 /second-part

```

NOW when you look at those directories, you will see the contents of the hard drive. If you store files in the directories, you are actually storing them on /dev/sda1 or /dev/sda2 (depending on which directory you access).

Now, reboot. DARN the connections are gone. You have to type "mount" again. Bummer.

Or... better to AUTO mount them, put the desired "connections" into fstab, like this:

```

/dev/sda1   /first-part     auto  defaults  0  2
/dev/sda2   /second-part    auto  defaults  0  2

```

What this means? In order, the entries mean:

(1) The device (drive) name, (2) Where you want to connect them to, (3) Let Linux automatically figure out if the drives are EXT3 or NTFS or whatever, (4) Setup default read, write and execute attributes, (5) Don't "dump" the drive contents if there's a crash and (6) Run FSCK (File System Check) on these drives at bootup to be sure they're not corrupted.


Got it now?

-- Roger

---

### Post by yldouright on 2008-12-16
Krupski
I'm fairly new to Linux so I appreciate the hand holding. I am beginning to understand that all the mount points 'tuck under' the root filesystem but they can be anywhere, even in cyberspace, correct? Now that I was able to mount the arrays and rebooting them with the fstab entries remounts them without any additional activity, why do I need to mess with mdadm.conf? I am posting the working fstab below:```
# /etc/fstab: static file system information.
#
# <file system>					<mount point>	<type>	<options>			<dump>	<pass>
proc						/proc		proc	defaults			0	0
# /dev/sda1
UUID=ebe544be-f872-40e2-a6c9-08308ff289a9	/		ext3    defaults,errors=remount-ro	0	1
# /dev/sda5
UUID=6669472b-2c0b-4066-a9da-1a6f77da3f58 	none		swap    sw				0	0
# /dev/sdb6
UUID=8b35ef5a-40be-407a-b602-7aca66e81fcb 	none		swap    sw				0	0
/dev/scd0					/media/cdrom0   	udf,iso9660 user,noauto,exec	0       0
/dev/fd0					/media/floppy0  auto    rw,user,noauto,exec		0       0
/dev/md0					/Hold		auto	defaults			0	2
# UUID=466fa0a4:f6e34a24:157ad407:f60bdcfa 	
/dev/md1					/Data		auto	defaults			0	2
# UUID=f04435c5:38a9a54d:157ad407:f60bdcfa 	
```Upon review, mdadm.conf is empty but mtab has entries and I will post them if requested.

samosamo
You are absolutely right about me having alot to learn but I am still in the experimental stage with Linux. My main boxes are still Windows so this is the time to be wreckless.

---

### Post by yldouright on 2008-12-17
Here is my mtab:```
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-16-generic/volatile tmpfs rw 0 0
/dev/md1 /Data ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
```In my research, I have the impression that all I'm required to do in order to move my /(root) to a new partition is:
1. boot from a live cd
2. move the entire installation to the new partition
3. make a /boot partition at the beginning of your disk (mirrored after)
4. edit fstab and my boot loader configuration to reflect the new location.

Is this an oversimplication of what is required? Here are some of the things which I believe may cause snags:
Do I need to stop the current arrays or will booting from a live cd ignore the arrays until I mount them?
Do I need to also edit the mtab? Any other files? How do I edit the GRUB? Will booting from a live cd enable me to edit those files?

---

### Post by fjgaude on 2008-12-17
AFAIK, you never have to edit an mtab file.

If your array is auto assembling, mounting at boot time you should have a mdadm.conf file in /etc/mdadm/. It is good to know how it looks to compare with what has been booted as an array, compared to:

```
sudo mdadm -D /dev/md[n]
```

Are you wanting to move the /root partition onto the raid5 array or onto a raid1?

If the latter, then this might be useful:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

Show us what

```
sudo mdadm -D /dev/md0
```

and

```
Sufo mdadm -D /dev/md1
```

look like, please.

---

### Post by yldouright on 2008-12-17
fjgaude
When I looked in the /etc/mdadm directory, I found the mdadm.conf file. I must have created a new document named mdadm.conf when I ran "sudo gedit /etc/mdadm.conf". I guess calling gedit to edit a file in the wrong location or with the wrong name will create THAT filename in THAT location. I have since deleted that empty file. This is a valuable lesson for me and I appreciate you taking the time to name the exact location of mdadm.conf. Without that information, I would've never known it was there. Here is the requested command result for md1:```
/dev/md1:
        Version : 00.90.03
  Creation Time : Thu Dec  4 10:24:57 2008
     Raid Level : raid5
     Array Size : 203310144 (193.89 GiB 208.19 GB)
  Used Dev Size : 67770048 (64.63 GiB 69.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Dec 17 09:28:14 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f04435c5:38a9a54d:157ad407:f60bdcfa (local to host p2bds-ubuntu)
         Events : 0.12

    Number   Major   Minor   RaidDevice State
       0       8        6        0      active sync   /dev/sda6
       1       8       23        1      active sync   /dev/sdb7
       2       8       38        2      active sync   /dev/sdc6
       3       8       54        3      active sync   /dev/sdd6

```I will be breaking md0 in order to reconfigure my installation. I am aiming for the following partition scheme:
/dev/sda5 /boot (64MB at the beginning of the media on the drive)
/dev/sdb5 /boot (64MB mirror at the beginning of the media on the drive)
/dev/sda6 swap (384MB partition part of a raid 5 swap) md0
/dev/sdb6 swap (384MB partition part of a raid 5 swap) md0
/dev/sdc5 swap (384MB partition part of a raid 5 swap) md0
/dev/sdd5 swap (384MB partition part of a raid 5 swap) md0
/dev/sda7 / (4GB partition part of a raid 5) md2
/dev/sdb7 / (4GB partition part of a raid 5) md2
/dev/sdc6 / (4GB partition part of a raid 5) md2
/dev/sdd6 / (4GB partition part of a raid 5) md2
/dev/sda7 /home (remaining space part of raid 5) md1
/dev/sdb7 /home (remaining space part of raid 5) md1
/dev/sdc6 /home (remaining space part of raid 5) md1
/dev/sdd7 /home (remaining space part of raid 5) md1

Does anyone see any potential problems with this configuration? Am I required to make a primary partition or have an MBR if I am solely using linux on this box? I remember reading that LILO could be placed in the first 512MB of the device and still boot without an MBR, did I read this wrong?

---

### Post by fjgaude on 2008-12-17
The /dev/md1 looks fine as a raid5 array.

Are trying to make this into a raid1:

/dev/sda5 /boot (64MB at the beginning of the media on the drive)
/dev/sdb5 /boot (64MB mirror at the beginning of the media on the drive)

You know there is no way to boot up from a raid5 array? Likely you are thinking that a raid1 can be made from the same drives as the raid5?

To boot you will have to have grub or something like that to point to the start-up menu and the kernel. To assemble an array the kernel has to be loaded.

Have you read what it takes to have a bootable raid1 array? If not, here's a good link:

[http://radu.rendec.ines.ro/howto/raid1.html](http://radu.rendec.ines.ro/howto/raid1.html)

Let me know what your thinking is. I'm not sure you can do what I think you are trying to do, in planning anyway.

---

### Post by yldouright on 2008-12-17
fjgaude
Yes, I am aware that you cannot boot from RAID 5 and that is why I made the (mirror) on the /boot partition. As I understand it, the /(root) filesystem can be anywhere so long as the /boot partition is located early in the drive. Is this incorrect? What makes putting a level 5 array and a mirror set across the same media a problem?

---

### Post by yldouright on 2008-12-17
Oops! I just looked at my partitioning scheme and noticed some errors. Here is the corrected version:
/dev/sda5 /boot (64MB at the beginning of the media on the drive)
/dev/sdb5 /boot (64MB mirror at the beginning of the media on the drive)
/dev/sda6 swap (384MB partition part of a raid 5 swap) md0
/dev/sdb6 swap (384MB partition part of a raid 5 swap) md0
/dev/sdc5 swap (384MB partition part of a raid 5 swap) md0
/dev/sdd5 swap (384MB partition part of a raid 5 swap) md0
/dev/sda7 / (4GB partition part of a raid 5) md2
/dev/sdb7 / (4GB partition part of a raid 5) md2
/dev/sdc6 / (4GB partition part of a raid 5) md2
/dev/sdd6 / (4GB partition part of a raid 5) md2
/dev/sda8 /home (remaining space part of raid 5) md1
/dev/sdb8 /home (remaining space part of raid 5) md1
/dev/sdc7 /home (remaining space part of raid 5) md1
/dev/sdd7 /home (remaining space part of raid 5) md1
Now the partitions are located at the same cylinders on each drive and none of the arrays have partition conflicts.

---

### Post by fjgaude on 2008-12-18
Well, what's wrong with giving it a try and see if it all works?

Make sure you have **grub** on both of the raid1 drives, that way you will be able to boot if one drive fails. And make sure the grub menu.lst file has those drives in the first and second options so you can try booting from either drive.

Create the raid1 first, just to make things easier, knowing that the prime aspect is working, and then you can use **mdadm** from the raid1 filesystem to create the raid5 arrays.

It makes no difference where on the drive the /boot section is, as long as the grub sees the menu.lst file.

Are you going to do the first array from a LiveCD?

---

### Post by yldouright on 2008-12-18
fjgaude
I am taking your advice from your earlier post to start another thread. My fstab issue was resolved and what I plan to do next is off topic so: [[COLOR="Blue"]Here [/COLOR]]("http://ubuntuforums.org/showthread.php?p=6393286#post6393286")is where you will find the continuation of this issue.

---

### Post by fjgaude on 2008-12-18
Wonderful, let's see if you get any takers!

---

