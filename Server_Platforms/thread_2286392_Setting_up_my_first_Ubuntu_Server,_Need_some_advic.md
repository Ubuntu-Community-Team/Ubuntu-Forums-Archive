---
title: "Setting up my first Ubuntu Server, Need some advice"
date: 2015-07-11
forum: Server Platforms
---

### Post by JusticeEmpire on 2015-07-11
Hi All,

I've got some old kit that I want to put to use, and some ideas I'd like to implement. I've spent the last four nights researching, and I just seem to be going round in circles and getting myself confused.

I have an old PC, that I installed Ubuntu on some time back, and all I've really done is some tor browsing. Separately, I have an old ReadyNAS unit that I recently upgraded the hard drives on, and I would like to have a RAID system. This issue I have with this is that the hardware is very old, in a hot environment, not setup properly, and I don't want to invest time and effort into it when I don't trust the hardware.

I like the idea of having a combined NAS Server, and there are some very tempting chassis on the market. But I like the idea of putting something together myself, I installed Ubuntu because I wanted to learn more with Linux and programming in general. 

So I have a plan of action, but I will need some help along the way. I don't mind spending out a little bit on upgrading mobo/cpu, RAM, NIC, RAID card etc, but at the moment, I need to try and understand some of the fundamentals. 

I want the server to do a few KEY things :

1 - Central File storage, separated for different users, password protected directories etc
2 - Secure Remote Access
3 - Continuous Backup (I'm thinking of reusing ReadyNAS unit to backup my backups)
4 - Cross Platform Access (Think I need SAMBA for this?)
5 - Media Streaming (Fairly certain I want to use Kodi for this?) - and using Raspberry Pi as clients

I feel fairly comfortable in Ubuntu's desktop GUI coming from windows, and I do mind if I need to up my resources a bit to compensate for that, but I'm still not comfortable with CLI yet.

Any thoughts, suggestions, or quick and easy step by step guides would be muchly appreciated, and I will keep this updated with progress, screenshots or pics :)

---

### Post by Bucky Ball on 2015-07-11
*Thread moved to **Server Platforms**.*

You may have better luck here. ;)

---

### Post by JusticeEmpire on 2015-07-12
Ok, cheers buddy, fingers crossed :)

---

### Post by tgalati4 on 2015-07-12
Welcome to the forums.

Search the web for blogs on setting up Ubuntu.  There are many that document the steps for home servers that perform similar steps.  You probably want to stick to an Long Term Support version (LTS) such as 14.04.

Just type in:  "blog setting up Ubuntu 14.04 home server" in your web browser.

You will get many hits:  [http://www.htpcbeginner.com/install-ubuntu-server-14-04/](http://www.htpcbeginner.com/install-ubuntu-server-14-04/)

You have a list of 5 items.  I would focus on one and then ask specific questions about that item.  

Since you are familiar with the Ubuntu desktop, you can install a lighter desktop such as MATE, which will run well on older hardware and still run all of your services.  So my first suggestion is to install a lightweight, desktop, LTS version of Ubuntu, then try implementing one of your items (such as incorporating the ReadyNAS as a backup system), then ask questions as they come up.

---

### Post by JusticeEmpire on 2015-07-12
Hiya,
Thanks for the response.
I had looked into Ubuntu Server version, looked a little scary, but I will give it a go. I'll also check out MATE as I would prefer a desktop.
Good suggestion on that, it is a work in progress so make sense to make logical steps.
My first step is getting the software installed before relocating the unti into my rack in the garage, so I will get on with that and ask the questions as I go.
I was thinking of using CrashPlan for the backups, wise choice?

I've already found one thing.........my hardware is TOO slow. I have 2gb DDR2 800 RAM, Pentium E5200 2.5GHz (Dual Core) and ASRock 4Core1600-D800 motherboard, and it takes around 1.5-2 seconds to open up a window.......................I am going to try and install on there, but I am also going to have a look round to upgrade the hardware. I know I need a new NIC (this one only 100mb) I want a small SSD for OS, so I will have a look later on, get all the bits ordered, then when they come in, refit and then install 64-bit version.......
If I manage to get the software installed before upgrading hardware, will let you all know :)

