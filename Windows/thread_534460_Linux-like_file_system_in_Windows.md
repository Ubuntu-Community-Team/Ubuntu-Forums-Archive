---
title: "Linux-like file system in Windows?"
date: 2007-08-25
forum: Windows
---

### Post by Ian505 on 2007-08-25
I was wondering if it is possible to set up windows like linux- have one partition for the actual system and a second partition for the actual data. I think that this would help me a lot because I have TONS of stuff on my computer and I would like to have everything separate so that I don't end up with a nice little blue screen. I would also like the data partition to be accessible from Linux if that is possible. I don't know what information you guys would need to determine if this is possible on my computer, so please tell me what you need and I will post.

If I can set this up so that all my files are accessible from BOTH Windows and Linux without hindrance- I will make a permanent move to Ubuntu Linux and keep Windows on my machine for everything else.

Thanks in advance.
-Ian

---

### Post by InGunsWeTrust on 2007-08-25
I need a little more info to know if it is truly possible. Are you just looking to have an install of each then all of your music, games, backups, etc go on another partition? or do you want to install all of your programs and stuff on the other partition as well?

In the case of the music and games Yes indeed it is possible and if that is the case I will be happy to give you a howto on that. However if you want to install programs to share that is just not possible because while you can use wine to execute windows programs on the shared partition Windows will be unable to read any binaries compiled for Linux. I'll subscribe to this thread and if you need the howto let me know, or if you just want more info about shared file systems I'd be happy to help.

---

### Post by Ian505 on 2007-08-25
I understand that it is impossible to have Linux run all Windows programs , and am only asking for a way to have all of the pics, games, video etc shared between both Windows and Ubuntu, so I would like your how to. :) Also I would like to be able to (as you mentioned before) run Windows programs that I can run from wine without having to install them on both OSes. 

So your description of what is possible is exactly what I would like:

[LIST]
[*]Shared images, documents, etc. on a seperate partition
[*]Videos on another partition.
[*]Each OS in its own partition (if possible)
[*]Ability to run Windows programs through WINE without having to install the programs on both OSes.
[/LIST]

I have 2 hard drives-

One is 80GB and currently is my main drive that contains Windows XP Pro and most of my stuff.There are actually 2 partitions on this drive (one is a restore partition by Dell) but I can't delete either because I cannot find my restore disk!

The other drive is 150GB and contains a ~80GB partition for video capture and editing (cant delete this also) and a  ~70GB partition for everything related to ubuntu. (The only deletable partition on my system.)
[B]
Your help is GREATLY appreciated![/B]

-Ian

EDIT- 
Ubuntu is currently NOT installed on my machine- except for a few VMs that I have. (Thats how I currently run Ubuntu.)

---

### Post by InGunsWeTrust on 2007-08-25
You may have to install programs on both OSes if they install important registry entries but that is about it. Most games and things of that nature write config files though so if you can get your games to work with wine then you wouldn't have to install those on both. But let's start anyway!

First thing, you said you have done a few VM installs with Ubuntu so you are probably familiar with Gparted (the partition editor) just let me know if you aren't cuz I can give some help on that too.

Make all of the partitions you need in Gparted before you start the installer as this will make things run more smoothly. I assume windows takes the whole drive at the moment so you will have to shrink that, make a partition for Ubuntu, the shared partition, and a swap partition. I know there are pre-existing partitions but I am sure you can figure out how to change and move and resize to your needs. Make the shared drive an NTFS drive. Next to enable writing to the NTFS drive open a terminal window and do this

```
sudo apt-get install ntfs-3g ntfs-config
```

Type Y for all of the prompts that come up

Then

```
ntfs-config
```

check both boxes and click OK

because you are on the live CD you will have to repeat this after the install to continue to be able to write to the NTFS drive.

After all of this is completed double click the installer and go through the install process until you reach the screen below (once again I'm assuming because you've done it before you are fairly familiar with the process but I can give more help if you need it).

[SceenShot Mentioned Above]("http://debianadmin.com/copper/displayimage.php?pid=753&fullsize=1")

(ignore the actual entries in the pictures I just googled that screen shot)

