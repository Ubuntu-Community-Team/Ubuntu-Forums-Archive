---
title: "Remote desktop - i'm tired, please help"
date: 2010-02-17
forum: Server Platforms
---

### Post by battery360 on 2010-02-17
Ok so I've got an old p3 with 11 ide hard drives strapped to it for storage and I decided to throw Ubuntu server on it because it's more lightweight than a standard ubuntu install, and given it's a pentium 3 with 128mb of ram, lightweight is good.

I installed, through putty (ssh), the gnome gui - then learned that putty only does cli (i was thrilled), so I've spend the last hour trying to figure out how to enable remote desktop.

I don't mind reinstalling to do what is necessary. Here's what I want:
1) remote desktop to manage file downloads from my windows 7 machine(s)

big list, i know.

history: this thing is/was my media server. I had xp on it, sharing all drives and watching hd movies off it, but then xp decided it did't want to boot anymore so here we are. I'm thinking of just putting ubuntu 8.04/8.10 on it and through its wonderful gui enabling remote desktop and using realvnc/tightvnc to access it

THANKS IN ADVANCE. 5 RUPEES TO THE FIRST PERSON TO SOLVE THIS PROBLEM! (i'm lying, theres no reward.)

---

### Post by bluefrog on 2010-02-17
ubuntu server. no GUI unless you install one, which means you will eat your 128 Mb.

command line only. time to learn.

you can access your server via sftp program though which should let you manage your files from windows. Most windows ftp program should be able to do sftp as well.

---

### Post by japsai on 2010-02-17
VNC can be installed over cli:

```
sudo apt-get install tightvncserver
```

then start a session like this:

```
tightvncserver
```

Then you can access it from a client (e.g. on your win 7) by its IP:number where number is the code it returns when your start a session.

---

### Post by Porter200el on 2010-02-17
> **battery360 said:**
> Ok so I've got an old p3 with 11 ide hard drives strapped to it for storage and I decided to throw Ubuntu server on it because it's more lightweight than a standard ubuntu install, and given it's a pentium 3 with 128mb of ram, lightweight is good.

I installed, through putty (ssh), the gnome gui - then learned that putty only does cli (i was thrilled), so I've spend the last hour trying to figure out how to enable remote desktop.

I don't mind reinstalling to do what is necessary. Here's what I want:
1) remote desktop to manage file downloads from my windows 7 machine(s)

big list, i know.

history: this thing is/was my media server. I had xp on it, sharing all drives and watching hd movies off it, but then xp decided it did't want to boot anymore so here we are. I'm thinking of just putting ubuntu 8.04/8.10 on it and through its wonderful gui enabling remote desktop and using realvnc/tightvnc to access it

THANKS IN ADVANCE. 5 RUPEES TO THE FIRST PERSON TO SOLVE THIS PROBLEM! (i'm lying, theres no reward.)

You could install Webmin, that gives you a web interface to manage the server, but from what you are describing, I would suggest installing FreeNas if you want a straight up file server, Ubuntu can do it as well, but FreeNas is a bit easier to implement for that specific purpose.

---

### Post by battery360 on 2010-02-17
The purpose of this machine is to sit in my basement and hold data, but also to download new stuff - thus my need for a gui. I suppose it could be done through commandline but it's such a pain in the *** managing multiple server and torrent downloads from commandline, for me. It doesnt have to be pretty but I'd like a cursor.
Does freenas have any good torrent apps? I've heard of it, but never used or even seen it before.

---

### Post by pirateghost on 2010-02-17
> **battery360 said:**
> The purpose of this machine is to sit in my basement and hold data, but also to download new stuff - thus my need for a gui. I suppose it could be done through commandline but it's such a pain in the *** managing multiple server and torrent downloads from commandline, for me. It doesnt have to be pretty but I'd like a cursor.
Does freenas have any good torrent apps? I've heard of it, but never used or even seen it before.
yes, it has a torrent downloader built into it.  it is extremely easy to use.

---

### Post by gobbledigook on 2010-02-17
for a basic fileserver you really don't need a desktop. The cli is fun to use, great and very educational :) set up samba and you can share across your network, cross-platform (linux, xp, vista, 7, mac... etc)

for downloading torrents i use utorrent and wine, mainly because i'm just comfortable with it and like the interface. You can set it up to have a webui and scan a specific folder for .torrent files and add them to the queue. I use tightvncserver to start a basic desktop with fluxbox to start utorrent... a little complicated but i don't need to reboot very often so it just works :)