Ok, well, after various issues, it appears that I have the OS installed. But it's saying that I have 200 packages that can be updated, and 140 of them are security. So, I now need to go and find out how to do that. I've tried apt-get install update but that doesn't seem to work

---

### Post by TheFu on 2015-07-13
There are many different ways to attack this. I think you are biting off a bunch for someone new to Linux.  Windows may appear to be similar, but that is just the outside. Inside they are VERY different OSes. There is an elegance and simplicity to Unix systems. Once the general ideas are understood, everything else starts to make sense ... except systemd and pulse-audio. ;)

That machine is absolutely fine for your needs. Just use a lighter desktop - add xfce4 or lxde or mate or .... there are 20= desktop  options.  Then remove Unity.  **Unity is the issue, not the RAM and not the CPU.** Unity is more about the GPU, but a strong CPU helps.  How much "cheese" do you really need and how much are you willing to pay?

Also - there isn't any need for an SSD.  File servers and media streaming don't need it and the OS already is tuned for disks. Sure an SSD will make boot 12 sec instead of 20 sec, but a file server won't be rebooted very often - perhaps once a month or 2.

So - where to start?
1) install and secure the box - lots of how-tos for that. gufw is probably the firewall GUI you want. Block everything except ssh for now.
2) setup ssh for remote access. Install fail2ban or denyhosts to block brute force attacks. ssh access is userid specific.
3) setup ssh-keys for remote access - this is more secure AND more convenient. Disable ssh logins using passwords.
4) Use sftp to access your files from anywhere in the world, securely. This uses ssh-keys too. There are great sftp clients for every OS that has networking. sftp is part of openssh-server - you've had it working since step 2. If you want to allow friends to have sftp access but not ssh - there is a setting.
5) setup remote desktop for access from anywhere in the world - x2go uses ssh, so you don't have to open any new router ports or firewall rules.
6) move your media over - use Linux file systems for this - life will be much easier if you avoid NTFS.
7) install Plex Media Server to serve video/audio/photos on the network. It isn't F/LOSS, but it is free and works extremely well. Any DLNA client can access the file on the server. No need for Kodi on this box. Put Kodi with PlexBMC on the r-pi if you go that way - I think people are going with a custom install from Elec for that.  I use a chromecast, roku and WD TV Live as DLNA clients, but much prefer the Kodi+PlexBMC solution. The chromecast is very picky about audio and video codecs - basically everything I've recorded from TV has to be transcoded for the chromecast.  If you must transcode for playback, you'll want a CPU with 2000+ Passmarks for the Plex Server.
8) setup a VPN-Proxy server ... to whenever you are remote and must connect to an open wifi, you can force all traffic to go through your home server and network. sshuttle does that. Don't know about Windows clients.

You mention wanting a faster NIC.  This probably will not help with internet file transfers at all. The WAN probably isn't that fast and uplink probably isn't more than 3-25Mbps.  If you do get a new NIC - I strongly recommend an Intel PRO/1000 - this is THE standard for GigE cards - PERIOD.  They are available new for $25, so there really isn't any reason to save $10 for something cheap that won't have the same throughput and might not "just work" when dropping into the slot.

Windows systems can access the files over sftp using winscp or filezilla. You can connect to a remote desktop from windows using the x2go-client (use the PPA to install the server-side).

That should be enough to get you started.

Let me see what the other items there are ... 
ah - a NAS server ... for OSX and Linux clients, use NFS. It is faster and makes network storage appear like local storage.  CIFS network storage for Windows ... meh.  I use it only for HOME directory access. Setting up HOME access per userid is pretty easy. Just be aware that SAMBA security sucks. It is an issue with the protocol. scp/sftp are better, but don't support live editing, so CIFS is expected in a Windows network.  CIFS is implemented in samba and only useful for network file access. It isn't really "cross-platform", IMHO.