Make all of the necessary  entries / should be in the ext3 partition you created for Ubuntu swap should be in the swap partition mount your XP partion to /media/XP/ and mount the **share drive at /home/** that is very important because it is possible to change it later but very hard. After you are positive that all of the entries in the mounting screen are correct finish the installer. In Ubuntu you have a Home folder and in that home folder after the install you can create your own document folders like My Docs, Music, Video, Etc.

After the install you can install wine (once again you seem familiar with it so I assume you know how, but I can help with that).

Once wine is installed boot into windows and open regedit. Navigate to this key: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion] and change ProgramFilesDir too LetterOfTheShareDrive:\home\YourUbuntuUsername\.wine\drive_c\Program Files\

This will make it so by default programs will install to the share drive in the fake windows install that wine creates.

To make your documents in XP link to your share drive:

Right-click My Documents, and then click Properties. Click the Target tab. In the Target box, Type LetterOfTheShareDrive:\home\YourUbuntuUsername\My Docs
or whatever you name the folder you will put your documents into

The same process can be done to My Video, My Music, and other the other XP "My's" other than my computer I suppose.

I think that about covers the general process. If you need help with anything along the way just let me know.

---

### Post by Ian505 on 2007-08-25
No idea what Gparted is. :-( I have been using the Windows partitioner. 

Edit- Okay this is quite over my head... I made a Virtual Machine in innotek VirtualBox, set the Ubuntu CD as the Optical Drive then installed it into a virtual drive.


-Ian

---

### Post by InGunsWeTrust on 2007-08-25
No problem, haha The windows partition sucks big time compared to Gparted. On the live CD you can go to System > Administration > Gnome Partition Editor

Depending on the version of the CD you have it might simply be System > Administration Gparted

It is very graphical and thus easy to figure out but if you have any problems with that to there are all kinds of tutorials on Gparted around the forums.

---

### Post by Ian505 on 2007-08-25
Okay, so should I do this first by booting from the live CD or should I use the VM?

---

### Post by Cows on 2007-08-25
I'm positive that windows cannot read information that's on the linux partitions. The only way windows and linux can read data from the same partition would be to have a FAT or FAT32 partition. That's only to share information and not to have Windows and Linux to read and execute from the same parition. As "InGunsWeTrust" said, windows will not be able to read linux binaries. As for Gparted, it's just a partitioning tool, just "sudo aptitude install gparted", better yet boot up with the linux live cd and it will be under "System -> Administrator -> Gparted".

Also a tip is that if you have stuff that will be mounted, most likely this will be a annoyance, so to stop them from automatically mounting just go to "System -> Preferences -> Removable Drives and Media", uncheck the first 3 checks and press ok.

---

### Post by InGunsWeTrust on 2007-08-25
> **Cows said:**
> I'm positive that windows cannot read information that's on the linux partitions. The only way windows and linux can read data from the same partition would be to have a FAT or FAT32 partition. That's only to share information and not to have Windows and Linux to read and execute from the same parition. As "InGunsWeTrust" said, windows will not be able to read linux binaries. As for Gparted, it's just a partitioning tool, just "sudo aptitude install gparted", better yet boot up with the linux live cd and it will be under "System -> Administrator -> Gparted".

Also a tip is that if you have stuff that will be mounted, most likely this will be a annoyance, so to stop them from automatically mounting just go to "System -> Preferences -> Removable Drives and Media", uncheck the first 3 checks and press ok.

actually if you install NTFS-3G you can have it as NTFS

---

### Post by InGunsWeTrust on 2007-08-25
> **Ian505 said:**
> Okay, so should I do this first by booting from the live CD or should I use the VM?

Your VM will only be able to edit your virtual hard drive so you need to start from the live CD on your normal computer. You should still be able to access the internet from the Live CD to read the instructions

---

### Post by Ian505 on 2007-08-25
Okay let me pop that in then- I will be back in a few (will edit when back.)

-Ian

EDIT- Okay I am here and I have found GParted

---

### Post by Ian505 on 2007-08-25
Okay, I have found out how to resize the partitions and such but I don't know how big to make the Ubuntu Partition or the swap partition. I always let it do it automatically in the VM.:(

-Ian

---

### Post by InGunsWeTrust on 2007-08-25
> **Ian505 said:**
> Okay, I have found out how to resize the partitions and such but I don't know how big to make the Ubuntu Partition or the swap partition. I always let it do it automatically in the VM.:(

-Ian

Generally you want to make the swap partition about twice the size of your RAM and the Ubuntu partition should be about 5 gigs because the install will take about 1 gig but if you want to access all the cool features of Linux you could very easily fill up 4 more gigs. Keep in mind that with Gparted if you run out of space you can make it bigger later.

---

### Post by Ian505 on 2007-08-25
Just so you know, I am going to make 2 different 'Shared' partitions later- one on each drive.

-Ian

EDIT- Okay what file system does the swap partition use as well as Ubuntu? And whats 'Round to Cylinders' mean? Also, do I create it as a primary partition or an extended partition? I have a feeling that these are pretty basic questions, but see my signature. (And its only the past week I have decided to make the switch.)

---

### Post by InGunsWeTrust on 2007-08-25
> **Ian505 said:**
> Just so you know, I am going to make 2 different 'Shared' partitions later- one on each drive.

-Ian

That is fine but make sure the one that you want "My docs" to be on is mounted at /home/ The other one for the video editing or whatnot can be targeted for "My Video" In Windows and you can make a link In Linux too.

Also did you remember to install ntfs-config and ntfs-3g

---

### Post by Ian505 on 2007-08-25
> **InGunsWeTrust said:**
> That is fine but make sure the one that you want "My docs" to be on is mounted at /home/ The other one for the video editing or whatnot can be targeted for "My Video" In Windows and you can make a link In Linux too.

Also did you remember to install ntfs-config and ntfs-3g

Okay I tried to install using the commands you gave me but got this:
```

ubuntu@ubuntu:~$ sudo apt-get install ntfs-3g ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-3g
ubuntu@ubuntu:~$ 
```

Help!?

-Ian
[COLOR="Red"][B]
Also- did  you see my edit about filesystems above?[/COLOR][/B]

---

### Post by InGunsWeTrust on 2007-08-25
One moment it is probably in a repository that isn't on by defualt, I'll look which one it is then edit it into this post

Do this:

```
sudo synaptic
```

then go to Settings > Repositories

then click the Third Party Software tab and check all the boxes that are not checked

click close

then click the search button and enter ntfs-config

then mark ntfs-config for installation and it should automatically ask you about dependancies. Click Mark

Then click Apply

---

### Post by AnRa on 2007-08-25
> **Cows said:**
> I'm positive that windows cannot read information that's on the linux partitions. The only way windows and linux can read data from the same partition would be to have a FAT or FAT32 partition.That's not true: [Ext3 in Windows](http://gentoo-wiki.com/Ext3_in_windows). ;)

---

### Post by InGunsWeTrust on 2007-08-25
> **AnRa said:**
> That's not true: [Ext3 in Windows](http://gentoo-wiki.com/Ext3_in_windows). ;)

If this ntfs-3g thing doesn't work I may just suggest that, I didn't know there was such a thing. I just figure we better not confuse poor old windows with non-native file systems haha

---

### Post by Ian505 on 2007-08-25
Uhh... there isn't anything under Third-Party Software...

---

### Post by InGunsWeTrust on 2007-08-25
> **Ian505 said:**
> Uhh... there isn't anything under Third-Party Software...

Well that is a bit weird. Try 

```
sudo gedit /etc/apt/sources.list
```

post the contents of the file that comes up (if any)

---

### Post by Ian505 on 2007-08-25
> **InGunsWeTrust said:**
> Well that is a bit weird. Try 

```
sudo gedit /etc/apt/sources.list
```

post the contents of the file that comes up (if any)

```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu feisty universe
# deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
```

**[COLOR="Red"]I am going to have to leave after the next post or 2, sorry![/COLOR]**

---

### Post by InGunsWeTrust on 2007-08-25
Delete the entire contents of the file and enter this. Then save. That has wine and lots of other good stuff to after the install you'll have to make the changes again.

Then do the original install line

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
  
  
  
  
  
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://packages.medibuntu.org/ feisty free non-free
```

---

### Post by Ian505 on 2007-08-25
Okay, unfortunately, I am out of time. I have to go after you reply this. 

I changed the file, ran Synaptic then made sure that all the 3rd Party Software was checked. (It was) Tried "sudo apt-get install ntfs-3g ntfs-config" but the same error appeared...

Please post after you read this as I have to go, but please (if it is convenient for you) discover the problem while I am gone. I don't know if I will be on again tonight, but I doubt it. 

-Ian

---

### Post by InGunsWeTrust on 2007-08-25
I'll try to boot up with he live CD and install ntfs-config and if I can't recreate it I'll get the ext3 driver suggested by another user above working on windows and provide some docs for that.

---

### Post by Ian505 on 2007-08-25
Okay thank you! I really appreciate you trying to help me. I am sorry that I couldn't stay on longer, but a friend is moving in and I promised to help them this evening.

Thanks for all your help! I will be back tomorrow for sure.

-Ian

---

### Post by InGunsWeTrust on 2007-08-25
I made a two kinda silly mistakes.

First I am using 64-bit Ubuntu so if you are using 32-bit our repositories will be different. Second I forgot to make you update your apt-get after you changed sources.list.

All you have to do is

```
sudo gedit /etc/apt/sources.list
```

uncomment the two deb lines that are commented and save so it will look like this:

```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

```

Then just do

```
sudo apt-get update
sudo apt-get install ntfs-config ntfs-3g
```

the apt-get update I accidentally skipped last time so you were looking at your old cached list of packages.

I successfully installed ntfs-config and ntfs-3g while running the live CD so I KNOW it'll work this time haha.

If you are using a 64-bit processor though you should use my sources.list after the install because it does have a lot of extra goodies in it.

---

### Post by Ian505 on 2007-08-26
Okay I opened sources.list and pasted what you put in your last post and updated it. I got several error messages:
```
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty Release.gpg
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty/restricted Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty Release
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty/main Packages
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty/restricted Packages
Err cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415) feisty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]       
Ign http://security.ubuntu.com feisty-security/main Translation-en_US     
Get:2 http://archive.ubuntu.com feisty Release.gpg [191B]
Ign http://archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Get:3 http://security.ubuntu.com feisty-security Release [50.9kB]
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Get:4 http://archive.ubuntu.com feisty Release [57.2kB]
Get:5 http://security.ubuntu.com feisty-security/main Packages [74.6kB]
Get:6 http://archive.ubuntu.com feisty/main Packages [1007kB]       
Get:7 http://security.ubuntu.com feisty-security/restricted Packages [6360B]  
Get:8 http://security.ubuntu.com feisty-security/main Sources [12.8kB]
Get:9 http://security.ubuntu.com feisty-security/restricted Sources [953B]     
Get:10 http://archive.ubuntu.com feisty/restricted Packages [7628B]         
Get:11 http://archive.ubuntu.com feisty/main Sources [293kB]
Get:12 http://archive.ubuntu.com feisty/restricted Sources [1710B]             
Get:13 http://archive.ubuntu.com feisty/universe Packages [3754kB]             
Get:14 http://archive.ubuntu.com feisty/universe Sources [1131kB]              
Fetched 6398kB in 21s (295kB/s)                                                
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/dists/feisty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I went ahead and ran the install line for ntfs-config and ntfs-3g and... they successfully installed!

```
ubuntu@ubuntu:~$ sudo apt-get install ntfs-config ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libntfs-3g0
The following NEW packages will be installed:
  libntfs-3g0 ntfs-3g ntfs-config
0 upgraded, 3 newly installed, 0 to remove and 75 not upgraded.
Need to get 158kB of archives.
After unpacking 770kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com feisty/universe libntfs-3g0 1:1.328-1 [90.0kB]
Get:2 http://archive.ubuntu.com feisty/universe ntfs-3g 1:1.328-1 [25.9kB]
Get:3 http://archive.ubuntu.com feisty/universe ntfs-config 0.5.5-0ubuntu1 [42.5kB]
Fetched 158kB in 0s (193kB/s)     
Selecting previously deselected package libntfs-3g0.
(Reading database ... 91545 files and directories currently installed.)
Unpacking libntfs-3g0 (from .../libntfs-3g0_1%3a1.328-1_i386.deb) ...
Selecting previously deselected package ntfs-3g.
Unpacking ntfs-3g (from .../ntfs-3g_1%3a1.328-1_i386.deb) ...
Selecting previously deselected package ntfs-config.
Unpacking ntfs-config (from .../ntfs-config_0.5.5-0ubuntu1_i386.deb) ...
Setting up libntfs-3g0 (1.328-1) ...

Setting up ntfs-3g (1.328-1) ...
Setting ntfs-3g suid root with group fuse...done
Users from 'fuse' group can now mount NTFS volume.

Setting up ntfs-config (0.5.5-0ubuntu1) ...
ubuntu@ubuntu:~$ 

```

Yay! It worked!

Now back to the partitioning.... I don't know if you saw my post edit earlier: (Post 14)
> EDIT- Okay what file system does the swap partition use as well as Ubuntu? And whats 'Round to Cylinders' mean? Also, do I create it as a primary partition or an extended partition? I have a feeling that these are pretty basic questions, but see my signature. (And its only the past week I have decided to make the switch.) 

Also, in the next post, you said something about making the My Docs partition pointed to /home/... I somewhat understand: 
You want the My Documents in Windows and Home in linux to be the same. I understand. However I don't want seperate partitions for all  of my folders- for example I would like a partition for documents and such as well as a partition for Media (Images and Video) But I don't want a specific partition for each, just one for media and one for basically everything else. (The everything else one being on the Windows (80GB) drive and the Media one being on the Linux (150GB) drive.) Though I would like a Video and a Image folder in the media partition to point to the My Images and My Video in Windows and whatever it is in linux.

I really, really appreciate you taking your time to help me with this, :)

-Ian

---

### Post by juxtaposed on 2007-08-26
> I was wondering if it is possible to set up windows like linux- have one partition for the actual system and a second partition for the actual data.

Yes. Make a small partition to install to, then another to put data on it, its very simple.

---

### Post by Ian505 on 2007-08-26
Yes but I want both Windows and Linux to be able to read the data partition(s) so I can access them from BOTH oses. (See InGunsWeTrust's posts)

-Ian

---

### Post by Imsati on 2007-08-26
>Yes but I want both Windows and Linux to be able to read the data partition(s) so I can access them from BOTH oses

This link should solve your problems:   [http://fs-driver.org/](http://fs-driver.org/)

My Set-up is...

80 GB XP Drive; 15 GB partition for the OS, 15 GB partition for Application Software (Adobe, Printer drivers, Office, Quicktime, Realplayer, etc.), and the rest for my personal files.

80 GB Linux Drive: 2 GB Swap, 7 GB Root, 10 GB Home, 7 GB Kubuntu Root, 10 GB Kubuntu Home, and the rest as a backup for my personal files.

I can view/change any partition from either OS using the above program. With the XP partitions set up the way they are, I can deal with a BSOD (i'll not like it, but I can deal with it) and still not have to worry about reinstalling my individual software or losing my personal stuff, just the OS and updates.

Feel free to PM me if you have any questions--it should be self-explanatory though. Partitions are tricky though sometimes.

---

### Post by Ian505 on 2007-08-26
Thanks for the offer, I really appreciate it. However I think that InGunsWeTrust is going to try the NTFS-3G format first and then try the Ext2 for windows. If he can't figure it out, we will ask you but for now I think that I will stick with InGunsWeTrust mainly because I have already done so much already.

I appreciate your offer though, I thank you for that.

-Ian

---

### Post by kellemes on 2007-08-26
> **Cows said:**
> I'm positive that windows cannot read information that's on the linux partitions. The only way windows and linux can read data from the same partition would be to have a FAT or FAT32 partition. 

A sharepartition should be formated ext3.
There are a gazillion reasons as to why ext3 is preferred over fat32 and it´s support on Windows is as stable as possible.

---

### Post by Ian505 on 2007-08-26
You know, maybe you guys are right... hey InGunsWeTrust... why don't we just go with that extension for Windows that extends its compatibility to include ext2 and ext3. (Mainly because I despise fragmentation.)

-Ian

EDIT- I am going to go ahead and do that- though I am still going to need your ntfs support so that linux can read ntfs for the windows partition.

---

### Post by InGunsWeTrust on 2007-08-26
There errors above were probably triggered by me referencing my CD-ROM image in my sources.list I would actually suggest that after the install you do not use my sources.list to avoid errors like that.

Also if you have restarted logged out or powered down since you applied the changes using the live CD. You will need to apply them again because the live CD does not write any information to the hard drive

Also note the last step in enabling NTFS access

```
ntfs-config
```
It may ask you to mount drives in which case you will check add in front of each box and give each partition a name (the name can be anything it doesn't really matter) Then check both boxes and click OK

Yeah I wasn't getting you to make seperate partitions for each My Docs, Videos, Etc. Basically /home/ is the Linux equivalent to My Documents. In Windows the My Music, My Video, etc. are inside of My Documents.

I have a pretty good understanding of what the exact configuration you want is but to provide exact terms could you take a screen shot of the partitioner showing all of the current drives on the system and add it as an attachment to this post? If I am not mistaken there is a drop down box in the corner that will let you select which hard drive you are editing if that is so take a screenshot of the info on both hard drives. If all the hard drives are on one page I only need one. The gnome screen shot tool default is .png image make sure to change if to .jpg (just delete the .png at the end and type .jpg)

---

### Post by Ian505 on 2007-08-26
> **InGunsWeTrust said:**
> There errors above were probably triggered by me referencing my CD-ROM image in my sources.list I would actually suggest that after the install you do not use my sources.list to avoid errors like that.

Also if you have restarted logged out or powered down since you applied the changes using the live CD. You will need to apply them again because the live CD does not write any information to the hard drive

Also note the last step in enabling NTFS access

```
ntfs-config
```
It may ask you to mount drives in which case you will check add in front of each box and give each partition a name (the name can be anything it doesn't really matter) Then check both boxes and click OK

Yeah I wasn't getting you to make seperate partitions for each My Docs, Videos, Etc. Basically /home/ is the Linux equivalent to My Documents. In Windows the My Music, My Video, etc. are inside of My Documents.

I have a pretty good understanding of what the exact configuration you want is but to provide exact terms could you take a screen shot of the partitioner showing all of the current drives on the system and add it as an attachment to this post? If I am not mistaken there is a drop down box in the corner that will let you select which hard drive you are editing if that is so take a screenshot of the info on both hard drives. If all the hard drives are on one page I only need one. The gnome screen shot tool default is .png image make sure to change if to .jpg (just delete the .png at the end and type .jpg)

Im in XP right now- I was going to move everything to the 80G drive to avoid loss of data while editing the 150G drive- should I continue?

EDIT- Nevermind!

---

### Post by InGunsWeTrust on 2007-08-26
Since you are in XP type mmc into the run box then highlight file and select Add Snap-ins. Select Computer Management. When asked network or local select local then close the Snap-in adding screen then expand storage and select disk management. Take a screen shot of that and post it. 

*Alternatively*

If you know how to open the computer management screen do it and select disk management

__

Before I can give any further instruction I just really need to know how many partitions there are, How full they are, the size of the partitions, and instad of asking a dozen or so questions a picture is worth a thousand words!

---

### Post by Ian505 on 2007-08-26
I know exactly what you are talking about- I have been there many times before but I am in Ubuntu now...

So I am going to put your new sources.list in, and install ntfs-config, mount the drives, then- if you want, I can move everything to the first drive. Here is a screenshot now.

I have to go and eat I will be back later.

---

### Post by InGunsWeTrust on 2007-08-26
In the top right corner where it shows /dev/sda/ Click that drop and a down box will appear 
select the second entry, That would be your second HD and i need to see that too

Also just a little more info about HD1

1. /dev/sda2 is obviously XP correct?
2. Does the XP partition have music and video that you intend on moving to the share partition?
3. /dev/sda3 is probably your recovery partition but what is /dev/sda1?

---

### Post by Ian505 on 2007-08-26
> **InGunsWeTrust said:**
> In the top right corner where it shows /dev/sda/ Click that drop and a down box will appear 
select the second entry, That would be your second HD and i need to see that too

Also just a little more info about HD1

1. /dev/sda2 is obviously XP correct?
2. Does the XP partition have music and video that you intend on moving to the share partition?
3. /dev/sda3 is probably your recovery partition but what is /dev/sda1?

Sorry, I forgot to upload the 2nd one. 

dev/sda3 and dev/sda1 are both part of the Dell Restore. One partition is named Dell Restore and the other is named Dell Utility. Again, I cannot delete either of these or compromise their integrity.

As for the /dev/sda2 partition, you are correct in saying that it is the XP partition and it DOES contain most of the stuff for the shared partition. 

The 2nd HD has 2 partitions and some just-cleared unpartitioned space. The first partition IS NOT EMPTY- it still contians ~77MB of info. (Though I am not sure what it is- or if I can delet it.) The other one also contains undeletable info. The info on the 2nd one is the most important of the 2.

Also, a question- when you resize the partition, does risk losing the data if you don't make it smaller than the data that is already on there?


-Ian

---

### Post by InGunsWeTrust on 2007-08-26
It won't allow you to resize it smaller than the amount of info on it. 

So basically you want a volume dedicated to windows, a volume dedicated to linux, a volume dedicated to video editing and a volume dedicated to Docs, music, etc. correct?

The 77 mb is probably volume info added to the drive as part of the formatting process. If you don't KNOW of important info on it then it is not important.

Since you are back in Ubuntu again the first step in any case would be to repeat the steps to install ntfs-config and ntfs-3g so go ahead and do that then answer the question and we can go from there.

I apologize in advance for my slow response time I am doing my homework at the same time right now! haha

---

### Post by Ian505 on 2007-08-26
1. Okay
2. Correct
3. Okay- installed, do you want me to run it?
4. No problem, I do it all the time! :)

---

### Post by InGunsWeTrust on 2007-08-26
Yes, Indeed run ntfs-config and enable writing just as i said before it may ask you to mount some drives just give it any old name and do so.

Then resize the first partition on the second drive to the largest size you can make it. This will become your share drive

Then explore the XP partition and copy the music videos etc that you want on the share partition, Do not however copy program files because most will require you to install them to the share drive.

---

### Post by Ian505 on 2007-08-26
> **InGunsWeTrust said:**
> Yes, Indeed run ntfs-config and enable writing just as i said before it may ask you to mount some drives just give it any old name and do so.

Then resize the first partition on the second drive to the largest size you can make it. This will become your share drive

Then explore the XP partition and copy the music videos etc that you want on the share partition, Do not however copy program files because most will require you to install them to the share drive.

Okay I will do that- please note that it will take some time for me to get EVERYTHING over to the shared partition, I will post when done and edit if I have to go anywhere.

-Ian

---

### Post by Ian505 on 2007-08-26
Error! Okay when I tried to resize it the following happened... I included 2 screenshots showing what happened. Once I closed those dialog boxes, I was going to try it again but all the options except New... are greyed-out. Also, there is a padlock next to the partition location.

What happened?

This happened when I resized it smaller and I did... something... and bypassed it... I dont remember.... But anyway then I booted XP and got a CHK Disk thing and checked to make sure my data was okay and it was... so what happened?

---

### Post by InGunsWeTrust on 2007-08-26
Oh yeah that happened because they are mounted from what you did from ntfs-config right click each one and select unmount or release or stop i dont know exactly what it says. After the changes are applied do ntfs-config again to remount them

---

### Post by Ian505 on 2007-08-26
> **InGunsWeTrust said:**
> Oh yeah that happened because they are mounted from what you did from ntfs-config right click each one and select unmount or release or stop i dont know exactly what it says. After the changes are applied do ntfs-config again to remount them

"You are not privlaged to unmount volume... only root can unmount /dev/"

Okay! I hope you know what happed 'cause I don't!

-Ian

---

### Post by InGunsWeTrust on 2007-08-26
close that session of gparted and do sudo gparted at the command line that should give you root privleges

---

### Post by Ian505 on 2007-08-26
> **InGunsWeTrust said:**
> close that session of gparted and do sudo gparted at the command line that should give you root privleges

Okay, it worked, thanks. I will move everything to the shared now.

-Ian

**GRR!** It wont re-mount the partition! Help?

-Ian

---

### Post by Ian505 on 2007-08-26
see edit above

---

### Post by InGunsWeTrust on 2007-08-26
Alright let's try another approach to this. Reboot and reinstall ntfs-config and ntfs-3g. This way we will have a clean slate.

Then open gparted and resize your Windows partition to 5 gigs smaller and format the resulting 5 gig chunk to ext3 this will be your ubuntu partition. 

Close gparted and run ntfs-config and enable writing to ntfs drives.

Then double click the install icon on the desktop and go through the install process. When asked how to partition choose manually. A screen that looks like gparted will come up and since you have already partitoned the drive how you want simply click next to go passed it. You will be at the screen where you choose mount points. 

Make the 5 gig partition you made /
Make the share partition /home/
Make the XP partition /media/XP/
Make the Video editing partition /media/VideoEditing/

Finish the install process as normal.

---

### Post by Ian505 on 2007-08-26
> **InGunsWeTrust said:**
> Alright let's try another approach to this. Reboot and reinstall ntfs-config and ntfs-3g. This way we will have a clean slate.

Then open gparted and resize your Windows partition to 5 gigs smaller and format the resulting 5 gig chunk to ext3 this will be your ubuntu partition. 

Close gparted and run ntfs-config and enable writing to ntfs drives.

Then double click the install icon on the desktop and go through the install process. When asked how to partition choose manually. A screen that looks like gparted will come up and since you have already partitoned the drive how you want simply click next to go passed it. You will be at the screen where you choose mount points. 

Make the 5 gig partition you made /
Make the share partition /home/
Make the XP partition /media/XP/
Make the Video editing partition /media/VideoEditing/

Finish the install process as normal.

I am going to have ubuntu on the 150G drive because that way if one drive fails I can always boot something.

Also, what about the 'swap' partition?

---

### Post by InGunsWeTrust on 2007-08-26
Didn't you say you had 2 Gigs or RAM? You don't really need a swap with that much RAM or am I thinking of another thread. Just resize the video editing or share partition 5 gigs smaller than and make an ubuntu partition.

---

### Post by Ian505 on 2007-08-26
> **InGunsWeTrust said:**
> Didn't you say you had 2 Gigs or RAM? You don't really need a swap with that much RAM or am I thinking of another thread. Just resize the video editing or share partition 5 gigs smaller than and make an ubuntu partition.

1.5gigs, but okay, if you say I don't need a swap I wont make one.

---

### Post by InGunsWeTrust on 2007-08-26
The swap is like the pagefile it is only used if you don't have enough RAM to support the applications you are running. If later you have performance issues you can always create one. But with all the troubles we are having I am just saying not now for simplicity's sake.

It's been a while since your last post so I assume the install is going smoothly

---

### Post by ashishgoel on 2007-08-26
i've read somewhere on the forum that FAT32 is recognized by both, ubuntu n Windows...
So, it can be used as common sharing disk..

---

### Post by InGunsWeTrust on 2007-08-26
The are indeed but FAT32 has no security features at all and there is a max size of i think 32 or 16 gig and only 256 entries can be at the root level

---

### Post by Cows on 2007-08-26
Yea I know that ntfs-3g can read/write to a ntfs partition. I use ntfs-3g and the ntfs-config.

---

### Post by InGunsWeTrust on 2007-08-26
While it is a little more difficult than just using FAT I was suggesting NTFS becase the FAT filesystem has so many restrictions I couldn't even hold all of my music in a FAT partition because of the size limit haha.

---

### Post by Ian505 on 2007-08-28
Okay, I am really sorry about the long dely in posting. I have been very obe as of late.

Anyway, everything is going fine so far, but I was wondering if I should use a different sources.list after install since yours is based on amd 64.

-Ian

PS- Ok, problem. I cannot select my drives that are partitioned as NTFS so I can set them as /media/XP etc., only the ext3 partition is selectable.

---

### Post by InGunsWeTrust on 2007-08-28
I do not know that for sure with the ubuntu reposintories but some of the third party ones are dedicated to 64 bit software. My suggestion would be to google each repository and see if it contains 32 or 64 bit software or you can just find your own repositories. I just provided mine cuz I knew that ntfs-config was on it.

---

### Post by Ian505 on 2007-08-30
Okay I will do that.

NOTE- From the looks of things, I will only be able to work on this during the weekend. I am sorry but school recently started and I need to focus on that during the week.

I still appreciate your help and effort.

-Ian

---

### Post by InGunsWeTrust on 2007-09-01
Let me know how it goes! Pretty much all the info you need is somewhere in previous posts so I hope it goes well

---

### Post by Ian505 on 2007-10-29
> **InGunsWeTrust said:**
> Let me know how it goes! Pretty much all the info you need is somewhere in previous posts so I hope it goes well

I would like to thank you properly for helping me with this and spending so much of your time on me. You helping me had greatly familiarized myself with ubuntu and I am no longer afraid of the terminal! I greatly appreciate everything you did to help. I now have almost everything set up and have found myself choosing Ubuntu at boot. 

-Ian

PS- I did get the NTFS3G set up before 7.10 came out, but I am glad it is now preinstalled. :-)

---

### Post by InGunsWeTrust on 2007-10-29
I know right Ubuntu 7.10 is awesome. You should try out some of the new features of Compiz too!

---

### Post by Ian505 on 2007-10-31
> **InGunsWeTrust said:**
> I know right Ubuntu 7.10 is awesome. You should try out some of the new features of Compiz too!

I know! The set on extra, the windows remind me of old jello!:)

-Ian

---

### Post by InGunsWeTrust on 2007-11-01
I suppose this issue has been officially solved by the Gutsy Gibbon so we can close this thread, but I added you to my buddy list, periodically I'll check out what kind of posts you have and see I can help ya out

---

