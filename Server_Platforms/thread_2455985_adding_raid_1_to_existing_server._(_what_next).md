---
title: "adding raid 1 to existing server. ( what next)"
date: 2021-01-01
forum: Server Platforms
---

### Post by tross9 on 2021-01-01
I'm adding a raid 1 to my existing server, i'm going to be using the current sdb as a backup drive and want to have raid 1 on it.
--
current server info:
    sda - ( boot drive ) -- no raid
               ata disk
               160 MB
               Partioned partioned : dos
    sdb - ( share drive) -- no raid -- samba for window access  -- to allow backup of windows system files to sdb drive. ( docs, pics, etc..)
               ata disk
               1tb
               Partioned partioned : dos
--
where i am with the server:  
  added second 1tb drive (sdc) as is and did not do anything else to it.
   so drives are now, lshw -- sees all three drive ( as listed )

     sda - ( boot drive ) -- no raid
               ata disk
               160 MB
               Partioned partioned : dos
    sdb - ( share drive) -- no raid -- samba for window access
               ata disk
               1tb
               Partioned partioned : dos

    sdc - (was from windows 7 system -- still format as a windows drive --  still has Window 7 OS and other data --  I do not need) 
               ata disk
               1tb
               Partioned partioned : dos
  
--
status so far:
  
   Tested sdc by -- mkdir /media/drive and mounting /dev/sdc  -- got msgs (wrong FS type bad option ....) 
    but cd to drive and
        df command did show  two lines 
         root root . 
         root root ..    

--
question :
 
  1)  do I need to format sdc? or will the Madam command take care of it? ( i assume that sdc will be written over, and to the same format as sdb, yes? no?)
  2)  I assume all I need to run is the following (only?)
        sudo madam --create --verbose /dev/md0 --force --level=1 --raid-device=1 /dev/sdb     ( some examples show /dev/sdb1 do i need the number?)
        sudo madam --grow /dev/md0 --raid-device=2 --add /dev/sdc ( again do i need to add a number)

   i assume the --grow will overwrite the format on the sdc drive to match sdb.

  3)  do i need to change the auto mount param, ( it is currently mounting sdb as /media/drivesdb on boot up) 
        or do i need to tell the system to mount the raid ( edit fstab to add /media/drivesdb  /dev/md0 or edit the exist entry, or do nothing)



Tia 
Tim

---

### Post by darkod on 2021-01-01
Hold on. You have couple of big mistakes...

Most important, if sdb curently has the data you need, you don't start by creating the array with sdb. You do it with the new disk, sdc.

And yes, it is better to have a number, like /dev/sdc1, because that means partition #1. It is better to use partitions for mdadm even though it can work with disk designator like /dev/sdc.

Also, you will create the array as 2 disk raid1 array, with one disk missing. That allows you to simplify things and you avoid doing grow later.

So your first step is to create new partition table on sdc to remove the current ntfs partitions. You said you DON'T need the data, right??? I don't know which tool you prefer, I myself prefer parted in the command line. And even though it is not necessary for a disk of 1TB, it is preferred to use gpt table, no msdos.

It is also best to check total number of MiB that sdb and sdc have. The disks are 1TB but the exact number of MiB might differ slightly. This is why I create the partition to end around 15-20MiB before the end of the disk. That way it allows new disk in the future to be able to have a partition of the same size.

You can check total number of MiB and other basic data of each disk with:
```
sudo parted /dev/sdb unit MiB print
sudo parted /dev/sdc unit MiB print
```

---

### Post by SeijiSensei on 2021-01-02
I would create a single partition on each of sdb and sdc. I use fdisk for this task so I can mark the partitions as type "fd" which is the code for RAID component.

This will obviously destroy all the data on both drives.

Next you would create a RAID1 array using mdadm (not "madam"):
```

sudo mdadm /dev/md0 --create --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```
Then you can format the array with whatever filesystem you need. For a standard ext4 Linux filesystem, you'd use
```
sudo mkfs -t ext4 /dev/md0
```
Then specify a mount point in the filesystem and add the array to /etc/fstab.  I'd use "sudo blkdid" to find its "UUID", then use the UUID in /etc/fstab.