Personally, I would avoid RAID - get your backups working first. RAID never replaces backups - automatic, daily, versioned, backups are critical. When RAID fails, you'll want a backup to restore from. Check these forums for all the RAID failures that couldn't be recovered because someone didn't have backups too.  There are 3 types of RAID - SW, Fake, HW.  SW is extremely flexible, but a little slower. I cannot think of **any** good reason to use FakeRAID (the RAID provided on MBs and cheap RAID cards). It generally provides the slow performance of SW-RAID, but ties the storage to the exact RAID HW on the MB. HW RAID is great if you buy 2 identical cards and really need the performance. The LSI ($350+) models are good, but definitely check for specific Linux kernel support.

The best suggestion I have is to get over the shell fear. Learn it, love it, use it.  Learn to be a "power user" with the shell ASAP.  There is a free PDF book here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  GUIs almost always make us slower. By scripting things, you can make it faster, reproducible, consistent. Those are key to being a good admin.  In a professional environment, 1 admin can manage 100 different systems if they are not the same. If they are the same, 1 admin can manage 100K systems, easily.  Just sayin'.

Sorry that I went on. Had too much time this morning. ;)

---

### Post by Bucky Ball on 2015-07-13
> **TheFu said:**
> 

That machine is absolutely fine for your needs. Just use a lighter desktop - add xfce4 or lxde or mate or .... there are 20= desktop  options.  Then remove Unity.  **Unity is the issue, not the RAM and not the CPU.** Unity is more about the GPU, but a strong CPU helps.  How much "cheese" do you really need and how much are you willing to pay?



+1. Forget Unity for a server. Xfce4 would do fine or the others TheFu mentions ...

---

### Post by TheFu on 2015-07-13
BTW - I looked up the passmark for your CPU.  

Until last week, my file/media/plex/kodi box was running an AMD dual-core APU with less than 50% performance for the last 3-4 yrs. 

For transcoding reasons, I decided to replace the AMD with something a little faster (680 passmarks for 20W and more power hungry 45W) and use the APU box as a pfsense router. Why?   Plex transcoding for hidef streams - the new MB+CPU runs about $100 total and provides 4000 passmarks (all other components were laying around here). I think you'll be fine - just blow out the dust from the case. 

Both my systems had GigE networking already that "just worked" with Linux. Used iperf to run a test just now:```

$ iperf -c istar
------------------------------------------------------------
Client connecting to istar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.6 port 49359 connected with 172.22.22.20 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.10 GBytes   943 Mbits/sec
```

I can live with that. Going in the opposite direction was 941 Mbits/sec. Reasonable for a GigE network. Real world file transfers don't come near that ... disks, encryption get in the way a little - usually only see 55-75MB/s (note the switch to megabytes) - and closer to 55-60 (480Mbps) most of the time. Even with SSDs, that is true.

---

### Post by JusticeEmpire on 2015-07-14
Hiya,

Thanks for the very thorough response :)

I think I made a typo, I meant unit in terms of the physical sense of the computer/server. I managed to get the updates done :) I know it is a bit of a leap, but the best way to learn is to do

I haven't got any GUI installed yet, someone else has mentioned MATE so I will look into that. Think I'll have to spend a couple of hours having a look through the various options.

But that's definitely a very good starting point so thanks for that. I can see why those numbers  would matter, but at the moment I am no way near the stage of working all of that out.

Same with scripts, I definitely want to do some exploring with that, part of the reason I'm venturing into linux land. As an example, I'd like to make a script to search for duplicate files when I've consolidated all of my data :)I

I'll let you know when I've made some progress

Ok, well, I have attempted to install MATE. I got stuck because I had installed GUFW first. But now that I have downloaded/installed the package, nothing new has happened. I rebooted, and it takes me straight back to CLI. Tried to look on the website for information, not much there at all. Is there something simple that I have missed, or should I just try and install a different desktop?

---

### Post by tgalati4 on 2015-07-15
You might be missing some pieces.  On my system (Linux Mint 17 MATE based on 14.04):

