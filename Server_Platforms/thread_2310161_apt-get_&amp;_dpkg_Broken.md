---
title: "apt-get &amp; dpkg Broken"
date: 2016-01-16
forum: Server Platforms
---

### Post by Eddy Gordo from Tekken on 2016-01-16
ubuntu Server 14.04.2
apt-get is failing to complete upgrades and installs


cat /etc/apt/sources.list

```
#
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted

# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release amd64 (20081028.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## external PPA repository. added to install latest version
## of mumble and murmur
# deb http://ppa.launchpad.net/slicer/ubuntu jaunty main # disabled on upgrade to jaunty
# deb-src http://ppa.launchpad.net/slicer/ubuntu jaunty main # disabled on upgrade to jaunty

## I added this so that I can download virtual box
# deb http://download.virtualbox.org/virtualbox/debian jaunty non-free # disabled on upgrade to jaunty

## I added this so that I can get XBMC
# deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu jaunty main
```

/etc/apt/sources.list.d/
is empty

sudo apt-get update
```
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security InRelease
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

sudo dpkg --configure -a
no error

again
sudo apt-get update
```
Hit http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 64.4 kB in 8s (8,014 B/s)
Reading package lists... Done
```

sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-generic (= 3.13.0.71.77) but it is not installed
E: Unmet dependencies. Try using -f.
```

sudo apt-get -f install

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-accountsservice-1.0 gir1.2-gkbd-3.0 gir1.2-mutter-3.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-shell gnome-shell-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgail-3-0 libgtk-3-0 linux-generic linux-headers-3.13.0-57-generic
  linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-headers-generic linux-image-3.13.0-74-generic
  linux-image-extra-3.13.0-74-generic linux-image-generic linux-image-server
  linux-server
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-image-3.13.0-74-generic linux-image-extra-3.13.0-74-generic
The following packages will be upgraded:
  libgail-3-0 libgtk-3-0 linux-headers-3.13.0-57-generic linux-headers-generic
  linux-image-generic linux-image-server linux-server
7 upgraded, 5 newly installed, 0 to remove and 394 not upgraded.
3 not fully installed or removed.
Need to get 0 B/64.3 MB of archives.
After this operation, 285 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1276993 files and directories currently installed.)
Preparing to unpack .../libgail-3-0_3.10.8-0ubuntu1.6_amd64.deb ...
Unpacking libgail-3-0:amd64 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.5) ...
dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

sudo apt-get clean
no error

sudo apt-get autoclean
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

sudo dpkg --configure -a
no error

and then I'm in a loop....

---

### Post by ian-weisser on 2016-01-16
You seem to have more than one problem.


Here's one that's usually easy to solve. 
> **Eddy Gordo from Tekken said:**
> Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-generic (= 3.13.0.71.77) but it is not installed
E: Unmet dependencies. Try using -f.
Try:
```
sudo apt-get clean linux-generic                  ## Delete the old version in the local cache,to prevent it from getting reinstalled
sudo apt-get install --reinstall linux-generic    ## Download the latest version of linux-generic and install it.
```



Here's another that's usually easy to solve.
> **Eddy Gordo from Tekken said:**
> The following packages were automatically installed and are no longer required:
  gir1.2-accountsservice-1.0 gir1.2-gkbd-3.0 gir1.2-mutter-3.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-shell gnome-shell-common
Use 'apt-get autoremove' to remove them.
Simply follow the advice and try:
```
sudo apt-get autoremove
```