for usenet i use sabnzbd+ which only has a webui and can scan a folder for .nzb files (i have the same folder for .nzb and .torrent) this has a daemon you can enable on start-up

---

### Post by pirateghost on 2010-02-17
have a look at [Torrentflux - b4rt Home Page - A BitTorrent and Internet Transfer ...](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CDUQFjAA&url=http%3A%2F%2Ftf-b4rt.berlios.de%2F&ei=0UV8S6K0MI6oNt3T8cIF&usg=AFQjCNFwePKtUXccr-g6eKji-LXxOIu3mQ) if the commandline doesnt scare you away(only needed to configure it once)

---

### Post by battery360 on 2010-02-17
k well i installed the ubuntu-desktop package and tightvncserver, now how can I access it from my win7 machine? i installed the tightvnc viewer on it but it just says failed to connect when i try to.
also i have 11 hard drives connected to the box but it only mounted the one - they all worked on xp. I'm really considering going back to xp given the, ya know, ease.

---

### Post by pirateghost on 2010-02-17
> **battery360 said:**
> k well i installed the ubuntu-desktop package and tightvncserver, now how can I access it from my win7 machine? i installed the tightvnc viewer on it but it just says failed to connect when i try to.
also i have 11 hard drives connected to the box but it only mounted the one - they all worked on xp. I'm really considering going back to xp given the, ya know, ease.
you are over complicating things.

first of all, your lack of ram is going to give you a huge headache for a gui.  period.

1. what is your ultimate goal?
-fileserver
-downloader

2. how to administer the server?
-webgui would be ideal in this situation given a)your lack of ram to handle gnome and b)for a server a desktop gui is not needed.  once its setup, thats it.

3. what do you want your layout (shares, downloads, etc) to look like when you browse them from another machine?
-i would recommend setting up linux raid and utilizing LVM to 'combine' your space to an expandable share so that you only have to present one share via samba and everything is located under that one share.  other people might prefer a different share for every type of folder you might have on the share (docs, apps, music, movies, pics, etc)

if you jump into this without planning you will get frustrated and fall right back to windows, because you think its too complicated.  its not really that complicated, but it takes some patience and education (you will need to do some reading and understand what you are doing)  it sounds like you are already heading down that path, based on your last post.  you are hastily trying to configure this and not realizing, that you are configuring the wrong thing (desktop gui is not going to assist you in setting up your server, this isnt windows).  get the functionality up and running first.  take your time and learn

---

### Post by battery360 on 2010-02-17
to quote myself:
> Here's what I want:
1) remote desktop to manage file downloads from my windows 7 machine(s)

1. what is your ultimate goal?
downloader

2. how to administer the server?
the computer will run headless so it will be admined remotely via either a gui or webgui.
from what i've seen the gui is responsive at 800x600 if that counts for anything.

3. what do you want your layout (shares, downloads, etc) to look like when you browse them from another machine?
well i just shared all the hard drives through the network when it had xp on it. 10 hard drives (9x250gb + 1x320gb) all ntfs all full of data. atm my major concern is just being able to access the drives. Down the line I may but a few 1tb drives and move everything to them and lraid the 250's.
one step at a time: I want to be able to mount the drives, as I said xp failed on me so the drives didn't shut down properly, says the error I get when I tried to mount. How can I force mount my drives? I need to be walked through this as opposed to 'read man mount'

I'm trying to not be hasty, but at the same time I want this up and running asap as I've depleted all my free disk space on my other computers and crippled one still have a good 100gb of disk space on one of the 250's.

---

### Post by pirateghost on 2010-02-17
> **battery360 said:**
> to quote myself:


1. what is your ultimate goal?
downloader

2. how to administer the server?
the computer will run headless so it will be admined remotely via either a gui or webgui.
from what i've seen the gui is responsive at 800x600 if that counts for anything.

3. what do you want your layout (shares, downloads, etc) to look like when you browse them from another machine?
well i just shared all the hard drives through the network when it had xp on it. 10 hard drives (9x250gb + 1x320gb) all ntfs all full of data. atm my major concern is just being able to access the drives. Down the line I may but a few 1tb drives and move everything to them and lraid the 250's.
one step at a time: I want to be able to mount the drives, as I said xp failed on me so the drives didn't shut down properly, says the error I get when I tried to mount. How can I force mount my drives? I need to be walked through this as opposed to 'read man mount'

