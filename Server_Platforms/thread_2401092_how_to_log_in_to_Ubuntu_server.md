---
title: "how to log in to Ubuntu server"
date: 2018-09-13
forum: Server Platforms
---

### Post by karebo on 2018-09-13
I just installed Ubuntu server 18.04.1 LTS on a new computer that I want to use as server.
This is the first time I use any other OS than Windows.
No problems logging in with username and password but that did not
let me in to the program. Then came root and sudo.
I have spent the last several hours reading postings on several communities and forums
but alas, understood little.
So I am stuck in sudo, could anyone please help me get past this and into the Ubuntu program?

---

### Post by mastablasta on 2018-09-13
Ubutnu is an operating system. you need to have a user created (the admin is created on install) then you just log in with username and password.

if you want to log in remotely you need a transfer protocol for that. i suggest OpenSSH.

what program do you want to log into actually? server has only command line installed. there is no desktop. if oyu want desktop on a server (not recomended) you need to install ubuntu-desktop package.

instead it if you need a user interface use a web browser based interface such as for example ajenti or zentyal.

---

### Post by slickymaster on 2018-09-13
Thread moved to **Server Platforms** for a better fit

---

### Post by oldos2er on 2018-09-13
> 
No problems logging in with username and password but that did not
let me in to the program. 

What program are you wanting to run?

---

### Post by LHammonds on 2018-09-14
Ubuntu Server is an operating system.  It doesn't really do much on its own out of the box.  You will need to install packages for specific tasks.

**EDIT:** When you installed the server software, you typed in an ID and password for the administrator account.  That is what you use to login.  If you need root-level access, you add "sudo" as a prefix to the command that needs elevated privileges.  The "root" account itself is disabled for security reasons so you use "sudo" to run commands that need that level of access.

Here is a how-to guide I put together which I use as a base for every server I create: [How to Install and Configure Ubuntu Server 18.04 LTS]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244").  It is lengthy but it covers step-by-step the things I do to setup a production-level server that is designed to run and last for years.

Examples of software you can add onto Ubuntu Server:

[LIST]
[*][File sharing with Windows]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p629") 
[*][File sharing with Linux]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p630") 
[*][MariaDB database server]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=245") 
[*][CumulusClips]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=246") YouTube-like media service. 
[*][WordPress]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=249") content management web site. 
[*][NextCloud]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=254") Dropbox-like web file service 
[*][MediaWiki]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=241") documentation web site. 
[*][Nagios]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=227") network monitoring service. 
[*]...and many other packages. 
[/LIST]

---

### Post by TheFu on 2018-09-14
I don't know what "stuck in sudo" means, but you can usually cancel out of anything shell program using <cntl>-c.

If you've never used Unix before, trying to work with any Linux server distro will be a very steep climb of knowledge.  Very steep, indeed.

If you see a prompt like this ```
$
```, then you are in Ubuntu Server. There isn't any point-n-click, if that was your hope.  Unix-like servers expect the user to be knowledgeable of the system.

If you google for "ubuntu server guide", it provides information for setting up specific services, but it will expect an intermediate-level of end-user knowledge for understanding the steps.

If the information provided in this thread is helpful and got you passed the issue, please mark it as "SOLVED" - thread tools button near the top. That helps the rest of the community - both seeking answers and looking to help others.

---

### Post by karebo on 2018-09-15
Thank you all for answers. Yes, I am New to Ubuntu and Linux, my only OS experience is Windows.
I am looking for an OS for my newly built server, and was recommended Ubuntu.
Now I understand that I am in Ubuntu server, that Learning to use it is a steep Climb.
I did expect the OS to have a GUI.
I want to keep Ubuntu, and learn to use it, but to get started With my server I need another OS, maybe Windows Home Server.

So the problem I face now is this: Is there an easy way to make partitions in Ubuntu Server, or should I rather make a fresh install and create partitions in the process?

---

### Post by TheFu on 2018-09-15
Nobody knows these things when we started.   Learning to use Unix-like OSes is like learning a new language. You can soften that curve by starting with a desktop.  In Linux, the difference between what a desktop can do and what a server can do is dictated by which packages you install.   On a desktop Linux install, you can install any server programs.   

