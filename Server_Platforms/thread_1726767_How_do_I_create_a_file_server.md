---
title: "How do I create a file server?"
date: 2011-04-11
forum: Server Platforms
---

### Post by SliderTech on 2011-04-11
Is this the correct place to ask about building a file server?

Thanks

---

### Post by uRock on 2011-04-11
> **SliderTech said:**
> Is this the correct place to ask about building a file server?

Thanks

Hello and welcome to the forums,

Feel free to start server related threads here [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

Cheers,
uRock

---

### Post by CharlesA on 2011-04-11
*Thread moved to **Server Platforms**.*

What did you want to machine to do? Just file server?

---

### Post by SliderTech on 2011-04-11
Hi all, 
Thanks for moving my question to the right place.

My family would like a file server for the home movies, music and whatever junk they want to put on it.  They would like a main folder called family with individual sub folders that everyone has access to. 

We wont be using the file server for much else. Mainly to store files and things. 

I can tell you that we have mixed systems here with Windows, Ubuntu and Mint on them. Some of them are duel boot.

None of us are computer savvy and we just started to play with the distro's.

Thanks for the help.

---

### Post by BertN45 on 2011-04-11
In your case I would use the standard Ubuntu desktop and use windows shares, since you are in a mixed environment. Use Nautilus or Samba to define which folders you like to share on the Ubuntu "server". Samba is available from the ubuntu software center. The user interface is easy to use and you can define the access rights of each user for the folders as you like it. You have to make sure that the "server" has all users defined that want to use the file server. The passwords selected must be used, when connecting to the server the first time. 

Do you want to use a monitor and keyboard/mouse for the server or do you want to control it remotely?

---

### Post by tgalati4 on 2011-04-11
For older computers, freenas works well:

[http://freenas.org](http://freenas.org)

---

### Post by papibe on 2011-04-12
Tips for choosing the machine for the server:

It doesn't have to a fast processor, atom, celeron or even Pentium 4 will work just fine. You don't need much RAM too, 512Mb will work, although 1Gb would be better if you chose to use Ubuntu Desktop. What you DO need is a fast hard drive, so I think a SATA drive is a must. Also, you're going to need a lot of space, 1Tb would be a start. As far as network card, unless you have a nice gigabit network running well, a regualar 100Mbs card would suffice.

Examples:
[LIST]
[*]I have a refurbish IBM, P4, 512Mb RAM working just fine (I had to add an additional hard drive latter on though).
[*]My brother has a custom made, Celeron Dual-Core, 1Gb RAM, 1Tb hard drive.
[/LIST]

I hope this info help you.

---

### Post by BertN45 on 2011-04-12
I am using a 650 mHz Pentium III with 384mB of memory as file server and it has two IDE hard disks of 250 GB and 300 GB. I admit I was lazy, so it still runs Windows XP since 2005, It is stored some where down in the cupboard and it only has two cables coming out, the power cable and the ethernet cable. I use power fail/auto-restart, which is a must in the Dominican Republic, if you do not want to go on your knees a couple of times per day to power on the machine..

Do not worry about memory 256/384 mb will be fine also for Ubuntu. You only log-in, if you want to set up the server. Used as server you only power on the machine, but you do NOT log in. The file server will have been started during booting. The desktop software will not be needed/loaded during file server operation. 

The speed of the disks is not a real problem, since you main bottleneck will be the network. Even the older disks will easily run at 50-100 Mb/secs, but the network will limit the throughput to max. 10 mB/sec or 5mB/sec for wifi. The size of the disks will become an issue, since after using the family file server  for a couple of years my two disks are getting too small. That might be a reason to use SATA drives, since they are more modern and provide more capacity for the same amount of bucks,

I consider to buy a network attached storage (NAS) device, that is a disk or a set of disks with a network connection. It is like an USB drive, but with an Ethernet plug, some also support wifi.  Normally it has an embedded processor that runs some flavor of Linux (e.g. Freenas) and it provides a remote desktop interface to set the user access rights. They are available for less than $200. Google for "consumer NAS device".

If you like to play around or re-use old hardware go for the Ubuntu solution , if you only interested in results go for the NAS device.

---

### Post by donniezazen on 2011-04-12
What video server do you guys use? Not video streaming, i am looking for something that can pull video files off my server and play it anywhere. I like Ajaxplorer but it only supports mp4 files and video conversion is mess. VLC server sound like a good idea but i can't find proper resources that would have a web interface and enable a secure login.

Thanks.

---

### Post by papibe on 2011-04-12
> **soham_1207 said:**
> What video server do you guys use? Not video streaming, ... and play it anywhere.

I'm not sure if I understand the question, so let me tell you what I believe I know about it (I'm sure more people will jump in and correct me, or add more useful info).

If the server's clients are computer (or smart devices), you don't need any kind of video server software or streaming service. Since all devices can decode and play any video format (of course, there're some limitations like old netbooks won't play HD). Then you just need share folders on the network by using [NFS]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html") or [SMB]("https://help.ubuntu.com/community/Samba").

On the other hand, if you have restricted or dumb devices like PS3, Xbox, Wii, etc. Since those devices both don't play all formats, and sometimes don't read shared folders, you need to setup some kind of a service to transcode the video to a format the device can play (translate mkv to mp4 for example), or/and stream the content to the device (using UPnP for example).

Now having said that, maybe what you're looking for is a nice client that let's you browse the content in a nice graphical way. In that case for media (pics, movies, audio), I would recommend [XBMC]("http://xbmc.org/") or [Boxee]("http://www.boxee.tv/").

I hope that rumble clears things up for you.

---

### Post by SliderTech on 2011-04-12
System:
OS Maverick 10 desktop.
5yr old Dell modified.

2 drives ATA: 
40GIG OS on it only
500GIG

CPU: Celeron 2.20GHz
Ram: It's reporting 488MB

How do I install windows share on it?
I have installed Samba.
When you talk about "users defined that want to use the file server" That means each person needs an account on the Ubuntu server? 
Each folder or share created, I would need to add each person to it or can I have one main folder and the sub folders would be populated access for all?

I have a monitor and keyboard connected to it.

I like the NAS idea.

---

### Post by BertN45 on 2011-04-12
You are almost there. You have to add the users if you want to define different access rights for different users. If all users are allowed to see and change everything you do not need to define the users. To define the users you have to go to the system menu and select "Users and Groups". You will have to add each user that needs access to the file server (see the remark about passwords in the third paragraph).

Afterwards you go to SAMBA and define the windows shares you need.. If you want to connect te printer it already taken care of. To define the shares press the "+" and select the directory, fill in the rest of the form and go to the second tab for the access rights. Here you could also select to give everybody access rights in case you did not specify the users..

Now you are ready to connect to the windows shares, but that process will be slightly different for Windows, Mint and Ubuntu clients. You just have to make sure that you provide the Ubuntu password, if you connect to the share. The easiest would be to use the same password for the same user on both client and server machines. Sometimes it also helps if you use the same work group name, For linux the default is WORKGROUP and the same is true for some Windows releases, but Windows XP Home e.g. uses MSHOME.

This process will be almost the same for a NAS device, since most of them use Linux and windows shares too. 

Your hardware will be perfectly capable of supporting the file server. It took us, two/three years to get 500 MB full. if that happens you could always add another drive..

You still have to consider two issues;
- Do you need some space and do you want to remove the monitor and keyboard?
- What about back-ups?

---

### Post by confusedstingray on 2011-04-13
for video server you may look at twonkymedia or  tumb media 
run it from 1 machine and all devices that have upnp and network access can see
all movies and pictures and music.

---

### Post by SliderTech on 2011-04-15
It seams I have a bit of work.

A quick side path.

I need to use the CD writer, what do I use?


[SIZE=3][COLOR=Blue][SIZE=4]I came home for lunch and put in a CD and the program came up.  So never mind... :)[/SIZE] [/COLOR][/SIZE]