I'm trying to not be hasty, but at the same time I want this up and running asap as I've depleted all my free disk space on my other computers and crippled one still have a good 100gb of disk space on one of the 250's.

well, here is where you ignore the GUI that you are so adamant about:
drop to a command line
```
sudo apt-get update
``````
sudo apt-get install ntfs-3g ntfsprogs ntfs-config
``````
sudo fdisk -l
```thats a lowercase L not a 1 or I.  this will list the drive letters you will need following the next step
```
sudo mkdir /mnt/drive1 /mnt/drive2 /mnt/drive3 /mnt/drive4 /mnt/drive5 /mnt/drive6 /mnt/drive7 /mnt/drive8 /mnt/drive9 /mnt/drive10
``` you can substitute these for whatever you want them to be called
```
sudo mount /dev/sdb1 /mnt/drive1 -t ntfs
```rinse and repeat this step for every drive you need to mount

that should mount all the drives

---

### Post by battery360 on 2010-02-17
ah here lies the problem, 4 of the drives are in 2 jbod arrays (2 per array)

also given that i've followed multiple guides on the whole gui thing and installed all sorts of gnome crap, should I do a reinstall or is there a way of curbing EVERYTHING i've installed so that all that's left is the base install?

---

### Post by pirateghost on 2010-02-17
> **battery360 said:**
> ah here lies the problem, 4 of the drives are in 2 jbod arrays (2 per array)




now this might be where the speedbump is.  you had a JBOD set up in windows?  do all these drives have data on them?

---

### Post by battery360 on 2010-02-17
```
battery360@P3:~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01010101

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         255     2048256   a7  NeXTSTEP
/dev/sda2             256        2491    17960670    5  Extended
/dev/sda5             256        2445    17591143+  83  Linux
/dev/sda6            2446        2491      369463+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61e9fc24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe57ce6a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       61031   490231476    7  HPFS/NTFS

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

Disk /dev/sdd doesn't contain a valid partition table
```
I forced a mount of sdb1 and it said:
```
battery360@P3:~$ sudo mount /dev/sdb1 /mnt/external -t ntfs -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
```

indeed the two jbod array have data on them, infact they're full.
i've got an empty 500gb hard drive, i could if i must pass the data to the 500 gigger then wipe the two 250's and put the data back on them as individual drives (not part of an array).

i should mention 2 hard drives are not actually connected as I needed to attack an ide cd drive. so thats 9 hard drives physically connected, only 4 are seen, discuss.

How they're all connected:
first ide channel on the mobo holds the 20gb os disk and one 250gb data drive
second ide channel on the mobo holds the cd drive, used to hold 2 x 250gb data drives

via 6421 accommodated 2x250 ide drives and 1x320gb sata drive

other pci ide card that i got off ebay for $10 holds 4x250gb

---

### Post by pirateghost on 2010-02-17
> **battery360 said:**
> 
i should mention 2 hard drives are not actually connected as I needed to attack an ide cd drive. so thats 9 hard drives physically connected, only 4 are seen, discuss.

what controller card do you have them connected to?

---

### Post by battery360 on 2010-02-17
> **pirateghost said:**
> what controller card do you have them connected to?
relevant info from lspci:
```
00:0a.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
00:0b.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
```

---

### Post by pirateghost on 2010-02-17
you may need to install dmraid 
sudo apt-get install dmraid

---

### Post by battery360 on 2010-02-17
installed:
```
battery360@P3:~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01010101

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         255     2048256   a7  NeXTSTEP
/dev/sda2             256        2491    17960670    5  Extended
/dev/sda5             256        2445    17591143+  83  Linux
/dev/sda6            2446        2491      369463+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61e9fc24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe57ce6a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       61031   490231476    7  HPFS/NTFS

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/dm-0: 502.0 GB, 502000385024 bytes
255 heads, 63 sectors/track, 61031 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe57ce6a3

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1       61031   490231476    7  HPFS/NTFS

Disk /dev/dm-1: 501.9 GB, 501997031424 bytes
255 heads, 63 sectors/track, 61030 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```
ok so those two ~500gb drives are two jbod arrays, do I force mount them like you said a few posts ago?

