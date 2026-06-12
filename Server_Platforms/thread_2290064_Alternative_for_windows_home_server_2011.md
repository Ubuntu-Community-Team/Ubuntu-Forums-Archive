---
title: "Alternative for windows home server 2011"
date: 2015-08-09
forum: Server Platforms
---

### Post by Filipe_ribeiro on 2015-08-09
Hello guys, first off i want to say that i am almost completely unfamiliar with ubuntu.

There is the thing, i want to build a server with ubuntu server with similar features that i use on my whs 2011 is that possible?

I am looking for something similar to stablebit drive pool, plex, remote desktop (team viewer), install my printer on it, and making some renders on it (converting video files). I also want to know if i can log in the server via network using windows machines or android (es file explorer).
I will also use utorrent

I will have 4 clients using android devices and windows (mostly to use plex)

My cpu is athlon 5150, 6gb ddr ram, 3 drives (main 500gb, and 2x 2TB drives).
I have one FX 8320 that is just getting dust that i could use, but i use the athlon mainly for power saving (4 cores 25w)

Is it a good idead, or is it just better for a noob like me to stay out? I can read some tutorials if available 

Thx in advance

ps: can i install onedrive on ubuntu?

---

### Post by GrouchyGaijin on 2015-08-09
Have you done a Google search for a DIY nas?

---

### Post by Filipe_ribeiro on 2015-08-09
i just did, and i think that wont suit my needs, as i still need a decktop os to work on (remote), besides i dont think i can manage/setup it, that why i am still on whs because its easy to use and setup, but i like the linux idea, i would love to use it more.

I have 3 machines getting dust that i want install ubuntu on it, for media and basic internet use, and maybe one workstation if i do like ubuntu and if i can find the software i may need

---

### Post by GrouchyGaijin on 2015-08-09
I've been seriously considering a nas.  I think I may end up buying a WD My Cloud; based on what I've read on other sites and posts I've seen on the Ubuntu Forms, the My Cloud works pretty well with Linux.  I have two Ubuntu 14.04 machines and an Xbuntu 14.04 machine connected to my home network.  In my case, being able to log in and work on a desktop from a remote location is not as important as running my own cloud and being able to access files when I am on the road.

---

### Post by Mark Phelps on 2015-08-09
If your intention is to access the WD MyCloud outside your home, be sure to verify that is possible.  From what I've read, all WD is providing is a network-accessible storage solution, in this case, wireless.  And if that is the case, you won't be able to access it outside the range of your home wireless network.

---

### Post by GrouchyGaijin on 2015-08-09
It was my understanding that smart phones as well as Windows and Mac computers could connect pretty easily to the My Cloud via a link WD/Seagate provides when you set up the nas.
Ideally I'd be able to connect remotely from Linux as well, but as my employer has given me a Windows laptop - and administrator rights - I imagine that 95% of the time away from home I'd access the nas from Windows or my phone.

---

### Post by grahammechanical on 2015-08-09
My advice would be to install Ubuntu on a spare machine (it seems you have one) and find out if it is for you and in the mean time search for Linux equivalents to the Microsoft software that you are familiar with. This will start you off