---

### Post by SliderTech on 2011-04-16
[confusedstingray]("http://ubuntuforums.org/member.php?u=406680")

Thanks for the info, that might be something to look into in the future. I like the idea, what about just regular files?


> **confusedstingray said:**
> for video server you may look at twonkymedia or  tumb media 
run it from 1 machine and all devices that have upnp and network access can see
all movies and pictures and music.

---

### Post by SliderTech on 2011-04-16
BertN45:

I have a total of 4 users to connect to the server.

Ok, Samba set to the storage drive, I also checked "writable and visible" and access set to "Allow everyone".

Since I checked "Allow everyone" I don't need to create or define the users. I think that is what you mean.

Under the windows shares I see the other system names under the workgroup name, I also see the (FS)file server name. When I click on the FS name it shows print$ and storage (the name I gave the drive)  When I click on "storage" a windows pops up, it says "Unable to mount location" "failed to mount windows share"  -  Is that a problem? 

I found out this morning my wife has 45Gig and my oldest son has 250Gig and I have about 100Gig of crud to put on the server, so I am going to stick a 1T in soon.

In XP I went to log into the file server and I get a window that says "is not accessible" and talks about not having permission to use that resource.

As for the monitor, keyboard and mouse; I use a KVM switch hooked up to a PC and the file server so saving desk space in no need, as for the UPS. I have a APC Smart-UPS 1400 for power but I don't have a data backup yet.

---

### Post by BertN45 on 2011-04-19
I have been installing Xubuntu 11.04 at home so I have been off  for some days. 

I assume you have rebooted the server after the installation.