Here's the tough one.
> **Eddy Gordo from Tekken said:**
> 
Preparing to unpack .../libgail-3-0_3.10.8-0ubuntu1.6_amd64.deb ...
Unpacking libgail-3-0:amd64 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.5) ...
dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)
First, take a look at [http://askubuntu.com/questions/253466/why-am-i-frequently-getting-this-cannot-allocate-memory-error](http://askubuntu.com/questions/253466/why-am-i-frequently-getting-this-cannot-allocate-memory-error)
That tells you what the issues are likely to be, and some of the information you will need to help figure out the cause.
Try the 'sudo apt-get update' and 'sudo apt-get upgrade' right after a reboot, when the most memory will be available.
I know packages, and don't claim to have a definitive answer for the memory issue - perhaps a guru skilled in that end of the system will chime in.

---

### Post by Eddy Gordo from Tekken on 2016-01-17
okay, I followed the suggestions. I got kinda frustrated (ie punchy with the keyboard) and didn't print the results of all the commands. but here goes

sudo apt-get clean linux-generic
no errors

sudo apt-get install --reinstall linux-generic
failed

but I pressed on...
sudo apt-get autoremove
failed

so I tried suggestions from the link...
free -m
~60 free from 741

swapon -s
nothing displays.  A problem for another time I think...?

ulimit -a
max user processes was ~3000...ie not 'unlimited'....

so I restarted the server
sudo shutdown -r now

when it came up, it went to check disk.  After check disk completed, I ran

sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

no errors

free -m
```
         total       used       free     shared    buffers     cached
Mem:           741        691         49          0        130        336
-/+ buffers/cache:        224        516
Swap:            0          0          0
```

swapon -s

```
Filename                                Type            Size    Used    Priority
```

ulimit -a

```
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 5722
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 5722
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

---

### Post by Bashing-om on 2016-01-18
Eddy Gordo from Tekken; Well ....

Observations ...
> 
Mem:           741        691         49 

real short on memory, can you add additional ram ?

> 
Swap:            0          0          0

No swap partition ? In this situation of low memory, you sure need the ability to lessen the load on ram and page out to the hard drive.
My system with 4 Gigs of ram, and a VeRy small swap partition:
```

sysop@1404mini:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3953       1006       2947         35         62        570
-/+ buffers/cache:        373       3580
Swap:            7          0          7
sysop@1404mini:~$

```
Where I do not have much going on and swap is not even being touched ! .. But it is there in the event of need ( there have been a couple of times I have crashed the system running out of memory )

What do we have to work with ?
post back :
```

sudo fdisk -lu
sudo blkid

```

And we get an idea of what our options are, and what you want to do .

[INDENT][INDENT]trying to do Ferrari with a VW ?
[/INDENT][/INDENT]

---

### Post by Eddy Gordo from Tekken on 2016-01-18
Thank you both for the help
i'll check to see if I have suitable RAM around here somewhere.
in the meantime...here are the results of your suggestions

sudo fdisk -lu
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 3000.4 GB, 3000370200576 bytes
255 heads, 63 sectors/track, 364774 cylinders, total 5860098048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   483909929   241954933+  83  Linux
/dev/sdb2       483909930   488392064     2241067+   5  Extended
/dev/sdb5       483909993   488392064     2241036   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907029167  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  3907029167  1953514583+  ee  GPT
```

sudo blkid
```
/dev/sdb1: UUID="4ed3b515-f037-422e-8103-89672ea44acd" TYPE="ext3"
/dev/sda1: UUID="49d65e80-8a65-4a7c-8969-6d9f04cfd2b2" TYPE="ext3"
/dev/sdb5: UUID="3b881a54-2299-4e42-9a15-ff348024e2a1" TYPE="swap"
/dev/sdc1: LABEL="First" UUID="cbf75ed4-35a5-4f96-acd8-a631f36ede1b" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdd1: LABEL="third" UUID="bb76be71-4310-4920-8241-e09337188bb0" SEC_TYPE="ext2" TYPE="ext3"
```

---

### Post by Bashing-om on 2016-01-19
Eddy Gordo from Tekken; Well !

You have a swap partition !
> 
/dev/sdb5       483909993   488392064     2241036   82  Linux swap / Solaris
bk
/dev/sdb5: UUID="3b881a54-2299-4e42-9a15-ff348024e2a1" TYPE="swap"

So that begs the question, why is it not being used ?
> 
free -m >> Swap:            0          0          0


Let's take a look at the (F)ile (S)ystem (TAB)le. See what is set there for the swap partition:
```

cat /etc/fstab

```

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by Eddy Gordo from Tekken on 2016-01-19
here goes...

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4ed3b515-f037-422e-8103-89672ea44acd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
# UUID=3de70bf2-deb2-4ec7-bd1b-214fd9ad9688 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# after upgrading from server 10 to server 12 the drive designation changed
#/dev/sda1       /etal           ext3   defaults         1      1
#/dev/sdb1      /etal           ext3    defaults        1       1
/dev/sda1       /etal           ext3    defaults        1       1

```

---

### Post by Bashing-om on 2016-01-19
Eddy Gordo from Tekken; OK, Uh Huh, yeah ..

Amongst all the other issues in fstab, there is no swap partition setup.
You are currently booting from the 1st partition of the 2nd hard drive (sdb1).


Question: are you really running ext3 as the file systems ? ext4 ( 4th generation) has been the default file system for some years now and has many advantages over ext3 .
ext3 on all your partitions' file systems ??

Question: what in the world is;
"/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0"
What is the requirement to explicitly declare the CD drive ? 
The gvfs system should take care of the cd drive !

As to swap:
make up a entry - after making a backup of the current /etc/fstab file :
Or edit the current entries to reflect " 3b881a54-2299-4e42-9a15-ff348024e2a1 " as the UUID - removing the starting comment (#) character.
Like so:
```

# swap is on /dev/sdb5 as of 19Jan2016
UUID=3b881a54-2299-4e42-9a15-ff348024e2a1 none            swap    sw              0      0

```

Once the edit is made and the file is saved; check that the system accepts the entry as valid:
```

sudo mount -a 

```
no response to the screen when the command is executed is a good thing. Means the system is happy with the fstab file . Else:
the system will scream and holler ... the errors to the terminal .

If the system is happy;
Now reboot for the swap partition to be recognized by the system and what now shows from:
```

free -m

```

[INDENT][INDENT][INDENT]all in the care and feeding of your 'buntu
[/INDENT][/INDENT][/INDENT]

---

### Post by darkod on 2016-01-20
There is no need to reboot at the end. Simply try:
```
sudo swapon -a
```

In fact that command might be able to pick up and activate all swap partitions, regardless of fstab entries. I've never tried it like that. So you could even try activating the swap like that and sorting out the fstab later. But you do need to sort it out as suggested above.

---

### Post by Eddy Gordo from Tekken on 2016-01-30
> Question: are you really running ext3 as the file systems ? ext4 ( 4th generation) has been the default file system for some years now and has many advantages over ext3 .
 ext3 on all your partitions' file systems ??

I used ext3 because I'm on a mixed network or Linux/windoze/android/smart tv. I believed at the time that ext3 was more flexible for that. I'll consider changing it

> Question: what in the world is;
 "/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0"
 What is the requirement to explicitly declare the CD drive ? 
 The gvfs system should take care of the cd drive !

I don't know what to make of this as the CDRom is currently disconnected from the server. Once I get this apt/dpkg thing settled, I'll tackle this.

Current fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4ed3b515-f037-422e-8103-89672ea44acd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
# swap is on /dev/sdb5 as of 20jan2016
UUID=3b881a54-2299-4e42-9a15-ff348024e2a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# after upgrading from server 10 to server 12 the drive designation changed
#/dev/sda1       /etal           ext3   defaults         1      1
#/dev/sdb1      /etal           ext3    defaults        1       1
/dev/sda1       /etal           ext3    defaults        1       1
```

sudo apt-get update
```
Get:1 http://security.ubuntu.com trusty-security InRelease [64.4 kB]
Ign http://us.archive.ubuntu.com trusty InRelease
Get:2 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty Release
Get:3 http://security.ubuntu.com trusty-security/main Sources [103 kB]
Get:4 http://us.archive.ubuntu.com trusty-updates/main Sources [248 kB]
Get:5 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B]
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [5,359 B]
Get:7 http://security.ubuntu.com trusty-security/universe Sources [33.1 kB]
Get:8 http://us.archive.ubuntu.com trusty-updates/universe Sources [147 kB]
Get:9 http://security.ubuntu.com trusty-security/multiverse Sources [2,357 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,161 B]
Get:11 http://security.ubuntu.com trusty-security/main amd64 Packages [410 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [689 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [335 kB]
Get:15 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:17 http://security.ubuntu.com trusty-security/universe amd64 Packages [123 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [663 kB]
Get:19 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,798 B]
Get:20 http://security.ubuntu.com trusty-security/main i386 Packages [384 kB]
Get:21 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:22 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [335 kB]
Get:23 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Get:25 http://security.ubuntu.com trusty-security/universe i386 Packages [123 kB]
Get:26 http://us.archive.ubuntu.com trusty-updates/main Translation-en [348 kB]
Get:27 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4,955 B]
Get:28 http://security.ubuntu.com trusty-security/main Translation-en [225 kB]
Get:29 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,437 B]
Get:30 http://security.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:31 http://security.ubuntu.com trusty-security/universe Translation-en [72.1 kB]
Get:32 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Get:33 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:34 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [176 kB]
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 4,668 kB in 12s (364 kB/s)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

sudo dpkg --configure -a
no errors

sudo apt-get update
```
Hit http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty Release
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done
```

sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
```

sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  alsa-base alsa-utils apg avahi-utils bluez brasero-cdrkit brasero-common
  cups-pk-helper dvd+rw-tools epiphany-browser-data evince-common
  evolution-data-server folks-common gamin gconf2 genisoimage
  geoclue-ubuntu-geoip gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0
  gir1.2-panelapplet-4.0 gir1.2-peas-1.0 gir1.2-totem-1.0
  gir1.2-totem-plparser-1.0 growisofs gstreamer0.10-alsa gstreamer0.10-gconf
  gstreamer0.10-nice gstreamer0.10-x hwdata indicator-applet
  indicator-applet-complete indicator-datetime indicator-messages
  indicator-power indicator-printers indicator-status-provider-mc5
  launchpad-integration libarchive12 libavahi-compat-libdnssd1 libbonobo2-0
  libbonobo2-common libbrasero-media3-1 libburn4 libdecoration0 libdotconf1.0
  libevdocument3-4 libevview3-3 libexempi3 libfolks-eds25 libfolks-telepathy25
  libfolks25 libg15daemon-client1 libgail-3-0 libgamin0 libgdata-common
  libgdata13 libgee2 libglib2.0-bin libgrip0 libgtkmm-3.0-1 libgxps2
  libindicate-gtk3 libindicator-messages-status-provider1 libisofs6 libjte1
  libkpathsea6 liblaunchpad-integration-3.0-1 liblaunchpad-integration-common
  liblircclient0 libmeanwhile1 libmission-control-plugins0
  libnautilus-extension1a libnm-glib-vpn1 liboauth0 liborbit2
  libpanel-applet-4-0 libpoppler-glib8 libpoppler44 libpurple-bin
  libquvi-scripts libquvi7 libspectre1 libspeechd2 libt1-5 libtotem0
  libunity-misc4 libvdpau1 libwacom-common libwacom2 libwnck-common libwnck22
  libzeitgeist-1.0-1 libzephyr4 linux-sound-base
  mobile-broadband-provider-info modemmanager mousetweaks mutter-common
  network-manager network-manager-pptp nux-tools obexd-client pptp-linux
  python-cups python-cupshelpers python-gconf python-notify python-smbc
  python-xkit python3-xkit speech-dispatcher system-config-printer-common
  system-config-printer-udev telepathy-indicator telepathy-mission-control-5
  totem-common ubuntu-docs ubuntu-system-service unity-lens-files
  unity-lens-music unity-lens-video unity-scope-musicstores usb-modeswitch
  usb-modeswitch-data wodim
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxml2 libxml2-dev
The following packages will be upgraded:
  libxml2 libxml2-dev
2 upgraded, 0 newly installed, 0 to remove and 177 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,201 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1279319 files and directories currently installed.)
Preparing to unpack .../libxml2-dev_2.9.1+dfsg1-3ubuntu4.7_amd64.deb ...
Unpacking libxml2-dev:amd64 (2.9.1+dfsg1-3ubuntu4.7) over (2.9.1+dfsg1-3ubuntu4.6) ...
Preparing to unpack .../libxml2_2.9.1+dfsg1-3ubuntu4.7_amd64.deb ...
Unpacking libxml2:amd64 (2.9.1+dfsg1-3ubuntu4.7) over (2.9.1+dfsg1-3ubuntu4.6) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libxml2:amd64 (2.9.1+dfsg1-3ubuntu4.7) ...
Setting up libxml2-dev:amd64 (2.9.1+dfsg1-3ubuntu4.7) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
```

sudo apt-get upgrade
truncated, no errors
```
Get:36 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2.2-bin amd64 2.4.7-1ubuntu4.9 [1,478 B]
Get:37 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libecryptfs0 amd64 104-0ubuntu1.14.04.4 [46.8 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main ecryptfs-utils amd64 104-0ubuntu1.14.04.4 [101 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ trusty/universe indicator-applet-complete amd64 12.10.2+14.04.20140403-0ubuntu1 [20.0 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ trusty/main libgpod-common amd64 0.8.3-4ubuntu3 [22.3 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-firmware all 1.127.20 [24.5 MB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main os-prober amd64 1.63ubuntu1.1 [18.0 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main poppler-utils amd64 0.24.5-2ubuntu4.3 [118 kB]
Get:44 http://us.archive.ubuntu.com/ubuntu/ trusty/main python-smbc amd64 1.0.14.1-0ubuntu2 [16.1 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ trusty/main upower amd64 0.9.23-2ubuntu1 [85.7 kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ trusty/main usbmuxd amd64 1.0.8-2ubuntu1 [37.3 kB]
Fetched 47.7 MB in 13s (3,507 kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 1279319 files and directories currently installed.)
Preparing to unpack .../libapt-pkg4.12_1.0.1ubuntu2.11_amd64.deb ...
Unpacking libapt-pkg4.12:amd64 (1.0.1ubuntu2.11) over (1.0.1ubuntu2.10) ...
Setting up libapt-pkg4.12:amd64 (1.0.1ubuntu2.11) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 1279319 files and directories currently installed.)
Preparing to unpack .../apt_1.0.1ubuntu2.11_amd64.deb ...
Unpacking apt (1.0.1ubuntu2.11) over (1.0.1ubuntu2.10) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up apt (1.0.1ubuntu2.11) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 1279319 files and directories currently installed.)
Preparing to unpack .../libapt-inst1.5_1.0.1ubuntu2.11_amd64.deb ...
Unpacking libapt-inst1.5:amd64 (1.0.1ubuntu2.11) over (1.0.1ubuntu2.10) ...
Preparing to unpack .../libcurl3-gnutls_7.35.0-1ubuntu2.6_amd64.deb ...
Unpacking libcurl3-gnutls:amd64 (7.35.0-1ubuntu2.6) over (7.35.0-1ubuntu2.5) ...
Preparing to unpack .../libcurl3_7.35.0-1ubuntu2.6_amd64.deb ...
Unpacking libcurl3:amd64 (7.35.0-1ubuntu2.6) over (7.35.0-1ubuntu2.5) ...
Preparing to unpack .../libcurl3-nss_7.35.0-1ubuntu2.6_amd64.deb ...
Unpacking libcurl3-nss:amd64 (7.35.0-1ubuntu2.6) over (7.35.0-1ubuntu2.5) ...
Preparing to unpack .../libgl1-mesa-dri_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libgbm1_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libgbm1:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libgl1-mesa-glx_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libwayland-egl1-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libegl1-mesa-drivers_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libglapi-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libglapi-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libopenvg1-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libegl1-mesa_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libegl1-mesa:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../libgpod4_0.8.3-4ubuntu3_amd64.deb ...
Unpacking libgpod4:amd64 (0.8.3-4ubuntu3) over (0.8.2-4) ...
Preparing to unpack .../mysql-common_5.5.47-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-common (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../mysql-server_5.5.47-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-server (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Setting up mysql-common (5.5.47-0ubuntu0.14.04.1) ...
(Reading database ... 1279319 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
mysql stop/waiting
Unpacking mysql-server-5.5 (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../mysql-client_5.5.47-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-client (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../mysql-client-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-5.5 (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../mysql-client-core-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-core-5.5 (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../mysql-server-core-5.5_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-server-core-5.5 (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../libmysqlclient-dev_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libmysqlclient-dev (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../libmysqlclient18_5.5.47-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libmysqlclient18:amd64 (5.5.47-0ubuntu0.14.04.1) over (5.5.46-0ubuntu0.14.04.2) ...
Preparing to unpack .../libsane_1.0.23-3ubuntu3.1_amd64.deb ...
Unpacking libsane:amd64 (1.0.23-3ubuntu3.1) over (1.0.22-7ubuntu1) ...
Preparing to unpack .../libsane-common_1.0.23-3ubuntu3.1_amd64.deb ...
Unpacking libsane-common (1.0.23-3ubuntu3.1) over (1.0.22-7ubuntu1) ...
Preparing to unpack .../libxatracker2_10.1.3-0ubuntu0.6_amd64.deb ...
Unpacking libxatracker2:amd64 (10.1.3-0ubuntu0.6) over (10.1.3-0ubuntu0.5) ...
Preparing to unpack .../apt-utils_1.0.1ubuntu2.11_amd64.deb ...
Unpacking apt-utils (1.0.1ubuntu2.11) over (1.0.1ubuntu2.10) ...
Preparing to unpack .../apt-transport-https_1.0.1ubuntu2.11_amd64.deb ...
Unpacking apt-transport-https (1.0.1ubuntu2.11) over (1.0.1ubuntu2.10) ...
Preparing to unpack .../bind9-host_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking bind9-host (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../dnsutils_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking dnsutils (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../libisc95_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking libisc95 (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../libdns100_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking libdns100 (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../libisccc90_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking libisccc90 (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../libisccfg90_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking libisccfg90 (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../liblwres90_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking liblwres90 (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../libbind9-90_1%3a9.9.5.dfsg-3ubuntu0.7_amd64.deb ...
Unpacking libbind9-90 (1:9.9.5.dfsg-3ubuntu0.7) over (1:9.9.5.dfsg-3ubuntu0.6) ...
Preparing to unpack .../rsync_3.1.0-2ubuntu0.2_amd64.deb ...
Unpacking rsync (3.1.0-2ubuntu0.2) over (3.1.0-2ubuntu0.1) ...
Preparing to unpack .../apache2-mpm-prefork_2.4.7-1ubuntu4.9_amd64.deb ...
Unpacking apache2-mpm-prefork (2.4.7-1ubuntu4.9) over (2.4.7-1ubuntu4.8) ...
Preparing to unpack .../apache2_2.4.7-1ubuntu4.9_amd64.deb ...
Unpacking apache2 (2.4.7-1ubuntu4.9) over (2.4.7-1ubuntu4.8) ...
Preparing to unpack .../apache2-bin_2.4.7-1ubuntu4.9_amd64.deb ...
Unpacking apache2-bin (2.4.7-1ubuntu4.9) over (2.4.7-1ubuntu4.8) ...
Preparing to unpack .../apache2-data_2.4.7-1ubuntu4.9_all.deb ...
Unpacking apache2-data (2.4.7-1ubuntu4.9) over (2.4.7-1ubuntu4.8) ...
Preparing to unpack .../apache2-utils_2.4.7-1ubuntu4.9_amd64.deb ...
Unpacking apache2-utils (2.4.7-1ubuntu4.9) over (2.4.7-1ubuntu4.8) ...
Preparing to unpack .../apache2.2-bin_2.4.7-1ubuntu4.9_amd64.deb ...
Unpacking apache2.2-bin (2.4.7-1ubuntu4.9) over (2.4.7-1ubuntu4.8) ...
Preparing to unpack .../libecryptfs0_104-0ubuntu1.14.04.4_amd64.deb ...
Unpacking libecryptfs0 (104-0ubuntu1.14.04.4) over (104-0ubuntu1.14.04.3) ...
Preparing to unpack .../ecryptfs-utils_104-0ubuntu1.14.04.4_amd64.deb ...
Unpacking ecryptfs-utils (104-0ubuntu1.14.04.4) over (104-0ubuntu1.14.04.3) ...
Preparing to unpack .../indicator-applet-complete_12.10.2+14.04.20140403-0ubuntu1_amd64.deb ...
Unpacking indicator-applet-complete (12.10.2+14.04.20140403-0ubuntu1) over (0.5.0-0ubuntu1) ...
Preparing to unpack .../libgpod-common_0.8.3-4ubuntu3_amd64.deb ...
Unpacking libgpod-common (0.8.3-4ubuntu3) over (0.8.2-4) ...
Preparing to unpack .../libxml2-utils_2.9.1+dfsg1-3ubuntu4.7_amd64.deb ...
Unpacking libxml2-utils (2.9.1+dfsg1-3ubuntu4.7) over (2.9.1+dfsg1-3ubuntu4.6) ...
Preparing to unpack .../linux-firmware_1.127.20_all.deb ...
Unpacking linux-firmware (1.127.20) over (1.127.19) ...
Preparing to unpack .../linux-libc-dev_3.13.0-76.120_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-76.120) over (3.13.0-74.118) ...
Preparing to unpack .../os-prober_1.63ubuntu1.1_amd64.deb ...
Unpacking os-prober (1.63ubuntu1.1) over (1.63ubuntu1) ...
Preparing to unpack .../poppler-utils_0.24.5-2ubuntu4.3_amd64.deb ...
Unpacking poppler-utils (0.24.5-2ubuntu4.3) over (0.18.4-1ubuntu3.1) ...
Preparing to unpack .../python-libxml2_2.9.1+dfsg1-3ubuntu4.7_amd64.deb ...
Unpacking python-libxml2 (2.9.1+dfsg1-3ubuntu4.7) over (2.9.1+dfsg1-3ubuntu4.6) ...
Preparing to unpack .../python-smbc_1.0.14.1-0ubuntu2_amd64.deb ...
Unpacking python-smbc (1.0.14.1-0ubuntu2) over (1.0.13-0ubuntu1) ...
Preparing to unpack .../upower_0.9.23-2ubuntu1_amd64.deb ...
Unpacking upower (0.9.23-2ubuntu1) over (0.9.15-3git1ubuntu0.1) ...
Preparing to unpack .../usbmuxd_1.0.8-2ubuntu1_amd64.deb ...
Unpacking usbmuxd (1.0.8-2ubuntu1) over (1.0.7-2ubuntu0.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
WARN: Duplicate profile 'Apache', using last found
WARN: Duplicate profile 'Apache Secure', using last found
WARN: Duplicate profile 'Apache Full', using last found
Setting up libapt-inst1.5:amd64 (1.0.1ubuntu2.11) ...
Setting up libcurl3-gnutls:amd64 (7.35.0-1ubuntu2.6) ...
Setting up libcurl3:amd64 (7.35.0-1ubuntu2.6) ...
Setting up libcurl3-nss:amd64 (7.35.0-1ubuntu2.6) ...
Setting up libgl1-mesa-dri:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libgbm1:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libglapi-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libgl1-mesa-glx:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libegl1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libwayland-egl1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libopenvg1-mesa:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libegl1-mesa-drivers:amd64 (10.1.3-0ubuntu0.6) ...
Setting up libgpod4:amd64 (0.8.3-4ubuntu3) ...
Setting up mysql-client-core-5.5 (5.5.47-0ubuntu0.14.04.1) ...
Setting up mysql-client-5.5 (5.5.47-0ubuntu0.14.04.1) ...
Setting up mysql-server-core-5.5 (5.5.47-0ubuntu0.14.04.1) ...
Setting up mysql-server-5.5 (5.5.47-0ubuntu0.14.04.1) ...
mysql start/running, process 10352
Setting up mysql-server (5.5.47-0ubuntu0.14.04.1) ...
Setting up mysql-client (5.5.47-0ubuntu0.14.04.1) ...
Setting up libmysqlclient18:amd64 (5.5.47-0ubuntu0.14.04.1) ...
Setting up libmysqlclient-dev (5.5.47-0ubuntu0.14.04.1) ...
Setting up libsane-common (1.0.23-3ubuntu3.1) ...
Setting up libsane:amd64 (1.0.23-3ubuntu3.1) ...
Installing new version of config file /etc/sane.d/xerox_mfp.conf ...
Installing new version of config file /etc/sane.d/genesys.conf ...
Installing new version of config file /etc/sane.d/dll.conf ...
Installing new version of config file /etc/sane.d/gt68xx.conf ...
Installing new version of config file /etc/sane.d/fujitsu.conf ...
Setting up libxatracker2:amd64 (10.1.3-0ubuntu0.6) ...
Setting up apt-utils (1.0.1ubuntu2.11) ...
Setting up apt-transport-https (1.0.1ubuntu2.11) ...
Setting up libisc95 (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up libdns100 (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up libisccc90 (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up libisccfg90 (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up libbind9-90 (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up liblwres90 (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up bind9-host (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up dnsutils (1:9.9.5.dfsg-3ubuntu0.7) ...
Setting up rsync (3.1.0-2ubuntu0.2) ...
update-rc.d: warning: default stop runlevel arguments (0 1 6) do not match rsync Default-Stop values (none)
 System start/stop links for /etc/init.d/rsync already exist.
 * Restarting rsync daemon rsync                                           [ OK ]
Setting up apache2-bin (2.4.7-1ubuntu4.9) ...
Setting up apache2-data (2.4.7-1ubuntu4.9) ...
Setting up apache2 (2.4.7-1ubuntu4.9) ...
 * Restarting web server apache2                                           [ OK ]
Setting up apache2-mpm-prefork (2.4.7-1ubuntu4.9) ...
Setting up apache2-utils (2.4.7-1ubuntu4.9) ...
Setting up apache2.2-bin (2.4.7-1ubuntu4.9) ...
Setting up libecryptfs0 (104-0ubuntu1.14.04.4) ...
Setting up ecryptfs-utils (104-0ubuntu1.14.04.4) ...
Setting up indicator-applet-complete (12.10.2+14.04.20140403-0ubuntu1) ...
Setting up libgpod-common (0.8.3-4ubuntu3) ...
Setting up libxml2-utils (2.9.1+dfsg1-3ubuntu4.7) ...
Setting up linux-firmware (1.127.20) ...
Setting up linux-libc-dev:amd64 (3.13.0-76.120) ...
Setting up os-prober (1.63ubuntu1.1) ...
Setting up poppler-utils (0.24.5-2ubuntu4.3) ...
Setting up python-libxml2 (2.9.1+dfsg1-3ubuntu4.7) ...
Setting up python-smbc (1.0.14.1-0ubuntu2) ...
Setting up upower (0.9.23-2ubuntu1) ...
Installing new version of config file /etc/dbus-1/system.d/org.freedesktop.UPower.conf ...
Installing new version of config file /etc/UPower/UPower.conf ...
Setting up usbmuxd (1.0.8-2ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
```

free -m

```
             total       used       free     shared    buffers     cached
Mem:           741        639        101          0         40        369
-/+ buffers/cache:        229        511
Swap:         2188          1       2187

```

I seem to be working.  Anything else I should be considering/checking?

---

### Post by Bashing-om on 2016-01-30
Eddy Gordo from Tekken; Hey Hey ..


You done good !
Yeah ... 
> 
I seem to be working. Anything else I should be considering/checking?


Looking good .. take a look and consider carefully - as the package manager advises - 
```

sudo apt-get autoremove

```
that is a large list of things the system thinks is no longer required . But when done will free up a lot of disk space , and maybe put the package manager in a better state of mind .

[INDENT]a bit of spit and polish
[/INDENT]

---