[https://www.teamviewer.com/hi/download/linux.aspx](https://www.teamviewer.com/hi/download/linux.aspx)

[http://www.bit-tech.net/bits/software/2012/07/19/replace-whs/1](http://www.bit-tech.net/bits/software/2012/07/19/replace-whs/1)

What do you mean by "clients?" Paying customers? If so, plan the transition carefully.

Regards.

---

### Post by TheFu on 2015-08-09
> **Filipe_ribeiro said:**
> Hello guys, first off i want to say that i am almost completely unfamiliar with ubuntu.

There is the thing, i want to build a server with ubuntu server with similar features that i use on my whs 2011 is that possible?

I am looking for something similar to stablebit drive pool, plex, remote desktop (team viewer), install my printer on it, and making some renders on it (converting video files). I also want to know if i can log in the server via network using windows machines or android (es file explorer).
I will also use utorrent

I will have 4 clients using android devices and windows (mostly to use plex)

My cpu is athlon 5150, 6gb ddr ram, 3 drives (main 500gb, and 2x 2TB drives).
I have one FX 8320 that is just getting dust that i could use, but i use the athlon mainly for power saving (4 cores 25w)

Is it a good idead, or is it just better for a noob like me to stay out? I can read some tutorials if available 

Thx in advance

ps: can i install onedrive on ubuntu?

That is a bunch of questions.  "Server" doesn't have a GUI, so you will have a steep learning curve if you want to do it "correctly in the Unix way."  If you just want something that works and don't care about security too much, you can use an all-in-one server deployment. I've never used one of those - security matters too much to me for that.

For Linux servers, remote access is through ssh.  Across the house or from around the world, ssh is the same. It is secure, provided you don't use passwords. There is a server and client component. There are ssh clients for every networked OS in the world.  Plus when you install openssh-server, you get sftp for free. That provides secure access to your files from anywhere in the world - provided you don't use passwords.  For ssh, you should only use ssh-keys for remote access after the first 5 minutes on a server.

Plex Media Server - I assume you mean that, not "Plex" which is completely different.  Plex MS runs great on Ubuntu. Everything works as expected, including the real-time transcoding for lesser devices.

I hear that Teamviewer can be made to work, if you are stuck on that. It would run under WINE. I've never gotten over distrusting external solutions like this. If you have a server already, why not run this stuff on your own equipment where trusting some 3rd party isn't needed?

A remote desktop doesn't really make sense, as a "server" doesn't have any GUI.  For a home user, you could install a GUI. The best remote desktop, IMHO, is x2go. This runs over ssh (same port, authentication, etc that you've setup above) and performs about 2-3x faster than either VNC or RDP.  However, there are no clients for Android.  x2go clients work great for Windows, Linux and OSX.  If you use rdp or vnc, please do so inside an ssh-tunnel.

For drive pools there are probably 10 different choices. I don't know anything about the tool you list. Let's just say that if it is possible with storage, then there is a Linux solution. If you paid for it, there is a 10% chance it will work with Linux. The best Linux software is generally F/LOSS ($0).  

Printers ... can be trivial to install or impossible. It really depends on the printer and how smart YOU were in the purchase to get one that is well supported by Linux. These days, it isn't worth my time to struggle with printers and well supported laser printers run about $50.  I have a well-supported all-in-one inkjet that works perfectly too - just not under Windows. Drivers didn't make it through the XP--> Vista transition.

Making "renders" - huh?  If you mean transcoding there are lots of tools for that, but most are based on ffmpeg. In fact, most transcoding tools on Windows are based on ffmpeg too. Handbrake is popular for h.264/aac/mkv transcoding. It has a GUI.

PlexMS is a DLNA server, so all the normal DLNA clients work.

I've never used bittorrent stuff. Don't know anything about that - except most of the things people grab in my part of the world is illegal to get.

That APU is dated. It should be able to transcode 1 hidef file at a time.
Not much use for all that RAM. 2G would be overkill in that box for what you've described.

So ... that GPU won't be used for anything more than an 80x25 text screen if you install "Ubuntu Server."  When you select to install "server", you've said "I am not a noob."  The OS expects you will know how to setup networking, storage, and any servers/services/daemons you like. For a noob, the learning curve will be steep. 

If you are serious about learning Linux - start here: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) . Regardless, please read the first few links on that page to set your expectations and get over the initial shock.
If you just want to point-n-click - look for a media server distro on distrowatch.com and try that. Even then, you will have to type a little until you master autocomplete.

Linux is extremely powerful. This is mainly due to the flexibility, but with all that flexibility comes complexity.  This is fantastic for experts, but terrible for noobs.  Even the way your systems find each other on the LAN is different. There isn't any automatic way that works well for systems to find each other that works 100%.  I manage /etc/hosts files and set static IPs on all my devices. For portable devices, I let the router manage that with DHCP reservations.  That is completely different from the way Windows systems broadcast "I'm here, I'm here" all the time. Linux has something like that called Avahi, but I find it doesn't work very well and sometimes sucks 95% of the CPU until I kill it.  Lots of people use it and seem to like it.  hostname.local is how you access LAN systems running avahi. [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf) explains more.

So - you have lots of options and lots of choices.

Learning Linux is like learning a foreign language. Things that seem to be similar to what you've learned in some other OS often are not.

---

### Post by howefield on 2015-08-09
Duplicate threads merged.

---

### Post by Filipe_ribeiro on 2015-08-10
Ok thx guys, server ubuntu is not for me, too many stuff to learn, i think regular ubuntu may do it, and ty [                                                      [IMG]http://ubuntuforums.org/images/avatars/UF_Logo10_90.png[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=1087323")                                                                                     [**[COLOR=#000000]grahammechanical  and [/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")[B][COLOR=#000000][                                                      [IMG]http://ubuntuforums.org/customavatars/avatar1037685_1.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=1037685")                                                                                     [URL="http://ubuntuforums.org/member.php?u=1037685"][B][COLOR=#000000]TheFu.

[/COLOR][/B][/URL][/COLOR][/B][COLOR=#000000][COLOR=#000000]resuming my needs are:
remote access (so i can work on my home computer from my work)
Drive pool: so i can mix different hard drives and have auto backup from some folders i choose
Plex media server
Transcoding: i use convert to x video 
network file acess: from windows and android
And a printer

By clients i mean users that log into it, its mostly family at top 4 users.
ABout my cpu choice AM1 platform is not that old, i choosed it because its cheap and is quadcore, it does all i need.
About the ram, is i do up all of it, in fact i may need more remote use and plex use most of it, then utorrent always running and all the security software.

I go install ubuntu on my FX machine and try it
 

If ubuntu can do all that, i will be happy, i go read the links you guys provided to me, i apologies for my english, i learned it all only on the INTERNET  [/COLOR][/COLOR][B][COLOR=#000000][URL="http://ubuntuforums.org/member.php?u=1037685"][B][COLOR=#000000]
[/COLOR][/B][/URL][/COLOR][/B]

---

### Post by LHammonds on 2015-08-11
> **Filipe_ribeiro said:**
> There is the thing, i want to build a server with ubuntu server with similar features that i use on my whs 2011 is that possible?
Have you looked at [Zentyal](http://www.zentyal.org/)?  Their aim is to make a Linux version of Windows Small Business Office Edition that works with Windows PCs.

LHammonds

---