If you allow everyone in Samba, all users on all client PCs should be able to connect to your share.
It is strange that windows says it does not have permission to access that share, since you allowed everyone access to the "Storage share".

I would start the "ubuntu software center" and click on "installed software". Look whether the following packages have been installed. It is easiest if you type "samba" in the search box, it should show:
- SMB/CIFS file, print and login server for Unix, 
  small text: samba
- Samba
  small text: Create, modify and delete samba shares.

Try now "smb" in the search box, but I will only supply the names in the small text otherwise I have to type so much:
- smbclient
- libsmbclient
- samba
- gvfs-backends
- libpam-smbpass
- samba-common
- libwbclient0
- samba-common-bin
- tcpdump
- libgnomevfs2-extra
- python-smbc

That are the packages I have installed, but my PC is both server and client. The missing packages you can install by typing the name in the search box after you switched to "get software".
 
Installing this week my system again, I found that libpam-smbpass was missing, so I could not access password protected shares.

---

### Post by SliderTech on 2011-04-23
Bert,

No worries on the quick replies.  I have been busy doing other things that need to be done.

I checked the list you have and only the libpam-smbpass was missing.  I installed it and still no access.  Same error message.

This server has no files on it or special anything, Can I reset it somehow encase I set something up wrong or did something I should not have? or what would be your next suggestion?

Thanks

---

### Post by TheFu on 2011-04-23
> **SliderTech said:**
> Hi all, 
Thanks for moving my question to the right place.

My family would like a file server for the home movies, music and whatever junk they want to put on it.  They would like a main folder called family with individual sub folders that everyone has access to. 

We wont be using the file server for much else. Mainly to store files and things. 

I can tell you that we have mixed systems here with Windows, Ubuntu and Mint on them. Some of them are duel boot.

None of us are computer savvy and we just started to play with the distro's.

Thanks for the help.

Ok, while you can make a file server from any Linux box that you like by loading Samba, it sounds like you may be happier with a media player device that can also be a file server/NAS.  For about $60 you can get a refurbished WD TV Live HD (not the plus) network media player.  You can connect it to your network via ethernet and connect 2 drives via USB.  Those drives will be seen on the network as Samba/CIFS (Windows Shares) and you won't be bothered with user accounts or permissions.  Obviously, this device will use much less power than a PC and the only noise will be from the spinning disks.

That device plays WD content and lots of different media formats - mpg, avi, mkv, mp4 and some mov, flv and wmv , but not all.  If you'd like Netflix, then get the "plus" version for $100.

By now, you've probably gotten samba working and figured out the permissions, but I figured this might be helpful to someone else later.

There are lots of other storage server options and if you want more than just pure CIFS/Samba shares, definitely use an Ubuntu-based server and you can add all sorts of other services like a home wiki or recipe DB or PVR or on-the-fly media transcoder if you have an Xbox360 or PS3 that you'd like to stream videos to as well. The options are unlimited.

---

### Post by SliderTech on 2011-04-24
The FU.

You might be right about that, but for now this is also a good chance for me to learn Linux so I can be a little better at using it. 

Thank you for the suggestion and I will keep it in mind.


~Steve

---

### Post by SliderTech on 2011-05-07
[BertN45]("http://ubuntuforums.org/member.php?u=1276368"),

Are you still helping me?

What would be my next step?


Thanks

---

### Post by SliderTech on 2011-11-23
[SIZE=3][COLOR=DarkOrange]Whom ever might have been watching this thread. [/COLOR][/SIZE]

[SIZE=2][COLOR=black]I never received any more help about this, so this thread ended because of that...[/COLOR][/SIZE]

[SIZE=3][COLOR=Blue]***( I am a complete nubie at this stuff and I did it! )**[/COLOR][/SIZE]

[SIZE=3][COLOR=Blue]**On a better note! **[/COLOR]  I found the[COLOR=DarkOrange] [COLOR=Red]Free NAS Server[/COLOR] [/COLOR]software with clear instructions.[/SIZE][SIZE=2][COLOR=Green]
v8 - [http://www.freenas.org/](http://www.freenas.org/)
v7 - [http://sourceforge.net/projects/freenas/files/FreeNAS-7-Stable/](http://sourceforge.net/projects/freenas/files/FreeNAS-7-Stable/)
7 Forum - [http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=75&t=2109](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=75&t=2109)
Other info - [http://wiki.freenas.org/FreeNAS#freenasthe_freenas_server](http://wiki.freenas.org/FreeNAS#freenasthe_freenas_server)
[/COLOR][/SIZE]
[SIZE=2]I have it up and running and it works amazingly well.  I am using v7 and not v8.

I even have it set up so anyone can connect to it from the web and do what they need to. I now have my families from all over the planet connecting to it and exchanging music, pictures or whatever they want. 

Next is to start a friends and family chat thing going on so we can move away from FB.


[/SIZE]

---