---

### Post by tross9 on 2021-01-02
[COLOR=#DD4814]Thanks  [darkod]("https://ubuntuforums.org/member.php?u=946366")[/COLOR]  And [SeijiSensei]("https://ubuntuforums.org/member.php?u=698195")

[FONT=Ubuntubeta]    i did not mention that I backup the SDB drive and if I loose the data on SDB, i have it else where.[/FONT]

[FONT=Ubuntubeta]  i'll be using both of your suggestions to create my raid.  i hope to have it created soon.[/FONT]

[FONT=Ubuntubeta]again thanks.    [/FONT]


[COLOR=#000000]Tim[/COLOR][COLOR=#dd4814][/COLOR]

---

### Post by rsteinmetz70112 on 2021-01-03
Assuming you get the partition sdc1 right you can make it a 2 disk raid 1 array with a missing disk, copy everything on to sdc1 then repartition sdb and add sdb1 to the array you set up.

---

### Post by tross9 on 2021-01-07
sdc1 is a 1TB drive. ( so is sdb1)

Question,  

when running fdisk /dev/sdc1 
I enter n them  p
 the following is displayed

 
 device                                   size               type ( i think it said type)
 /dev/sdc1p1                         835.5g            qnx4. ... 
 /dev/sdc1p2                         259.6g            unknown
 /dev/sdc1p3                         259.5g            unknown
 /dev/sdc1p4                          26.9m            speedstor

I assume that these are the window partition, that were leftover,   and the Px are the partition number
  do I want to have one partition for my raid or will Mdadm fix that? ( or do I delete the partitions first then  create a new partition on sdc1) 
    also do I need repartition sdb1? ( seeing that it is ext4 already)

fdisk -l 
  shows 
sdb1 as 1 device  931.5 in size  and  Linux lvm
sdc1 as 1 device  931.5 in size  and  hpfs/ntfs/exfat  ( I assume I need to have it changed to Linux lvm)

Thank you

---

### Post by darkod on 2021-01-07
You need to repartition any disk that was used before. You want it to be with new clean partition table, like new. So that means you need to repartition both sdb and sdc.

You might have sdb1 as ext4 right now, but with mdadm the sdb1 does not carry any filesystem. The filesystem will be on the raid array device, like /dev/md0.

You can use fdisk or parted, which ever you prefer. But start by creating new empty gpt partition table. Of course, this will destroy all data on both disks but you said you are OK restoring that from backups.

I still think best approach is to create the array with sdc1 and one member missing, copy the data from current sdb1, then repartition sdb to add the new sdb1 to the array. From internal to internal HDD it would copy the data much faster.

If your backup is on external USB for example, copying back from it would take much longer than from internal HDD.

But the choice how you handle this operation is on you.

---

### Post by tross9 on 2021-01-08
ok, 
when I tried to create a new [COLOR=#000000]partition on /dev/sdc1[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000][/COLOR]fdisk displayed the following,  


[COLOR=#000000]device size type ( i think it said type)[/COLOR]
[COLOR=#000000]/dev/sdc1p1 835.5g qnx4. ...[/COLOR]
[COLOR=#000000]/dev/sdc1p2 259.6g unknown[/COLOR]
[COLOR=#000000]/dev/sdc1p3 259.5g unknown[/COLOR]
[COLOR=#000000]/dev/sdc1p4 26.9m speedstor

[/COLOR]so do I delete the existing partition first? then create a new single partition? 

sorry about not knowing the steps to take, still new to Ubuntu.

---

### Post by TheFu on 2021-01-08
I saw a number of questions asked above which still haven't been answered. Commands run.

Tip:  If you'd like good help, answer the questions. Run the commands.  Post the output.

Tip: Don't interpret the output.  Just post it WITH THE EXACT COMMAND RUN.

Tip: whenever posting commands and output, use forum code-tags so it looks like it did in the terminal.  This is a simple copy/paste thing. Nobody is asking for any extra work, no font changes, nothing like that. [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

Please.

---

### Post by SeijiSensei on 2021-01-08
> **tross9 said:**
> ok, 
when I tried to create a new [COLOR=#000000]partition on /dev/sdc1[/COLOR]
[COLOR=#000000][/COLOR]
[COLOR=#000000][/COLOR]fdisk displayed the following,  

[COLOR=#000000]device size type ( i think it said type)[/COLOR]
[COLOR=#000000]/dev/sdc1p1 835.5g qnx4. ...[/COLOR]
[COLOR=#000000]/dev/sdc1p2 259.6g unknown[/COLOR]
[COLOR=#000000]/dev/sdc1p3 259.5g unknown[/COLOR]
/dev/sdc1p4 26.9m speedstor

In fdisk, "d(elete)" all the partitions, then use "n(ew)" to create a new partition that spans the entire disk. Use the "t(ype)" command to mark it as type "fd".  Then "w(rite)" the results to the drive. Do the same to the other disk to be used in the array. Then run mdadm --create to bind the partitions together.

---

### Post by tross9 on 2021-01-08
ok, deleted the partitions, created new single partition , the T FD changes from Linux to fat12 , i assume that is what I need for Samba?
   again thanks for your time and patience

---

### Post by darkod on 2021-01-08
fat12 sounds like filesystem to me, and the partitions for mdadm should NOT have a filesystem on them. I might be wrong what it means though, I stopped using fdisk some years ago.

Part of the reasons I prefer parted is precisely because mkpart creates a partition without assigning it any type or filesystem. Clean and easy. After that adding the raid flag is very easy too.

To be able to receive more feedback from the others following this thread please post the output of:
```
sudo fdisk -l
sudo parted -l
```

---

### Post by rsteinmetz70112 on 2021-01-08
I don't understand your comment. Samba will work with almost any normal partition type.

---

### Post by tross9 on 2021-01-08
[[COLOR=#000000]darkod[/COLOR]]("https://ubuntuforums.org/member.php?u=946366")[COLOR=#000000] [/COLOR]
ok, it seem that using fdisk , the drive is either going to be fat12 or ntfs , where as SDB1 is ext4, I did see someone mentioning that I should create it as ext4.  i'll look for that post or try parted, or keep trying fdisk.


[COLOR=#000000]Ago[/COLOR]
[COLOR=#000000]rsteinmetz70112
  I just want to be sure that I'll be able to access this Raid from windows, ( i intend to use it as a backup/file server for my windows machines) and want to be sure that I'll be able to do that without going thru reformatting because I have the wrong filetype.

  [/COLOR]

---

### Post by SeijiSensei on 2021-01-08
Sounds like you might be confusing partition types and filesystems.

Open one of RAID the drives with fdisk, then use "l" to see a list of types.  FAT12 is type 1.  Type "fd" is "Linux raid auto".  Now enter the command "t" and the code "fd" when prompted.  Then use "w" to save the changes to the partition table.  Repeat with the other drive.

Once you've built an array you can put any type of file system on it. In my example [above](https://ubuntuforums.org/showthread.php?t=2455985&p=14011286&viewfull=1#post14011286), I use mkfs to put an ext4 filesystem on the array called /dev/md0.

The mdadm kernel code will automatically recognize partitions marked "fd" as RAID members during boot.

---

### Post by SeijiSensei on 2021-01-08
Sounds like you might be confusing partition types and filesystems.

Open one of RAID drives with fdisk, then use "l" to see a list of types.  FAT12 is type 1.  Type "fd" is "Linux raid auto".  Now enter the command "t" and the code "fd" when prompted.  Then use "w" to save the changes to the partition table.

Once you've built an array you can put any type of file system on it. In my example [above](https://ubuntuforums.org/showthread.php?t=2455985&p=14011286&viewfull=1#post14011286), I use mkfs to put an ext4 filesystem on the array called /dev/md0.

mdadm will automatically recognize partitions marked "fd" as RAID members during boot.

>  I just want to be sure that I'll be able to access this Raid from windows, ( i intend to use it as a backup/file server for my windows machines) and want to be sure that I'll be able to do that without going thru reformatting because I have the wrong filetype.

Access it from Windows on the same machine via a dual-boot arrangement?  Or access it from Windows machines over the network?  

For the first of these, you'll need to put an NTFS filesystem on the array like this:
```
sudo mkfs -t ntfs /dev/md0
```
It's possible to install third-party software on Windows to access ext[234] filesystems, but it's not the recommended approach. Format the array with NTFS and Windows will be happy.

If you mean access the files on the array over the network by, say, mapping a network drive in Windows, then you will be exporting the files [using the Samba application]("https://ubuntu.com/tutorials/install-and-configure-samba#1-overview").  In this case you should format the array with ext4 which Samba expects to find.

---

### Post by TheFu on 2021-01-08
> **rsteinmetz70112 said:**
> I don't understand your comment. Samba will work with almost any normal partition type.

+1.  But when Linux is the host for the Samba shared storage, it is best to stick with native Linux file systems like ext4 and definitely avoid FAT-whatever or NTFS.  Those don't support native Unix permissions and drastically limit local control of the storage on Linux systems.

FAT12 is the FAT version from before FAT32. There is almost zero use for it today.

fdisk has a field for each partition that just marks the file system type. It is separate from the actual file system. There is a RAID type ... let me check the number ... hummm. Interesting.  On 16.04, fdisk and parted are showing either Linux or msftdata (Microsoft basic data) or nothing at all for my mdadm RAID devices.

parted shows this for the md arrays:

```
# parted  -l /dev/md1
Model: Linux Software RAID Array (md)
Disk /dev/md1: 1990GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  1990GB  1990GB  ext4

```
which is to be expected.  parted -l shows all the devices, ignoring my input of a specific device.

```
# fdisk  -l /dev/md1
Disk /dev/md1: 1.8 TiB, 1989643075584 bytes, 3886021632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 2560 bytes
```

That's the entire fdisk output for the md1 device.

gparted shows all the RAID devices (partitions) as "linux-raid" and knows RAID device it is included in, but it lies about the "Mount Point".  It says the mount point is /dev/md1, which is wrong. That's the mdadm device.  It is actually mounted to ....
```
# df -Th
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdc1      ext4   20G  8.9G  9.3G  49% /
/dev/sdc2      ext4  186G  120G   57G  68% /Data/1TB
/dev/sdc5      ext4  151G  107G   36G  75% /export
/dev/md2       ext4  1.3T  1.2T   67G  95% /Data/r2
**/dev/md1       ext4  1.8T  1.7T   19G  99% /raid**
/dev/sda1      ext4  1.4T  1.3T   26G  99% /Data/1.5T
```

```
# more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdg2[1] sdf2[0]
      1338985536 blocks [2/2] [UU]
      
md1 : active raid1 sdd3[2] sde2[3]
      1943010816 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```
shows that md1 is made from /dev/sdd3 and /dev/sde2 and that all is fine with it.  That file is handy.  Don't modify anything in /proc, just view it.

---

### Post by tross9 on 2021-01-08
ok, here the issue, I cheated , I entered t fd on one line, fdisk ignored the fd
   when I entered t pressed the return key then type FD   ' changed from Linux to Linux raid auto...'

parted -l    still  still shows that /dev/sdc1 is type as ntfs but i assume that mkfs will fix that.

i think i ok for now, 
   i'll see what issues i run into when I run mdadm

---

### Post by TheFu on 2021-01-08
Booted Windows can read an mdadm created arrays?  Is that new?  When did Windows start honoring Linux storage?

---

### Post by darkod on 2021-01-09
> parted -l still still shows that /dev/sdc1 is type as ntfs but i assume that mkfs will fix that.

No, mkfs will not fix that. You are mixing up things. In mdadm raid the filesystem you will create goes on top of the raid array device, it is not in the partitions like when you use simple HDD partitions.

If you still have ntfs partitions that means you didn't delete them. Few of us already said few times to remove all partitions and create new ones. Please focus and follow the instructions.

You need to delete all partitions in sdc or simply create new blank partition table. A new partition table will delete all existing partitions at once without needing to go one by one.

Basically do it any way you want just get rid of the old ntfs partition from when you were using the disk in a windows machine.

PS. In post #12 I asked you to post the currect status of the disk partitions so that we wouldn't need to guess things. But you still avoid to provide it.

As for accessing the storage from windows, there are few different ways. Depending which Windows version we are talking about, the recent versions even have NFS client as windows feature. That allows you to export storage from linux server as nfs and use it on windows too. You don't even have to use Samba shares which can be more complex to set up compared to nfs export.

---

### Post by tross9 on 2021-01-09
system info if needed  -- 16.04.7 lts

1 I am deleting the partition before creating a new one
step   r) = system prompt ---       #) = my keystrokes
   sudo fdisk /dev/sdc1
     1) d enter
           r)   partition  deleted  
     2) n enter
           r) - p or e
     3) p enter
           r) - partition number
     3) 1 enter
           r) - starting sector - default 2048
     4) enter
           r) - ending sector - default 1953503936
     5) enter
           r) - partition created of type Linux size 931.5
     6) t enter
           r) - partition 1 selected  -- enter partition type
     7) fd enter
           r) - partition changed from Linux to Linux raid autodetect
     8) w enter
           r) - partition table has been altered - system using existing table till reboot
     9) sudo shutdown -r now
 
     i do not have direct access to the server so was not able to post the DF output. I just remembered  the >> option.

     I attached the file , not sure how to attach code like you have done.
         the (df , fdisk, etc..) commands were ran after the above steps and after the reboot.  which i've repeated several times so either i'm missing a step or maybe I should be using parted? 

         fyi -the first time i used fdisk on /dev/sdc1 It had 4 partition , so I was able to delete them and create 1 partition, and It is still flagged as a boot drive which I don't need on this.