> tgalati4@Mint17 ~ $ apropos mate
atril (1)            - The MATE Document Viewer
caja (1)             - The MATE File Manager
chat (8)             - Automated conversational script with a modem
Class::Accessor (3pm) - Automated accessor generation
du (1)               - estimate file space usage
eom (1)              - The Eye of MATE Image Viewer
ico (1)              - animate an icosahedron or other polyhedron
marco (1)            - The MATE Window Manager
mate-about (1)       - Learn more about MATE
mate-about-me (1)    - is a control center applet.
mate-appearance-properties (1) - is a control center applet.
mate-autogen (1)     - generates all makefiles for MATE packages
mate-calc (1)        - (mate-calculator) - The MATE Desktop Environment Calculator
mate-calc-cmd (1)    - A console calculator for the MATE Desktop Environment.
mate-default-applications-properties (1) - is a control center applet.
mate-desktop-item-edit (1) - A small tool to edit .desktop files.
mate-dictionary (1)  - Look up words on dictionaries
mate-disk-usage-analyzer (1) - A graphical tool to analyse disk usage
mate-doc-common (1)  - include the standard user documentation build files
mate-gsettings-toggle (1) - wrapper for MATE gsettings keys
mate-notification-properties (1) - Set up the options for desktop notifications
mate-panel (1)       - The Panel for the MATE Desktop Environment
mate-panel-test-applets (1) - display and test installed applets
mate-power-manager (1) - mate power manager userspace daemon
mate-power-preferences (1) - mate power preferences gui
mate-power-statistics (1) - mate power statistics gui
mate-screensaver (1) - The MATE Desktop Screensaver and Locker
mate-screensaver-command (1) - The MATE Desktop Screensaver and Locker
mate-screensaver-preferences (1) - Configure MATE Screensaver
mate-screenshot (1)  - capture the screen, a window, or an user-defined area and save the snapshot image to a file.
mate-search-tool (1) - the MATE Search Tool
mate-session (1)     - Start the MATE Desktop Environment.
mate-session-properties (1) - Configure applications to start on login.
mate-session-save (1) - End or save the current MATE session
mate-settings-daemon (1) - Handles the MATE session settings
mate-system-log (1)  - the MATE System Log Viewer
mate-system-monitor (1) - (unknown subject)
mate-terminal (1)    - The MATE Terminal Emulator
mate-volume-control (1) - The MATE Volume Controller
mate-volume-control-applet (1) - The MATE Volume Applet
mate-wm (1)          - Start the window manager configured by the user
matedialog (1)       - display GTK+ dialogs
mozo (1)             - MATE Menu Editor
pluma (1)            - The MATE Text Editor
x-session-manager (1) - Start the MATE Desktop Environment.
xfs_estimate (8)     - estimate the space that an XFS filesystem will take


What happens when you:

```
startx
```

---

### Post by JusticeEmpire on 2015-07-15
I had thought that, so tried this [http://askubuntu.com/questions/481104/mate-not-showing-up-after-install](http://askubuntu.com/questions/481104/mate-not-showing-up-after-install) but it didn't seem to work.

After it boots up, I get CLI to login into server, and then a prompt. I tried 'startx' but it says : The program 'startx' is currently not installed. You can install it by typing sudo apt-get install xinit

---

### Post by tgalati4 on 2015-07-15
It's possible that you are missing it, or Ubuntu MATE uses something different from xinit to set up the X-Windows environment.  Linux Mint MATE is different from Ubuntu MATE, so understand that there may be differences in how it is set up.

> tgalati4@Mint17 ~ $ apt-cache policy xinit
xinit:
  Installed: 1.3.2-1
  Candidate: 1.3.2-1
  Version table:
 *** 1.3.2-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
tgalati4@Mint17 ~ $ man xinit


---

### Post by JusticeEmpire on 2015-07-15
Turns out I was missing it. Installed it, ran startx, and now have a desktop, thanks :) anyway to make it boot into that automatically without logging in and running startx?