The server-stuff will still need manual configuration, but the desktop stuff is point-n-click for many things.  However, the real power comes from using the shell, not the GUI.  However, with a GUI, there are hundreds more attack vectors when compared to a Linux Server and GUIs eat resources that are better used for doing server work.

There are a few all-in-one Linux Server distros that make using it easier. These usually have a web front-end. Depends on what your main goals are with the system which might be best.  I usually just install Ubuntu Server and configure the specific services I want based on they risk factors.  For example, I keep external-facing services separate from internal-only services.  I also keep infrastructure services separate.  It 

No need to ever touch any Windows Server, ever.  I though MSFT discontinued WHS a few years ago. Yep. Not an option.
[https://blogs.technet.microsoft.com/sbs/2017/07/03/windows-home-server-2011-end-of-mainstream-support/](https://blogs.technet.microsoft.com/sbs/2017/07/03/windows-home-server-2011-end-of-mainstream-support/)

Partitioning is one thing I use a desktop ISO to perform if the disk is already being used. To modify partitions, those partitions cannot be in use.  Booting from a flash drive with a live-boot distro like any Ubuntu Desktop will allow modification. 

You can modify unmounted partitions using **fdisk** or **parted**. These are CLI tools.  Depending on what you need to accomplish, they are easy-to-difficult to use.

For someone new to Linux, this link is a good overview: [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)

---

### Post by mastablasta on 2018-09-18
> **karebo said:**
> 
I want to keep Ubuntu, and learn to use it, but to get started With my server I need another OS, maybe Windows Home Server.


Ok so you want a GUI. Then try Zentyal (comes with webgui as well as desktop GUI and runs Ubuntu underneath) or Openmediavault (webgui only but easy to use). 

> 
So the problem I face now is this: Is there an easy way to make partitions in Ubuntu Server, or should I rather make a fresh install and create partitions in the process?

since you prefer GUI you can boot into the desktop version (using live USB) and then use gparted to make partitions (don't forget to assign appropriate permissions to them).

---

### Post by karebo on 2018-09-18
Last night I found commands to install Xfce, and several hundred files installed, but it did not end
in the Xubuntu desktop Gui that I expected, but the command line. I searched in vain for a command line
to open Xubuntu. When I boot the computer today it seems to run through all the Xfce installation from yesterday,
but it does not end with the usual command-line, just a blinking cursor.
I am unable to write anything, so how do I get on from here?
I even removed the SSD from the computer and tried to erase the installation from the disc, but it was inaccessible for the
Windows Discmanager

---

### Post by TheFu on 2018-09-18
When you are new to Linux, many things that are possible aren't really recommended.  If you want a desktop, the best answer is to install the desktop variant you want, wiping the disk during the installation.

This will get a system that follows online guides for how things work and limit surprises.  A mixed server-desktop system will lack packages that desktop users will expect. That is only an issue if you need the desktop.  Server people will be fine managing the system like a server.  I actually prefer that for my desktops, but that is me. I'm odd. People tell me that all the time.  ;)

---

### Post by mastablasta on 2018-09-19
> **karebo said:**
> Last night I found commands to install Xfce, and several hundred files installed, but it did not end
in the Xubuntu desktop Gui that I expected, but the command line. I searched in vain for a command line
to open Xubuntu. When I boot the computer today it seems to run through all the Xfce installation from yesterday,
but it does not end with the usual command-line, just a blinking cursor.
I am unable to write anything, so how do I get on from here?


don't know how to get from blinking cursor (could be a GPU driver issue?!). try booting into older kernel (hold shift on boot to get grub menu selection) or boot to recovery mode. form the data porvided it is imposisble to say what you did and what the error was.

you were supposed to install xubuntu-desktop package not just XFCE. if you installed only XFCE then you need to manually install the display manager a.k.a. login manager (probably gdm but there are others available). the manager then loads after boot and this is the point where you select username and enter password. remember linux is a modular system. this means whole parts of the OS can be changed. windows just has one display manager, but linux has a couple of them and you can choose the one you want. if you install the desktop package all this is installed for you. but you only installed the desktop environment (XFCE). 

[https://www.makeuseof.com/tag/choose-switch-linux-display-managers/](https://www.makeuseof.com/tag/choose-switch-linux-display-managers/)

---

### Post by karebo on 2018-09-19
Thank you mastablasta.
I had Ubuntu server already installed, and if I got it right, Ubuntu + Xcfe = Xubuntu.

There is no GPU issue. I had an older 2,5" HDD that I exchanged with the SSD in question, and there was no problem
setting BIOS to boot and install from USB to the old HDD.

I will try your suggestions for getting the command line and hopefully enable the SSD to load an OS from USB.
I have realized that it will be too time-consuming for me to get acquainted and familiar with Ubuntu, so maybe I should try
Plex or Amahi

---

### Post by TheFu on 2018-09-19
> **karebo said:**
> Thank you mastablasta.
I had Ubuntu server already installed, and if I got it right, Ubuntu + Xcfe = Xubuntu.
<snip> 

I have realized that it will be too time-consuming for me to get acquainted and familiar with Ubuntu, so maybe I should try
Plex or Amahi

Xubuntu is a group of programs plus the core Ubuntu and XFCE desktop.  In theory, the programs installed would be tuned for the XFCE theme and not as heavy as the suite of programs installed with a full Ubuntu Gnome3 desktop.

Plex is a program, not an OS. BTW, you don't need a plex account or need to use any plex clients to access the media it manages.  I've been running plex media server on  a server system here for at least 4 yrs now.  It is accessible from anywhere in the world - all without a plexID.

Amahi?  Looked it up.   Seems it is a group of media-centric programs installed over either Fedora or Ubuntu OSes.  Think I'll load it into a VM today and check it out.  Many of the things Amahi is trying to accomplish to make adding more programs/features are solved using either snaps or containers on standard Ubuntu.  

Regardless, choice is a good thing. Perhaps if you say what it is you want the system to accomplish, someone here can make suggestions more to your skill level and needs?

---

### Post by mastablasta on 2018-09-19
> **karebo said:**
> 
I had Ubuntu server already installed, and if I got it right, Ubuntu + Xcfe = Xubuntu.



correction - in this case it would be Ubuntu **desktop** + XFCE = something similar to Xubuntu

Xubuntu uses a few other applications/programs.

Ubuntu server on the other hand is command line only version of Ubuntu operating system. it also preinstall many things needed for server.

Zentyal server for example (by default - or at least it used to do it by default) installs desktop, but it also installs WebGUI (which means you can access the server from another PC via browser).

i am not sure what you are trying to do or what you will use the server for. but if you plan to use this as media server then i suggest you look into Openelec or Kodi. both should be easy to install. there are others there as well. if this is a media server then you definitely do not need any desktop.

---

### Post by TheFu on 2018-09-19
"Media Server" means different things to different people.  Usually, what people want is a mix of place to store their media AND a playback machine. Some want a way to record TV as well. If that is your goal, and you don't mind the noise from the PC, then something like Kodi is an excellent choice.  

If you want to record TV, then you'll need a tuner device that works in your location with either OTA or whatever paid TV service you have. I have antennas in the attic and use a few network-based TV tuners from Silicon Dust.  The tuners are available to any computing platform on the same subnet using DLNA.  I can watch TV (sports) on an Android tablet while smoking ribs out back, for example.  Where I live, there are over 90 channels "broadcast" OTA.

OTOH, if "media server" means a place to store and stream media FROM, not actually consume, then something like Plex Media Server or miniDLNA or one of the 10 other "servers" would be better.  You can still use Kodi as a client, I do, to play the media.  I use OSMC for playback from a plex server. OSMC is a raspberry-pi distro of Kodi designed for silent media consumption from  10 ft away using just a TV-style remote control.  I don't use any plex client software, just DLNA-capable software from PC, Linux, Android, and Kodi client machines.

But the Plex Server is on a headless (no monitor) "server" running Ubuntu.

---

### Post by karebo on 2018-09-21
Thank you
1) The services I want my server to render are: store, primarily videos, playback (that is viewing on my TV screen [LEFT]cabled to the computer), and remote access over the internet.
so that would mean that I should install both Kodi (for playback to cabled TV) and Plex (for internet Access)?
2) I am stuck in a curious problem though: My SSD is blocked. After installing Ubuntu server and adding Xfce, I am unable to boot from USB, that is, I am unable to install any other software
or erase the disc. When I set BIOS to boot from USB, this message appears for some Seconds: " error: cant find command hwmatch", then Ubuntu server starts.
Any suggestions to what I could do to make BIOS boot from USB? 
[/LEFT]

---

### Post by mastablasta on 2018-09-21
> **karebo said:**
> Thank you
1) The services I want my server to render are: **store**, primarily videos, **playback** (that is viewing on my TV screen [LEFT][COLOR=#222222][FONT=Verdana]cabled to the computer), and **remote access** over the internet.
so that would mean that I should install both Kodi (for playback to cabled TV) and Plex (for internet Access)?
[/FONT][/COLOR][/LEFT]

remote access to files is best done via sFTP (using SSH). remote playback (streaming) is another thing.

Kodi will play the media on cabled TV.

i don't know about the other issue. i am not sure what xfce has to do with booting from SSD or how it would even block it. are you saying it doesn't boot at all?
and from USB  - are you saying you can't boto into any OS from USB as well? not even a live desktop linux?

---

### Post by karebo on 2018-09-21
The other issue, 2): I would like to install Kodi, on the same SSD where Ubuntu server is now installed.
To do that I will of course have to download and "burn" Kodi on a USB stick and set BIOS to boot from it.
This is impossible, because after having set BIOS to boot from USB, the computer boots from SSD-Ubuntu (starting with this error Message I mentioned)
Could this be an UEFI/BIOS issue? I believe Rufus "burned" Ubuntu in UEFI mode.
Preferably I would like to keep Ubuntu, if I succeed in accessing USB on booting, hopefully being asked in the process to create a New partition,
but that is another matter, now the problem is to be able to install anything at all.
I have tried putting in another, empty HD in the computer, and booting from USB Works fine.

---

### Post by TheFu on 2018-09-21
Plex isn't necessary for internet access, but it can make it easier if you don't mind that organization having access to your media.

For streaming over the internet, there are multiple solutions to access the plex webGUI without a plex account/ID.  You can either setup a SOCKS proxy via ssh or setup a VPN using any of the VPN solutions like openvpn, WineGuard, AlgoVPN (IPSec), whatever.

With a VPN, android clients can have easy access to your entire home network, which is secure, and can be handy.  If you setup a nextcloud instance, then you have sometime like dropbox + calendaring + contacts under your control that doesn't need some outside "cloudy" provider.

You can install kodi with apt-get install. No need for a separate boot setup.  Kodi is a DLNA client/renderer which will connect to any DLNA server like Plex, miniDLNA, whatever.  It can also connect directly to storage, but if you have multiple clients, having a central plex server really is nicer.
I use Kodi from multiple places in the house with the PlexBMC addon to have nice access to a headless Plex Server. Remote streaming of music, I use multiple different methods, nextcloud, plex webGUI, or just a local copy on a microSD card in the phone.  Streaming video over the internet is more of a trick to me. I try to respect other people's bandwidth.  It is just easier to put video onto a flash drive for playback later.

I can't help with the boot issue besides check your BIOS boot settings.

Had an SSD go read-only a few weeks before it died completely. I was lucky.  Sometimes they just stop working, no warning. It never worked again after that. Get your daily backups perfect and either replace it ASAP or start planning to replace it for when it never works again.

---

### Post by karebo on 2018-09-21
Here is what I did: paid 32 USD for the Windows 10 compatible utility EaseUS that efficiently erased the SSD and created two partitions. So now I am ready to install Utilities for my server.
Acronis True Image that I have installed on all my computers was unable to erase the SSD

---

### Post by TheFu on 2018-09-21
A free alternative is **dd**. It can erase any storage that allows erasing through the driver, period. There are many others.
In the Linux world, paying for software happens very infrequently, if ever.

There are many things that are different from the Windows ecosystem in Linux.

---