---

### Post by TheFu on 2021-01-09
/dev/sdc1 is almost certainly wrong.
 /dev/sdc is the whole disk device.
 /dev/sdc1  the first partition.  

See why we keep being confused and want to see the actual parted/fdisk commands?

```
Disk **/dev/sdb**: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcbaa9abf

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953525167 1953523120 931.5G 8e **Linux LVM**

Disk **/dev/sdc**: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6faf6faf

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1  *       63 1953503999 1953503937 931.5G  7 HPFS/NTFS/exFAT
```
Ok, 1TB.

I see you use LVM.  Will you be using LVM on the array?  If so, LVM can be used to create RAID setups w/ mirror or stripes.  Check out **lvconvert**. No need for **mdadm** at all when lvm is part of it.

Cough ... sdb is all LVM.  If you don't want to change that, we need to see
```
sudo pvs
sudo vgs
sudo lvs
```

[https://linoxide.com/linux-how-to/identify-linux-lvm-mirror/](https://linoxide.com/linux-how-to/identify-linux-lvm-mirror/) has a how-to guide, but they used a single disk w/ 2 partitions, instead of 2 disks each with a partition to become the PVs.

---

### Post by SeijiSensei on 2021-01-09
fdisk is a utility that is designed to work on entire devices.  In Linux, entire disks are designated with names like /dev/sdc. If that disk has partitions, they are designated /dev/sdc1, /dev/sdc2, etc. So you need to run the command "sudo fdisk /dev/sdc" to delete the existing partitions and create new ones.

---

### Post by tross9 on 2021-01-09
attached updated parted and fdisk output [B]

the Fu   [/B]

    I have not touched SDB yet, i was mainly trying to get SDC created,
      as to lvm , not sure, i was going to repeat the steps from SDC on SDB.

           all I really want to do, is use the raid as a file server, I want to use it to backup all my files, pictures, etc .. on it and be safer than being on a single drive and just want to do it right the first time. 


( it took me several weeks to set up the one drive and get my windows machine to connect. ( permission, auto mounting the drive, etc... and other things i need to figure out)


**[COLOR=#000000]SeijiSensei[/COLOR]**

   thanks , it looks better ( no boot flag, no ntfs)

**everyone **, thanks you your patience and understanding.
      my backgound,
        is 99% MS dos and window , started with dos 1.0, back when there was IBM dos , compaq dos , wyse dos, and yes MS dos ) 
         for anyone not old enough to have use a pc before they had hard drives and only had floppy drives, every computer manufacture had their own version of dos back then.

         so i need to unlearn the window gui and get back to command prompt.

---

### Post by tross9 on 2021-01-10
ok, 
I fdsik sdb
   ran mdadm
  mkfs -t /dev/md0
  nano /etc/fstab   ( /dev/md0    /media/drivesdb1 ext4 defaults 0  0)

 now it fails to boot due to dependencies for  /media/drivesdb1

  when i tried to run    sudo blkdid        "command not found"


the server does boot to emergency mode -- was able to comment out the fstab line and rebooted normally without the raid drives

what did i miss?

---

### Post by SeijiSensei on 2021-01-10
You need to be a lot more careful when typing. It's not "blkdid" but "blkid". Also your /etc/fstab is missing the filesystem and options fields. Here's mine for a RAID array using its UUID:
```
UUID=ff2902fb-c4bc-41a4-bd94-72bedf5eec32   /media/raid   ext4   defaults 0 0
```

---

### Post by tross9 on 2021-01-10
i was typing the command that was in post #3


   added line in fstab
UUID=9f8bf34d-cec9-426b-a998-27500f71e4cd     /media/raid ext4 defaults 0 0

   still boots into emergency mode

**update   2:27 est**

   /dev/md0 does not exist  but /dev/md127 does. 
    changing fstab to

    /dev/md127 /media/raid .......    

allows me to boot and df -TH sees /dev/md127 mounted as /media/raid
   parted show md127 as a software raid

 i'm going to try using the uuid of md127 and see what that does

---

### Post by SeijiSensei on 2021-01-10
Is that the UUID for your array found using "sudo blkid"?

I use /media/raid as the the mount point for my array. Did you create an empty directory with the same name at the same location? From the commands you gave above, it looks like you tried to mount your array to  /media/drivesdb1.

Don't just copy and paste from suggestions. You need to view them as examples and read and understand the syntax involved. Then modify them to fit your needs.

If after fixing the fstab entry you still end up in emergency mode, then try this.  Remove or comment out with a hash mark ("#") the line that mounts the array.  Let Ubuntu boot up.  Then open a terminal and type
```
mount -v /dev/md0 /mount/point
```
where /mount/point is the location to which you want the array mounted ("/media/raid" in my case or perhaps "/media/drivesdb1" using your earlier posting).  If that doesn't work, copy and paste the results from the terminal here inside of [noparse]```

```[/noparse] tags.

If you're still having problems, run the command "sudo mdadm --detail /dev/md0" and post those results here.

I'm assuming that when you created the array you named it /dev/md0.  If it is named something else, like /dev/md127, then replace /dev/md0 with /dev/md127 in the commands above.

---

### Post by TheFu on 2021-01-10
> **tross9 said:**
> i 
allows me to boot and df -TH sees /dev/md127 mounted as /media/raid
 

The correct command is:
```
df -Th
```
Please post the output for the md* line from that cmd.  Note the case for the options. It matters.

Post #3 mkfs had some options that seem to have been forgotten in later posts and perhaps when entering the commands. We can't tell.

If attention to details is a problem, linux will always be hard.

---

### Post by tross9 on 2021-01-10
/dev/md0 does not exist ( df , fdisk or parted) . I'm not sure if it did exist, I told mdadm to create /dev/md0 

yes, I did try to mount to drivesdb1 when i could not get /media/raid to work
yes, there is a raid folder in /media, i don't recall manually creating it, but it is there
  fyi --    when i LL the raid folder , unmounted it only shows . and ..
                       when mounted it shows . and .. and "lost and found'  , i assume that means it ok.

  ( drivesdb1 and drivesdc1 also exist i that folder, i'll be removing them later)

   blkid only see the raid as md127 and using the UUID of md127 in fstab works , so either entry of /dev/md127 or uuid=59...   fstab will mount the drive. 

i would attach the output (df , parted, etc ..) but I no longer can access the drives from my windows machine,
   and i never did setup permission for putty to the server. so i have to write down what i see the retype it here.

getting there,
 I need to work with samba and or permission on the raid folder ,  can see the share folder from windows system but no permission  (i think i need to chown the group I use  instead of root root,  i'm not granting permission to everyone ( using 770 mostly)
i assume that I could mount a flashdrive and save the output to it but not sure how.

---

### Post by tross9 on 2021-01-10
in my notes i've entered       [COLOR=#000000]mkfs -t **ext4 **/dev/md0
   i do seem to recall that /dev/md0 was listed during one of the disk info displays  

  I should have reported exactly what I did, sorry.


 [/COLOR]

---

### Post by tross9 on 2021-01-10
the line from df -Th  is

 /dev/md127    917G 72M 870G 1% /media/raid

---

### Post by tross9 on 2021-01-10
output from df parted and fdisk

---

### Post by TheFu on 2021-01-10
> **tross9 said:**
> the line from df -Th  is

 /dev/md127    917G 72M 870G 1% /media/raid


There isn't a file system listed.  Appears that the mkfs didn't work. I'd guess you missed the **-t ext4** option?
```
$ \df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/md2       **ext4**      1.3T  1.2T   67G  95% /Data/r2
/dev/md1       **ext4**      1.8T  1.7T   18G 100% /raid

```
Something like this is what I expected.  That's on my RAIDs. Without a file system, nothing good can happen ... er ... unless you want to put LVM onto it, but if that was the case I'd have skipped using mdadm at all and let LVM handle the RAID setup instead.

---

### Post by tross9 on 2021-01-10
ext4 was left out  when i was retyping.
   the server in another part of the room , so i needed to write down what I saw and type in on this system when I'm in the forum. ( i need new glasses ;))
 ( was not able to connect to the server's shares to pull the saved output)

 once i got the raid boot issue fixed , it took awhile for me to connect this system to the share , but i reposted the drive info.

 i think the raid is ok, 
   i just need to fix the permissions,  I can read from the share, just cant write to it. 
     I need to look at samba config file, and I  need to check user accounts ( not sure if  chown and chmod need to be to the shares).
       i've not setup or needed a Samba workgroup in the past but i'll need to do that now,
   i have a couple of users that will need to backup their stuff, and i don't want them using anything but their own share, i have a few links to samba permission setup but other link you may have are welcome

---

### Post by TheFu on 2021-01-10
You aren't using ssh and sftp for this?  Ouch.

---

### Post by tross9 on 2021-01-11
yes , ouch
   and a lot of typo on my part

---

### Post by TheFu on 2021-01-11
> **tross9 said:**
> yes , ouch
   and a lot of typo on my part

ssh between Unix systems is trivial to setup. 3 commands, 30 seconds. Done.
```

Step 0:  Install openssh-server on the remote system or use the metapackage "openssh" for the client and the server.
   $ sudo apt install openssh fail2ban

Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
 The "username" is optional and not needed if the same between the
 client machine and remote server.
 "remote" can be a DNS name, IP address, some manually setup lookup
 inside the /etc/hosts or configured in the ~/.ssh/config file.

Step 3: Test that ssh works.  ssh into the remote system, 
   $ ssh username@remote
```

Can't help with Windows, but Win10 added ssh-client support and I vaguely recall helping someone set that up last fall. It was the same, but "Windows-like" and there isn't any ssh-copy-id command, so copying the public key has to be done manually in a way that doesn't break things like permissions or adding newlines.

I install fail2ban on every system with ssh to block brute force attacks. The fail2ban settings address this by default on the default ssh port 22/tcp. There isn't much downside (if any) and it does so much to protect ssh it isn't worth NOT installing.  sshd_config can be tweaked for all sorts of other protections, but I only do that for known internet-facing ssh servers.

---

### Post by tross9 on 2021-01-11
/dev/md127:
        Version : 1.2
  Creation Time : Sun Jan 10 11:47:32 2021
     Raid Level : raid1
     Array Size : 976630464 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976630464 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Mon Jan 11 09:31:29 2021
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : server1:0  (local to host server1)
           UUID : 9f8bf34d:cec9426b:a9982750:0f71e4cd
         Events : 2508


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1


I assume that this means that the raid is setup correctly, if so, I close this post.

  again thanks to everyone for the help , and especially your patience.

---

### Post by TheFu on 2021-01-11
> **tross9 said:**
>  
I assume that this means that the raid is setup correctly, if so, I close this post.

Only you close it. **Thread tools** button near the top.

---

