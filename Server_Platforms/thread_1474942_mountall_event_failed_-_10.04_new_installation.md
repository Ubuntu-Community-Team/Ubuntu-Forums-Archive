---
title: "mountall: event failed - 10.04 new installation"
date: 2010-05-06
forum: Server Platforms
---

### Post by wkande on 2010-05-06
I just installed 10.04 on two different servers using the ISO image. Both give me messages that concern me during boot. Perhaps I do not understand them.


1) init: mounted-tmp main process (874) terminated with status 127

2) mountall: Event failed

I booted with and without the ureadahead package installed. I understand that a ureadahead status of 4 is OK. The system seems to run well. I just am concerned about the two lines above that are found in both boot.log files shown below.

Thanks,
Warren Anderson

************************************

With the package ureadahead installed

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
root: clean, 8807/2445984 files, 269092/9764864 blocks
usr_local: clean, 36/2445984 files, 198568/9764864 blocks (check in 4 mounts)
tmp: clean, 12/3055616 files, 237822/12206848 blocks (check in 5 mounts)
srv: clean, 13/610800 files, 76474/2441216 blocks
srv_logs: clean, 11/305216 files, 54318/1220352 blocks
home: clean, 19/610800 files, 76478/2441216 blocks
var: clean, 2107/610800 files, 118074/2441216 blocks
usr: clean, 41716/1220608 files, 225848/4882432 blocks
opt: clean, 11/915712 files, 99180/3661824 blocks (check in 5 mounts)
srv_data: clean, 11/21364736 files, 1390711/85448960 blocks (check in 2 mounts)
boot: clean, 211/122160 files, 24455/488192 blocks
init: ureadahead-other main process (876) terminated with status 4

init: mounted-tmp main process (877) terminated with status 127

mountall: Event failed
init: ureadahead-other main process (883) terminated with status 4

init: ureadahead-other main process (888) terminated with status 4

init: ureadahead-other main process (893) terminated with status 4

init: ureadahead-other main process (898) terminated with status 4

init: ureadahead-other main process (903) terminated with status 4

init: ureadahead-other main process (912) terminated with status 4

init: ureadahead-other main process (917) terminated with status 4

init: ureadahead-other main process (922) terminated with status 4