I'm struggling with the SSH side of things, probably due to confusion. I've got the gufw installed, but have to disable it everytime I want to download. Added a rule that only allows SSH in/out on port 22. Got fail2ban installed, although doubt it's setup correctly, followed a tutorial and didn't get a 'pong' response from sudo fail2ban-client ping. Couldn't seem to get x2go installed, and slightly confused about its purpose. 

I work better graphically, so I will draw a simple block diagram and post it, to make sure I am understanding it right.

Also worth noting, I have a crappy router. ISP suppler --->[http://electronics360.globalspec.com/article/3410/netgear-super-hub-2-vmdg485-wireless-router-teardown](http://electronics360.globalspec.com/article/3410/netgear-super-hub-2-vmdg485-wireless-router-teardown)

I do want to change it, as I don't think I can get any remote access from it, from what I remember tinkering with in the past. Someone has recommended Draytek to me, any good?

---

### Post by tgalati4 on 2015-07-15
You need a desktop manager (which contains the login scripts) to automatically start the desktop environment.  

Let's focus on one thing at a time.  You have several things going on and I can't figure out which way is up.

If you install the desktop version of Ubuntu MATE or Linux Mint MATE, everything works out-of-the-box.  When you install the server version and add stuff, you get a half-baked operating system for a new user.  The server version is for advanced users that have 10 years of experience with linux.

I believe that Linux Mint MATE is using the mdm desktop manager.  It's possible that Ubuntu MATE uses the *lightdm* desktop manager.  I don't know.  I'm not running it.

> tgalati4@Mint17 ~ $ apt-cache policy mdm
mdm:
  Installed: 1.6.9
  Candidate: 1.6.9
  Version table:
 *** 1.6.9 0
        700 [http://packages.linuxmint.com/](http://packages.linuxmint.com/) qiana/main amd64 Packages
        100 /var/lib/dpkg/status
     0.1.3-2.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
tgalati4@Mint17 ~ $ apt-cache policy lightdm
lightdm:
  Installed: (none)
  Candidate: 1.10.5-0ubuntu1.1
  Version table:
     1.10.5-0ubuntu1.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     1.10.0-0ubuntu3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages


Some differences between mdm and lightdm:  [http://www.webupd8.org/2012/06/how-to-use-lightdm-instead-of-mdm-in.html](http://www.webupd8.org/2012/06/how-to-use-lightdm-instead-of-mdm-in.html)

---

### Post by JusticeEmpire on 2015-07-15
Hmmmmm, so are you saying that I shouldn't have installed the server edition of ubuntu?

---

### Post by tgalati4 on 2015-07-15
Do you have 10 years of linux experience?  Edit:  Servers require quite a bit of knowledge to set up and maintain.  If you have the time and inclination, go for it.  If you want a more polished linux learning experience, install a Desktop version, so you can use programming IDE's, research tutorials, watch installation videos, etc.  Otherwise you will need to set up two computers:  a server, and a Desktop client machine so you can do all the development and research work to get the server to work correctly.

You might consider changing the Title of this thread:  Setting up my first Ubuntu Server,  Need some advice.

---

### Post by Bucky Ball on 2015-07-16
> **tgalati4 said:**
> 

You might consider changing the Title of this thread:  Setting up my first Ubuntu Server,  Need some advice.

Not sure OP can due to post count and elapsed time since thread was posted.

A title descriptive of what you are after support for is *_always_* a good idea, though, and will improve greatly improve your chances of support, so if JusticeEmpire would like title changed and can't change it via 'Go Advanced' on the first post, feel free to PM me with a title suggestion and I will change.

---

### Post by JusticeEmpire on 2015-07-16
No, I don't have 10 years experience with Linux or servers. In fact, I have NO experience of servers, and a tiny bit of linux (I installed Ubuntu desktop once). My 'desktop/client' machine is my work laptop, running windows. This is what I use 99% of the time, and hence why I need the server to support cross platform, as there are a lot of programs on this I used for work, and I intend to back up the laptop daily onto the server.
I went for the server edition after a couple of days researching. I was under the impression that was the right choice, as from what I can gather, installing server edition then installing desktops etc, was far more secure than installing desktop edition and then installing server bits........... am I wrong?

Fair comment about thread title, I will see if I can change that.

---

### Post by tgalati4 on 2015-07-16
Security is only an issue if you port-forward a bunch of ports on your router and use simple passwords for your ssh server.  But now you should explore using ssh keys for passwordless login.  If you have a browser on the desktop version with a lot of add-ons installed, some of those add-ons could be a security risk.  So yes, using a Desktop Environment with extensive web access could be more of a security risk than a minimal server.

Have you read the server documentation?

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

If you just want a backup solution, I would use a USB external drive and some backup scripts.  It's a lot easier than setting up a linux server.

---

### Post by JusticeEmpire on 2015-07-16
Yeah, I had read something along those lines, and hence why I went for the server edition. I've gone through some of those pages, but not all of them.

I've got 4 x 8TB drives in my NAS at the moment, and as they are fairly new, I want to get them into some hardware that I trust. I know I could buy a box, but I'd rather learn and build myself, and that's how I found myself here.....

---

### Post by tgalati4 on 2015-07-16
Well, building a server for learning services is different from just building a NAS.  For that you can look at *freenas*, which is a BSD-flavored NAS operating system that you can also add services to.

Again, if you are new to linux, just install an LTS Desktop linux distro, because there is a steep learning curve that will take the better part of a year to feel comfortable.  Then after that year, you can build another box as a minimal server.  Otherwise, you will spend a lot of time configuring things that work out-of-the-box with the Desktop version and it's easier to research and fix things with the multiple workspaces available on the Desktop, versus trying to do everything through an ssh terminal session.

---

### Post by JusticeEmpire on 2015-07-17
I do understand it's different, when I was researching, I learnt about NAS servers, and from what I read, it's the way to go. Doesn't make much sense to have two separate boxes, when they can be combined into one. I've seen freenas crop up a few times, will look into it. 

I have done some SSH before with Putty, when I was setting up my bitcoin miners, I just lack the practice

---

### Post by tgalati4 on 2015-07-17
The purpose of having two boxes becomes clear when you break your server but still have a working computer so you can continue to work.  If you break your work machine--and it is your only machine--then you have a problem.

Over time you will appreciate the difference between a development machine and a production machine.  If you only have one computer, then you don't have a choice.  But used computer equipment is cheap, so if you really want to learn, try building a few different machines:  NAS, home server, game machine, etc.  Yes, you could build one super machine to perform all of those functions, but then configuring it will be a challenge.

---

### Post by Bucky Ball on 2015-07-17
> **JusticeEmpire said:**
> 

I want the server to do a few KEY things :

1 - Central File storage, separated for different users, password protected directories etc
2 - Secure Remote Access
3 - Continuous Backup (I'm thinking of reusing ReadyNAS unit to backup my backups)
4 - Cross Platform Access (Think I need SAMBA for this?)
5 - Media Streaming (Fairly certain I want to use Kodi for this?) - and using Raspberry Pi as clients



This may sound ludicrous, and bear in mind I am no server guru, but couldn't you also use a RPi as the server as well? Does the ReadyNAS attach USB? You could then install the server .iso on the Pi and SSH to it from your desktop via Putty. :-k

That way you could tweak around and learn about servers using the RPi and learn about Ubuntu desktop on your laptop/desktop.

---

### Post by JusticeEmpire on 2015-07-17
@ tgalati4 - Yeah, that's a fair point, hadn't considered that. In that case, I do think I might be better off looking at a solution like FreeNAS, and then using something like the RPi as suggested, as a learning/development environment........In fact, building different machines and then combining into one super machine would be a REALLY good learning curve, and much more achievable rather than trying to jump straight into the super computer. It would also allow me to get something up and running a lot quicker :)

@ Bucky Ball - Yeah, I had thought along those lines, and I think it is possible. It's a good suggestion, and I probably will tinker with that, but I don't trust my current NAS hardware. That is probably want I need to address first and foremost. Get my new NAS system built and my data secured, then start 'adding' bits to the system and progress my way up to the server

---