---

### Post by pirateghost on 2010-02-17
sudo dmraid -r y
sudo dmraid -s

---

### Post by battery360 on 2010-02-17
if ya don't mind my asking, what do they do?
guess i'll find out as I absentmindedly copy and paste.

edit: looked it up in man dmraid
the output of the two:
```
battery360@P3:~$ sudo dmraid -r
/dev/sdd: via, "via_ejaaibjfg", linear, ok, 490234751 sectors, data@ 0
/dev/sdc: via, "via_ejaaibjfg", linear, ok, 490234751 sectors, data@ 0
battery@P3:~$ sudo dmraid -s
*** Active Set
name   : via_ejaaibjfg
size   : 980469488
stride : 8
type   : linear
status : ok
subsets: 0
devs   : 2
spares : 0

```

---

### Post by pirateghost on 2010-02-17
lol.  you didnt want to read man pages, but [http://linuxmanpages.com/man8/dmraid.8.php](http://linuxmanpages.com/man8/dmraid.8.php)

---

### Post by battery360 on 2010-02-18
so.. now what? do I force mount them?
how about sharing them with my windows comps?

---

### Post by pirateghost on 2010-02-18
> **battery360 said:**
> so.. now what? do I force mount them?
how about sharing them with my windows comps?
what was the status of sudo dmraid -a y ?

---

### Post by battery360 on 2010-02-18
RAID set "via_ejaaibjfg" already active
RAID set "via_ejaaibjfg1" already active

---

### Post by pirateghost on 2010-02-18
> **battery360 said:**
> RAID set "via_ejaaibjfg" already active
RAID set "via_ejaaibjfg1" already active


sudo mount -t ntfs /dev/mapper/via_ejaaibjfg1 /mnt/drive1 (or whatever path you want to mount)

once that is done, you will need to configure samba to share that mount path.  make sure the workgroup that samba is set up with is in the same workgroup as the rest of your machines on your network

---

### Post by battery360 on 2010-02-18
ok so I'll do:
sudo mount -t ntfs /dev/mapper/via_ejaaibjfg /mnt/array1
sudo mount -t ntfs /dev/mapper/via_ejaaibjfg1 /mnt/array2

ok i've heard of samba. all I can do is squak 'ima n00b! ima n00b! polly wanna command'

---

### Post by pirateghost on 2010-02-18
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
pay attention to 
Samba Server Configuration -  Manual

---

### Post by battery360 on 2010-02-18
awesome.
so I gave this a shot: ```
sudo mount -t ntfs /dev/mapper/via_ejaaibjfg /mnt/array1
``` and got
```
NTFS signature is missing.
Failed to mount '/dev/mapper/via_ejaaibjfg': Invalid argument
The device '/dev/mapper/via_ejaaibjfg' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

---

### Post by battery360 on 2010-02-18
my bad, double post

---

### Post by pirateghost on 2010-02-18
> **battery360 said:**
> awesome.
so I gave this a shot: ```
sudo mount -t ntfs /dev/mapper/via_ejaaibjfg /mnt/array1
``` and got
```
NTFS signature is missing.
Failed to mount '/dev/mapper/via_ejaaibjfg': Invalid argument
The device '/dev/mapper/via_ejaaibjfg' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```


because you can only mount partitions and not the whole drive.

sudo mount -t ntfs /dev/mapper/via_ejaaibjfg1 /mnt/array1

---

### Post by battery360 on 2010-02-18
> **pirateghost said:**
> because you can only mount partitions and not the whole drive.

sudo mount -t ntfs /dev/mapper/via_ejaaibjfg1 /mnt/array1

argggghhh

```
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/mapper/via_ejaaibjfg1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

---

### Post by The Real Dave on 2010-02-18
> **Porter200el said:**
> You could install Webmin, that gives you a web interface to manage the server, but from what you are describing, I would suggest installing FreeNas if you want a straight up file server, Ubuntu can do it as well, but FreeNas is a bit easier to implement for that specific purpose.

+1 for FreeNAS if you want an easy to configure GUI interface that will still work on 128Mb of RAM. Gnome, just won't :)

Either that or learn how to do what you want through CLI. It's not that hard :)

---

### Post by pirateghost on 2010-02-18
It appears, with that error, that the way you have the drives setup have locked you into Windows until you can get your data moved off those drives and reconfigure them properly.  FYI, JBOD is a bad idea if the data is important to you.

---

### Post by battery360 on 2010-02-18
would freenas save me the trouble of having to backup and reformat the drives?

edit: screw it I never like the jbod arrays to begin with. I'll just reform the drives.. all three jbod arrays. My first array constantly threw file system errors, every second boot required a chkdsk run.

another edit: what file system should I format the new drives? I heard XFS was good for media servers, then again I've never really had an issue with ntfs (that a quick run of chkdsk couldnt fix, but this isn't windows any more..). Perhaps the default ext3?
*sigh* windows 7 disk manager only allows for ntfs