init: ureadahead-other main process (927) terminated with status 4

 * Starting AppArmor profiles       ^[[160G
^[[154G[ OK ]



*******************************************

With the package ureadahead removed (sudo aptitude purge ureadahead)

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
root: clean, 8804/2445984 files, 269079/9764864 blocks
srv: clean, 13/610800 files, 76474/2441216 blocks
srv_logs: clean, 11/305216 files, 54318/1220352 blocks
boot: clean, 211/122160 files, 24455/488192 blocks
home: clean, 19/610800 files, 76478/2441216 blocks
var: clean, 2099/610800 files, 118011/2441216 blocks
usr: clean, 41711/1220608 files, 225843/4882432 blocks
usr_local: clean, 36/2445984 files, 198568/9764864 blocks (check in 5 mounts)
opt: clean, 11/915712 files, 99180/3661824 blocks
tmp: clean, 12/3055616 files, 237822/12206848 blocks
srv_data: clean, 11/21364736 files, 1390711/85448960 blocks (check in 3 mounts)
init: mounted-tmp main process (874) terminated with status 127

mountall: Event failed
 * Starting AppArmor profiles       ^[[160G
^[[154G[ OK ]

---

### Post by Neolo on 2010-05-07
[COLOR=Black]Same error after update from 9.10![/COLOR]

---

### Post by wkande on 2010-05-13
Can anyone offer insight mostly to the line:

mountall: Event failed

---

### Post by lavinog on 2010-05-16
There was an update to mountall today, do you still get this with the updated version?

---

### Post by wkande on 2010-05-16
Sadly it did not fix it. I tried on two different servers, same problem.

---

### Post by durwoodg on 2010-06-03
I'm having the exact same issue after a fresh install of 10.04 server.

The following is probably unrelated but for completeness:

I did have a panic crash and there were errors in my fsck of /var on reboot which were not resolved.  I have yet to figure out a way to umount /var -- ubuntu single-user mode still mounts all file systems :( -- so i rebooted to single user and "risked" running fsck on the mounted /var since the only error was in the inode count. That did seem to fix all my disk issues BUT i'm still getting the same messages that the poster stated.  I was getting them after my "panic" crash AND after my fsck /var -- not sure if i was getting them before the panic crash or not.

---

### Post by isaacjgs on 2010-06-08
Indeed, I am having the same problem. Clean install, I have the following partitions on my 40 GB hard drive.

fat32 (primary partition; has Win98 for old software 3GB)
/boot (primary parition, ext2 100 MB)

(Extended partition here encompasses all of the following logical drives/mount points:)
swap (~384 MB)
/ (ext3 250 MB)
/tmp (ext3 100 MB)
/usr (ext2 about 6 GB)
/usr/local (ext3 about 7 GB)
/var (ext3 3 GB)
/var/log (ext3 100 MB)

I have /home mounted to a SATA RAID1 pair of 500 GB hard drives.

The first line I get a ureadahead status 5, then I get a bunch of ureadahead-other status 4s after that (which are unrelated, so as I've read; some web site said reinstalling the package with aptitude reinstall ureadahead may help), along with mount-tmp main process (620) terminated with status 127 (whatever that means), and then the next line says "mountall: Event failed"

It hung. However, I remembered that there were weird occasions (in the past) that I could still log in even if there doesn't appear to be a login screen. So I typed in my name, but the moment I hit "s" then it said something about "Skipping /home at user request." Then it gave me the login screen. I wasn't able to login because all of a sudden I had to do something else. I'll try logging in tomorrow.

~Isaac~

---

### Post by lavinog on 2010-06-08
> **isaacjgs said:**
> Indeed, I am having the same problem. Clean install, I have the following partitions on my 40 GB hard drive.

fat32 (primary partition; has Win98 for old software 3GB)
/boot (primary parition, ext2 100 MB)

(Extended partition here encompasses all of the following logical drives/mount points:)
swap (~384 MB)
/ (ext3 250 MB)
/tmp (ext3 100 MB)
/usr (ext2 about 6 GB)
/usr/local (ext3 about 7 GB)
/var (ext3 3 GB)
/var/log (ext3 100 MB)

I have /home mounted to a SATA RAID1 pair of 500 GB hard drives.

The first line I get a ureadahead status 5, then I get a bunch of ureadahead-other status 4s after that (which are unrelated, so as I've read; some web site said reinstalling the package with aptitude reinstall ureadahead may help), along with mount-tmp main process (620) terminated with status 127 (whatever that means), and then the next line says "mountall: Event failed"

It hung. However, I remembered that there were weird occasions (in the past) that I could still log in even if there doesn't appear to be a login screen. So I typed in my name, but the moment I hit "s" then it said something about "Skipping /home at user request." Then it gave me the login screen. I wasn't able to login because all of a sudden I had to do something else. I'll try logging in tomorrow.

~Isaac~
Can you post your /etc/fstab?
It might be that mountall is not waiting for home to be checked.

You can ignore the ureadahead status 4 messages, status 4 means that it completed successfully.  I believe it was mentioned by keybuk that the bug is actually upstart is not supposed to report status 4 messages.

---

### Post by isaacjgs on 2010-06-09
I also had a status 5 with ureadahead. Status 5, as one web page indicates, has something to do with /var. Also, I suspect that my /var and /var/log are being mounted as read-only and I may not be able to get access to any of the logs in /var/log. I will be able to access my machine later though...I'll provide more details when I get to it.

~Isaac~

P.S.

Oh, I must say, earlier today I used the CD-ROM to "Fix a broken system" for the first time. The only root filesystem that I could mount was sda6. I cd'ed into /var and the only two listings I get were ./lock and ./run. No ./log subdir. (Also with Karmic, the earlier version, I had no problems with it; this was a clean reinstall to install 10.04)

As for /home, I saw the following in /etc/fstab using less:

# <file system>                                         <mount point>   <type>     <options>           <dump>      <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda6 during installation
UUID=a572177c-661a-4cbf-a348-caa857e37de3 / ext3 errors=remount-ro 0 1
# /boot was on /dev/sda2 during installation
UUID=19ede422-b808-41cd-871f-29f506ca05ff /boot ext2 defaults 0 2
# /home was on /dev/md0 during installation
UUID=a8542e12-b375-4f4a-bed4-ab25824563ac /home          ext3          defaults                   0               2
# /tmp was on /dev/sda7 during installation
UUID=bba55a0b-bcf9-4f92-8a9d-d6f1ca6edb7e /tmp ext3 defaults 0 2
# /usr was on /dev/sda8 during installation
UUID-c4c69397-bcac-4270-a243-679e094d80cc /usr /ext2 defaults 0 2
#/usr/local was on /dev/sda11 during installation
UUID=31bf84cb-6f78-44e5-be21-2bb1ff0b3943 /usr/local ext3 defaults 0 2
# /var was on /dev/sda10 during installation
UUID=d724ab95-73c6-4339-968d-e65d811767b3 /var             ext3          defaults                   0               2
# /var/log was on /dev/sda9 during installation
UUID=5ca106fa-a97e-4f24-b818-b5496846596f /var/log          ext3          defaults                  0                2
#swap was on /dev/sda5 during installation
UUID=2bbb4c3c-d1da-456c-bfcc-d0cdcff02270 none swap sw 0 0

I had to manually type these out. The problem filesystems at this point are /home, /var and /var/log (being mounted as read-only) and apparently /tmp (because of "mount-tmp main process (620) terminated with status 127"), as described earlier in my post(s).

---

### Post by lavinog on 2010-06-09
> **isaacjgs said:**
> I also had a status 5 with ureadahead. Status 5, as one web page indicates, has something to do with /var. Also, I suspect that my /var and /var/log are being mounted as read-only and I may not be able to get access to any of the logs in /var/log. I will be able to access my machine later though...I'll provide more details when I get to it.

~Isaac~
I think it could mean a couple of things.
I think you can get a status 5 if /var/lib/ureadahead/debugfs doesn't exist.

---

### Post by isaacjgs on 2010-06-09
Thanks for your prompt response. It is greatly appreciated. Anything fishy or wrong with my fstab or anything that I should know about? Anything unusual, when you said that mountall may not be giving /home enough time to be checked? I'm curious as to what the <dump> and <pass> columns mean and if they have anything to do with this.

~Isaac~

---

### Post by lavinog on 2010-06-09
> **isaacjgs said:**
> 
```

# <file system>                                         <mount point>   <type>     <options>           <dump>      <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda6 during installation
UUID=a572177c-661a-4cbf-a348-caa857e37de3 / ext3 errors=remount-ro 0 1
# /boot was on /dev/sda2 during installation
UUID=19ede422-b808-41cd-871f-29f506ca05ff /boot ext2 defaults 0 2
# /home was on /dev/md0 during installation
UUID=a8542e12-b375-4f4a-bed4-ab25824563ac /home          ext3          defaults                   0               2
# /tmp was on /dev/sda7 during installation
UUID=bba55a0b-bcf9-4f92-8a9d-d6f1ca6edb7e /tmp ext3 defaults 0 2
# /usr was on /dev/sda8 during installation
UUID-c4c69397-bcac-4270-a243-679e094d80cc /usr /ext2 defaults 0 2
#/usr/local was on /dev/sda11 during installation
UUID=31bf84cb-6f78-44e5-be21-2bb1ff0b3943 /usr/local ext3 defaults 0 2
# /var was on /dev/sda10 during installation
UUID=d724ab95-73c6-4339-968d-e65d811767b3 /var             ext3          defaults                   0               2
# /var/log was on /dev/sda9 during installation
UUID=5ca106fa-a97e-4f24-b818-b5496846596f /var/log          ext3          defaults                  0                2
#swap was on /dev/sda5 during installation
UUID=2bbb4c3c-d1da-456c-bfcc-d0cdcff02270 none swap sw 0 0

```


dump is for the dump backup program (shouldn't cause any issues)
pass determines the order of fsck, but I am not sure if it is used by the mountall program anymore.

My first question is why do you have so many filesystems?
I can understand having a separate home, but why does var and var/log have their own partitions...this seems like it could be a waste of harddrive space...and could cause a problem if you run out of space.

I wonder if there is a race condition where the diskcheck for /var/log is completing before /var

try adding bootwait to each line next to defaults
for example:
```

UUID=a8542e12-b375-4f4a-bed4-ab25824563ac /home          ext3          defaults,bootwait                   0               2

```

> The  mountall(8)  program  that  mounts filesystem during boot also recognises additional options that the ordinary mount(8) tool does not.  These
       are: ``bootwait'' which can be applied to remote filesystems mounted outside of /usr or /var, without which mountall(8) would not hold up the boot
       for  these;  ``nobootwait''  which  can  be applied to non-remote filesystems to explicitly instruct mountall(8) not to hold up the boot for them;
       ``optional'' which causes the entry to be ignored if the filesystem type is not known at boot time; and ``showthrough'' which permits a mountpoint
       to be mounted before its parent mountpoint (this latter should be used carefully, as it can cause boot hangs).



Is your home drive a raid setup?

---

### Post by isaacjgs on 2010-06-09
Affirmative, but only for the /home. /home is on a RAID 1 pair of 500 GB hard drives. The rest of the mount points are on a smaller 20 GB hard drive device. I was wondering if having so many partitions could have actually caused the problem I am having now. I had the same RAID 1 setup for /home when I had Karmic installed and had no issues.

---

### Post by isaacjgs on 2010-06-09
Okay, I have access to the system again. Added bootwait to each line, but it still hangs in the end. I probably am going to just reinstall Karmic if there are no other solutions.

---

### Post by luc1kJke on 2010-06-12
same problem for me
here's my fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e20ab896-62ce-46d0-aed6-4c39219792bb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=50b10387-d50a-4b3e-9cc6-c83efcf5e80d /home           ext4    defaults        0       2
/dev/sdb6       /usr            ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=569d72d7-2d5d-46de-a3a2-71e0d76d00e5 none            swap    sw              0       0
```

after i installed 10.04(clean installation) i had problem that randomly occur. When booting i get 
"[I]init: mounted-tmp main process (874) terminated with status [I]127 
[/I][/I]*mountall: event failed*"

i'm newbie in Ubuntu so i don't know how to solve prob(except of downgrading to Karmic)

---

### Post by isaacjgs on 2010-06-13
I fixed the problem. What was weird was that I deleted the whole entire ext3 partition on both of the individual SATA 500 GB drives. I was because during the first install, I saw that a tiny portion of the disk was "unusable." It must have been a little less than 1 megabyte. Seeing that "unusable" portion of the drive there, I reasoned, "Why was it NOT giving me the full drive?" Therefore I deleted the ext3 partitions with GParted, and then the space was unallocated, but I didn't reformat it with GParted. Instead, I went into Ubuntu Server Install, and repartitioned those two large hard drives and formatted them there. I formatted them as "Physical Volume for RAID" which is what I was supposed to do. Then I saw for each drive, this:

FREE SPACE (tiny bit, perhaps less than 1 MB)
500.1 GB K RAID
FREE SPACE (same, less than 1 MB).

FREE SPACE (tiny bit, perhaps less than 1 MB)
500.1 GB K RAID
FREE SPACE (same, less than 1 MB).

So I thought, "This is strange. It has the FREE SPACE between those tiny unusable portions of unallocated data."

So then I configured Software RAID, made a new MD device, selected the two drives with the RAID, and it took me back to the menu where it lists all the other partitions.

But I didn't see an entry for a RAID device near the top, as I should have seen it. I still saw the

FREE SPACE
500.1 GB K RAID
FREE SPACE

FREE SPACE
 500.1 GB K RAID
 FREE SPACE

at the bottom. So then I selected "write changes to disk" and continued, thinking that it would do it automatically afterward and I didn't think much of it.

After the install, it didn't mount /home. After that, I came to you guys. Someone suggested lengthening the boot time, which didn't work (thanks for your help though). But then I started to wonder, "You know, that time when I saw the sandwiched RAID space during the time when I was setting up RAID, it wasn't doing that in previous Ubuntu Server installations in previous versions before. There might be something wrong with the partitioning. I also looked in Mark Sobell's 8.04/8.10 Practical Guide to  Ubuntu Linux, and I noticed that on his screenshots there weren't any sandwiched RAID spaces, although it did show one slot for each of his RAID drives where were was a tiny amount of space. But it also showed me that he RAID1 device was listed at the top of the screen after making the md device and selecting the disks.

That was when I realized something was wrong with the partitioning. I went back into GParted, reformatted all the Linux partitions on the 40 GB drive, and proceeded to delete the partitions on the 500 GB drives. But when I tried to delete the partition on one of the drives, it complained, saying that there may be something wrong with GParted. Then I rebooted, went back into GParted, proceeded to delete the partition again, and it said that I needed a new partition table, which I then created, and THEN I could make a new ext3 partition and format it. Both hard drives were formatted with ext3, so then I proceeded to reinstall Ubuntu Server.

When I went to set up software RAID again, I selected both ext3 partitions and selected "physical volume for RAID" for each of them again. I didn't see a sandwiched RAID space; I saw a single tiny bit of unusable space for each of the drives; otherwise, I saw 500.1 MB for each, for the physical volume for RAID. At this point, I'm thinking it's going to work. I then set up software RAID, went to select an md device, then selected the disks that had the RAID volumes on them again, and then it took me back to the screen where all the other partitions were, but this time the results were different. I saw a RAID1 device at the top of my list, just as it should have been, along with a tiny unusable bit of space. And then I scrolled down and I didn't see the sandwiched RAID space; I did see a tiny unusable space, along with the 500.1 MB of free space.

Now I realized what I did wrong the first time.

Then I selected the RAID device at the top and formatted with ext3. Done!

Then I reinstalled and rebooted.

I still get the mountall: Event failed error, but this time it really did mount my /home directory. I know that it said, "mountall: Event failed". I also know that these the two partitions /var and /var/log partitions were mounted, after I logged on, as "read-only." I'm thinking that there may be a connection between the two.

---

### Post by wakefia on 2010-06-29
Anything more on this ?

I get exactly the same errors on boot as the OP. System appears usable.

All packages up to date.

---

### Post by RobDonovan on 2010-07-02
1) The boot errors 

```

init: mounted-tmp main process (877) terminated with status 127
mountall: Event failed

```are caused by Ubuntu Bug [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/523587](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/523587)

I solved it on my system by editing /etc/init/mounted-tmp.conf to read the following:

```

# start on mounted MOUNTPOINT=/tmp
start on local-filesystems

```Obviously if you have a remote /usr partition you'll need something else here.

2) The fscks are intended behaviour of mountall on boot.  You can get rid of them by changing the 6th field of your /etc/fstab field to 0.  However this may not be a good idea since then your disks will never be checked for errors.  Some previous versions of *nix have used an /etc/fastboot flag to skip fscking if everything was umounted successfully on shutdown, but Ubuntu doesn't seem to do this.

3) If you get two sets of fscks on boot you may be interested in following this bug report [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/605687](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/605687)

4) The discussion of the problems with /usr and /var umount at shutdown which was previously on this thread has been moved to [http://ubuntuforums.org/showthread.php?p=9561593](http://ubuntuforums.org/showthread.php?p=9561593)

---

### Post by imota on 2010-09-16
I actually reported a bug on launchpad related to this:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/638238](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/638238)

It started after I ran a system upgrade and got the latest samba and smbfs package patches. I have the linux filesystem on its own HD (160GB), dual-booting with windows XP sitting on another HD (250GB)

I also have shares on NTFS (Microsoft Server 08 shares) - it's a work computer.

Here's my boot.log:

```

fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
/dev/sdb1: clean, 182347/644640 files, 1254103/2578424 blocks 
/dev/sdb3: recovering journal 
Extra_Data: clean, 37/6381568 files, 4561156/25497155 blocks 
init: ureadahead-other main process (840) terminated with status 4  
init: ureadahead-other main process (849) terminated with status 4  
error -1 (Unknown error 18446744073709551615) opening credential file /home/imota/.smbcredentials 
error -1 (Unknown error 18446744073709551615) opening credential file /home/imota/.smbcredentials 
mountall: mount /media/IwanMota [850] terminated with status 1 
mountall: mount /media/EngineerShare [853] terminated with status 1 
error -1 (Unknown error 18446744073709551615) opening credential file /home/imota/.smbcredentials 
mountall: mount /media/ITEngShare [851] terminated with status 1 
error -1 (Unknown error 18446744073709551615) opening credential file /home/imota/.smbcredentials 
mountall: mount /media/ScannedDocs [854] terminated with status 1 
/dev/sdb3: clean, 19558/8871936 files, 4520705/35459471 blocks 
mount error: cifs filesystem not supported by the system 
mount error(19): No such device 
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) 
mountall: mount /media/IwanMota [896] terminated with status 32 
mount error(101): Network is unreachable 
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) 
mount error(101): Network is unreachable 
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) 
mountall: mount /media/ITEngShare [898] terminated with status 32 
mountall: mount /media/ScannedDocs [907] terminated with status 32 
 * Starting AppArmor profiles       [180G mount error(101): Network is unreachable 
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) 
mountall: mount /media/EngineerShare [902] terminated with status 32 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

```and here's my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ee0061ca-3ab4-425a-b3a2-9d82ee6dde75 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=4ca20b4b-2bfb-4d39-bfac-bdfb33d90e16 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=c798fd10-08d4-4373-86d9-0bf0d9a77101 none            swap    sw              0       0

#ADDED 20100907
UUID=DA44227544225513 /media/DATA           ntfs    defaults        0       0
UUID=d2bff7a8-abdf-43c7-ad20-1e9d7acb02c4 /media/ExtraData ext4 defaults 0 2

#ADDED 20100830
//192.0.0.212/IwanMota /media/IwanMota cifs iocharset=utf8,credentials=/home/imota/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.0.0.212/ITEngShare /media/ITEngShare cifs iocharset=utf8,credentials=/home/imota/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.0.0.212/EngineerShare /media/EngineerShare cifs iocharset=utf8,credentials=/home/imota/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.0.0.212/ITEngShare/ScannedDocs /media/ScannedDocs cifs iocharset=utf8,credentials=/home/imota/.smbcredentials,file_mode=0777,dir_mode=0777 0 0

```Packages installed:

```

apt-cache show libsmbclient libwbclient0 samba samba-common samba-common-bin smbclient smbfs | grep -i version
Version: 2:3.4.7~dfsg-1ubuntu3.2
Version: 2:3.4.7~dfsg-1ubuntu3
Version: 2:3.4.7~dfsg-1ubuntu3.2
Version: 2:3.4.7~dfsg-1ubuntu3
Version: 2:3.4.7~dfsg-1ubuntu3.2
Version: 2:3.4.7~dfsg-1ubuntu3
Version: 2:3.4.7~dfsg-1ubuntu3.2
Version: 2:3.4.7~dfsg-1ubuntu3
Version: 2:3.4.7~dfsg-1ubuntu3.2
Version: 2:3.4.7~dfsg-1ubuntu3
Version: 2:3.4.7~dfsg-1ubuntu3.2
Version: 2:3.4.7~dfsg-1ubuntu3
Version: 2:3.4.7~dfsg-1ubuntu3.2
Version: 2:3.4.7~dfsg-1ubuntu3

```

---