---

### Post by battery360 on 2010-02-18
ok assuming I get all that patched up and mounted properly, in terms of managing my downloads, what clients would you suggest? I download primarily from IPTorrents and Megashares. I'd like a webgui of some kind or to be able to ssh into my comp remotely to check the status of my downloads and to start new ones.

---

### Post by pirateghost on 2010-02-18
> **battery360 said:**
> ok assuming I get all that patched up and mounted properly, in terms of managing my downloads, what clients would you suggest? I download primarily from IPTorrents and Megashares. I'd like a webgui of some kind or to be able to ssh into my comp remotely to check the status of my downloads and to start new ones.

in reference to your prior question, i typically go with ext3, although my old fileserver had xfs...really it wont matter

i cant say enough about [http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)

it takes a little bit of setup time, but in the end you get a webgui based torrent/newsgroup/wget downloader.  set it up right and you can have access to it from anywhere in the world.

[http://ubuntuforums.org/showthread.php?t=848138](http://ubuntuforums.org/showthread.php?t=848138) shows you how to set it up.  you will need to make sure you have apache, mysql, and php installed prior, but you may have done all that when you installed the OS if you selected LAMP server.

it may seem overwhelming at first, but really its not that difficult.  just go slow and follow the steps.

if you decide that all that may be too difficult, have a serious look at FreeNAS.  you dont have to do any command line stuff, but is a little more limited in that aspect.  all you get is a webgui to configure from, but it is nicely polished and refined.  it has a torrent downloader in it, you can configure a folder for it to watch and when it sees a .torrent file in that folder it will begin downloading automatically.  good stuff, and if all you really need is storage/itunes streaming/upnp/torrentdownloader server, that would be the EASIEST way to go about it.

---

### Post by battery360 on 2010-02-18
I'm thinking of doing a fresh install of 8.04 server and installing all the neccessary junk (and LAMP). Reason I want to do this is because I installed gnmore and all that other crap.
Should I bother, or should I just leave it there?
Any comments on webmin?

Given that win7 only allowed me to format to ntfs, I'd have to move that ntfs drive over to my fileserver then format the newly un-jboded drives to ext3 then spend another **6 hours** transfering the 463gb of junk on it.
Are there any major downsides to keeping all the drives on ntfs?

I'll give torrentflux and install - looks good.
edit: oh is there any way of using an ssh tunnel to access torrentflux?

---

### Post by pirateghost on 2010-02-18
> **battery360 said:**
> I'm thinking of doing a fresh install of 8.04 server and installing all the neccessary junk (and LAMP). Reason I want to do this is because I installed gnmore and all that other crap.
Should I bother, or should I just leave it there?
Any comments on webmin?

Given that win7 only allowed me to format to ntfs, I'd have to move that ntfs drive over to my fileserver then format the newly un-jboded drives to ext3 then spend another **6 hours** transfering the 463gb of junk on it.
Are there any major downsides to keeping all the drives on ntfs?

I'll give torrentflux and install - looks good.
edit: oh is there any way of using an ssh tunnel to access torrentflux?
starting fresh would likely be a good thing.

wow, 6 hours for 463gb?  100mbps network?

downside to ntfs from what i have seen using it in linux is the CPU usage.  i noticed considerably high CPU usage while writing to ntfs, but that has been a while since i messed with ntfs+linux

you can ssh into the box regardless of torrentflux.  can you elaborate on what you mean by that?

---

### Post by battery360 on 2010-02-18
> **pirateghost said:**
> starting fresh would likely be a good thing.

wow, 6 hours for 463gb?  100mbps network?

downside to ntfs from what i have seen using it in linux is the CPU usage.  i noticed considerably high CPU usage while writing to ntfs, but that has been a while since i messed with ntfs+linux

you can ssh into the box regardless of torrentflux.  can you elaborate on what you mean by that?
I moved one of the arrays and one spare 500gb hard drive to another computer - the transfer is not over the network.
As long as the system can keep up with a constant 10mbps of data I don't too much care for the cpu usage.
elaborating: creating a ssh tunnel to access the torrentflux ui
sort of like: [http://tf-b4rt.berlios.de/forum/index.php?topic=1061.0;wap2](http://tf-b4rt.berlios.de/forum/index.php?topic=1061.0;wap2)

---

### Post by pirateghost on 2010-02-18
> **battery360 said:**
> I moved one of the arrays and one spare 500gb hard drive to another computer - the transfer is not over the network.
As long as the system can keep up with a constant 10mbps of data I don't too much care for the cpu usage.
elaborating: creating a ssh tunnel to access the torrentflux ui
you could set something up like an ssl vpn to connect to the webgui, or if you have another machine on the network, you could tunnel into it and use the web browser on that machine.

personally, i prefer openvpn.  i vpn into my network and do all the stuff i need without exposing everything to the outside world.

---

### Post by battery360 on 2010-02-18
ok I've managed to back up the contents of one of my arrays, and I just read about a way to give windows the ability to work with ext2/3 filesystems. So would it be good to mix and match ntfs and ext3 drives in the same box, should I just stick with ntfs or move all my data to ext3?
A quick response would be ideal due to the sheer quantity of data I need to move.

---

### Post by pirateghost on 2010-02-19
personally, i chose to never go back to windows for my fileshares.  if i change my mind in the future i will utilize iscsi and still keep my linux box full of disks.  thats a tough decision because only you know whether or not you want to commit.

---

### Post by battery360 on 2010-02-19
I have no problem keeping this box running linux and I've gotten comfortable with the idea of managing it with cli or a webui so..
whatever works - basically this box holds a whole bunch of high definition videos that I watch from other computer that can actually decode them. I'd like this box to be low maintenance - I just want to watch movies off it and download new ones.

So is Ubuntu happier with ext3 or does it not care.
Given that win 7, with a minor tweak, can use ext3 I don't really care. I just want ease and stability (and maximum uptime).

---

### Post by pirateghost on 2010-02-19
i would go with ext3 then

---

### Post by battery360 on 2010-02-21
ok the transition of ext3 has not been going well. So I threw in a 9.04 live cd to format the drives two 250gb hard drives to ext3. Booted to win7, tried to give it read/write access to ext3 via ext2ifs, detected the drives but said they were corrupt - gave up on that. Moved the 2 250's and the 500 ntfs with all my data on it to the server and it doesnt detect the 250's and says the 500gb drive has a ~127mb patrition and the rest is all free space.
What the hell.

---

### Post by pirateghost on 2010-02-21
why are you putting these drives into a win7 box, or trying to make win7 read ext3?

---

### Post by battery360 on 2010-02-21
I used to win7 box to back up the 2x250 on the 500gb hard drive.
I figured if I could give the win7 box read/write access to the freshly ext3'd drives I could transfer the files back without having to move the drives or use a live cd

Update: connected the 250's to my win7 box and deleted their partitions: I plan to format them to ext3 in my server box. Any idea why the ntfs 500gb drive is not being read properly? it says it has a 128mb unknown primary partition and that the rest if free space (gparted), but fdisk says the drive is ntfs

---

### Post by pirateghost on 2010-02-21
if you are using an older version of ubuntu - i think you said you were using 8.04?  did you install the ntfs stuff from earlier?

---

### Post by battery360 on 2010-02-21
8.04 is whats on my server
9.04 was used as a live cd on the win7 box
I haven't yet reformatted, so the ntfs package is still on the server. It says there's a 128mb unknown patrition and the rest is free space. I just hooked it up to my win 7 box and it's fine - all my files are there. Windows disk manager says it a basic mbr ntfs disk.

---

### Post by battery360 on 2010-02-21
I moved the drives from my 6410 to the 6421 and onboard ide ports and:
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2f5c9f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488383488    7  HPFS/NTFS

```
ok maybe I was wrong.. aparently the 500gb disk isn't mbr. Guide me!

---

### Post by pirateghost on 2010-02-21
that explains things a little better.  the 128mb partition is related to creating a GPT partition on the rest of it.  this should have no bearing on being able to mount that drive.

while you have it hooked up this way can you do a:
```
mount -t ntfs /dev/sdb1 /mnt/test
```

---

### Post by battery360 on 2010-02-21
kick ***! it worked!
when I had the two blank drives hooked up to the 6410 it just said no raid drives when I asked it to list. Any idea why? maybe I just did it wrong.. given that these two drives are now formatted to ext3 I'd like to move them over to the 6410 as the 6421 is easier to deal with..
Why doesn't the 6410 work natively like the 6421?

---

### Post by pirateghost on 2010-02-22
i am not very familiar with those ide cards, so i am not sure.  sorry.

i will do some research on it when i find time tomorrow at the office

---

### Post by battery360 on 2010-02-22
On second thought it may be best if I keep all the drives NTFS, I sometimes pull drives from my server and throw them into enclosures when I travel.
Also, I noticed when I formatted my drives to ext3 that there was only 219gb free (properties of the mount location), while gparted said there was 230gb free space.
Last night I tried to transfer the files back the the two drives, so I started the gui and selected 216GBs worth of data, but didn't have permission to copy the files over to the mounted location (mounted in /mnt/WD1). The reason I tried doing it through a gui was because the only way I know how do it with cli is with "cp file1 file2 file3 ... filen /mnt/WD1", which is a pain.
I'd like to set up a (s)ftp server so I can manage the files on the various drives from a remote location.
I've been able to log in as root from filezilla on my win7 box and mess with the files.

At my university pretty much all the common ports are blocked except 80 and 443 - how can I ssl to ssh into my system? I found [this]("http://dag.wieers.com/howto/ssh-http-tunneling/"); will this let me access my server from my university/elsewhere?

I really appreciate all the help you've given me.

---

### Post by battery360 on 2010-02-25
I installed torrentflux-b4rt but I'm having permission issues. I set b4rt's download destination to be /mnt/WD1, but it's owned by root and I can't seem to change that with:
chown -R www-data:www-data /mnt/WD1
any ideas? the Os disk is only 20gigs and no good for downloading to.

---

### Post by pirateghost on 2010-02-25
sorry, i missed your post from 2 days ago.

first copying multiple files to a destination
```
cp -Rpv /mnt/disk1/* /mnt/disk2
```-r or R means recursive (includes all subfolders)
-p is preserve mode/timestamps/ownership
-v will scroll the entire output while it is copying
* is a wildcard, it says that anything under /mnt/disk1/ no matter what it is, will be copied to disk2
this alleviates copying individual files by hand
some other options can be seen here
[http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm)

as far as SFTP, you already have it.  SSH.  snag a copy of WINSCP for your windows machines
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)
bam, graphical file management.  filezilla will also do SFTP (which is another term for ftp over ssh), but i prefer winscp.  just a personal preference.

getting into your home system?
i like VPN, much more secure than opening up SSH ports
i prefer OpenVPN, but the setup might be a little intimidating
[http://wiki.amahi.org/index.php/Adito](http://wiki.amahi.org/index.php/Adito) is a project that will allow you to use SSL VPN....handy stuff, and hak5 has a video on it.  not bad stuff, i will give it a shot one day.

permissions issues on torrentflux....try doing chmod -R 777 /mnt/WD1 and see if that helps (oh and dont forget that you need to sudo those commands).
sudo chown -R www-data:www-data /mnt/WD1
sudo chmod -R 777 /mnt/WD1
since my torrentflux is not available outside my network, i just 777 my entire download directory


i hope some of this helps get you on the path to mastering the server ;)


**edit**
i just remembered.  the reason that your drive is showing less space than it actually has is this:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
> **Modify Reserved Space  (Optional)**

 When  formatting the drive as ext2/ext3, 5% of the drive's total space is  reserved for the super-user (root) so that the operating system can  still write to the disk even if it is full. However, for disks that only  contain data, this is not necessary. 
NOTE: You  may run this command on a fat32 file system, but it will do nothing;  therefore, I highly recommend not running it. 
You can adjust the percentage of reserved space with the  "tune2fs" command, like this: 
 sudo tune2fs -m 1 /dev/sdb1This example reserves 1% of space - change this number  if you wish. 
[IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/icon-info.png[/IMG] Using this command does not change  any existing data on the drive. You can use it on a drive which already  contains data. 

---

### Post by battery360 on 2010-02-25
Well the thing is  I only want to move half the files to each drive. Will this command move as much as it can, or will is just say there's not enough disk space?

I punched in the ownership commands and it let me start a download! :KS

to set up torrentflux I followed [this]("http://server-servers.com/install-torrentflux-b4rt-on-ubuntu/") guide, but then that didn't work properly so I jump over to [this]("http://www.tbaumi.de/blog/?p=380") guide. The only thing I've noticed is that the download speeds are very slow (60-80kBps), though it may just be this torrent in particular. Which torrent client would you suggest I use (bittornado, transmission)? Also do you know of any tweak I can do to boost the transfer speeds?
Would you recommend [MoBlock]("http://www.fsckin.com/2007/09/27/do-you-use-linux-the-riaa-and-mpaa-dont-want-you-to-use-this-program/")?

Good to know about the reserved space for the su.
I'm having second thoughts about reformatting. It wouldn't be hard but given that everything seems to be working properly.. I've heard every server user say that gnome or and desktop ui is a security threat, but if I stop gdm does that fix the problem?

I've only got two ports forwarded to the server, 443 and my ssh port. Should I bump ssl to a different port?

Update: Ok my download speed has dropped to sub 40kBps and my upload speed is at 0kBps. I've never had issues with my isp regarding torrents, but how can I enable protocol encryption - and which clients support it? Also, how do I choose which client is used.

Update 2: After some screwing around with the settings, my download speed is now 170-180kBps, and my up is 70-90kBps. Still now the 1mBps I'm wanting, but I'll take what I can get. I'll try another torrent and update again.

---

### Post by battery360 on 2010-02-28
ok thing have been going pretty good. I've got 10 hard drives hooked up to the box now. With the gui in file browser it shows all the drives and their names, when I mount from command line how can I get it to display the names or the drives?

---

### Post by pirateghost on 2010-02-28
what do you mean the names of the drives?

---

### Post by CharlesA on 2010-02-28
Guessing he means the volume labels.

Easiest way is to figure out what designation each of them has. e.g., /dev/sdd1 /dev/sde1

---

### Post by battery360 on 2010-02-28
yea I meant volume labels, I have 10 identical 250gb drives and over the last week they've been moved several times. They're all ntfs and have different names (well different designations Maxtor1, Maxtor2...). When I enable the gui and open the file browser, on the left it shows all my drives with their proper volume labels. So I'm wondering how I can see that when I'm only using cli.

I'm having issues with my VT6410, when I do dmraid -ay dmraid -r it just says No Raid Disks, moving the drives to a different controller lets me access them. I read about a patch by Daniel Drake that added the VT6410 to the via82cxxx.c drivers - but its a bit over my head..

EDIT:
lshw -C storage gives:
```

PCI (sysfs)
  *-ide
       description: IDE interface
       product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
       vendor: VIA Technologies, Inc.
       physical id: 7.1
       bus info: pci@0000:00:07.1
       logical name: scsi0
       logical name: scsi1
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_via latency=64 module=pata_via
  *-storage:0 UNCLAIMED
       description: RAID bus controller
       product: VT6410 ATA133 RAID controller
       vendor: VIA Technologies, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: storage pm bus_master cap_list
       configuration: latency=64
  *-storage:1
       description: Mass storage controller
       product: PDC20268 (Ultra100 TX2)
       vendor: Promise Technology, Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: scsi3
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: storage pm bus_master cap_list emulated
       configuration: driver=pata_pdc2027x latency=64 maxlatency=18 mingnt=4 module=pata_pdc2027x

```

---

### Post by battery360 on 2010-03-01
Aside from the VT6410 my only other MAJOR issue is that I need a way to download from Megashares (a service like rapidshare - except no garbage download limits). I tried downloading a file through (cli) torrentflux and it said I had to log in. 
Been doing a bit of reading and found [this]("http://community.megashares.com/forum/showthread.php?p=182"). So I'm thinking of setting up wget webui so I can queue a bunch of files.

---

