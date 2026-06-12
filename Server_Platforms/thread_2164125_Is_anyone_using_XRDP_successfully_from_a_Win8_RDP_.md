---
title: "Is anyone using XRDP successfully from a Win8 RDP client?"
date: 2013-07-30
forum: Server Platforms
---

### Post by Chris of Arabia on 2013-07-30
Whilst I'm managing to connect successfully to my box (64-bit 13.04 server +  KDE) using RDP and have no problems seeing the screen, or accessing the menus, I can't to be able to control the contents of any applications I open. 

For example, I was trying to run the Muon Package Manager earlier, and whilst it opened without issue, every time I mouse over the window that opened, the cursor remained as the double-arrowhead icon that's normally used for resizing a window. Nothing I tried would allow me to select any of the buttons or fields within the Muon window, though I can obviously resize it.

At the moment, that makes the use of RDP pretty much redundant for me. I've had something of a search around, but I can't see similar issues being reported, or at least not that I can readily identify, nor does anything at xrdp.org help.
I'm open to any suggestions or alternatives.

---

### Post by TheFu on 2013-07-30
FreeNX server and any nx-client. There's a FreeNX how-to guide for Ubuntu - google finds it easily.  NX works over SSH, so you'll need to run an ssh server on the remote machine - even inside your own LAN. This also means that NX is secure from anywhere in the world. Thankfully, NX is much more efficient than RDP or VNC protocols, so using it from anywhere is not usually an unpleasant experience.

---

### Post by Chris of Arabia on 2013-07-31
OK. Thanks for that. I'll take a look later on.

---

### Post by lah7 on 2013-07-31
I've just tested this by connecting to my Ubuntu 13.04 Desktop using the Remote Desktop Client on Windows 8.1 (Beta) and I have no issues.

Using "vnc-any" to connect to 'localhost' to give me the Unity desktop as it is to the physically logged in user, interacts with no problems. I also tried the "sesman-Xvnc" module to start a concurrent session, which uses the GNOME Classic environment ("gnome-session-fallback") and again, there are no problems with controlling my apps.

Does this happen with any RDP clients (try your distribution's built in one) or just from the Windows 8 system? Also, which desktop environment does XRDP use?

---

### Post by Chris of Arabia on 2013-08-01
Well yesterday kind of got wiped out and I didn't manage to get too much done on there at all. However, by way of an update

> **TheFu said:**
> FreeNX server and any nx-client. There's a FreeNX how-to guide for Ubuntu - google finds it easily.  NX works over SSH, so you'll need to run an ssh server on the remote machine - even inside your own LAN. This also means that NX is secure from anywhere in the world. Thankfully, NX is much more efficient than RDP or VNC protocols, so using it from anywhere is not usually an unpleasant experience.

I've installed both SSH and FreeNx  on the Ubuntu server, and the NoMachines NX client 3.5.0-9 on my Win8 PC. Everything looks to have installed correctly, but when I try to connect, the NX client runs through its connection sequence, shows a black full screen window for perhaps 5 seconds, then shuts itself down again. Looking at the log file reads as follows:

> Info: Display running with pid '9024' and handler '0xe08f8'.
NXPROXY - Version 3.5.0
Copyright (C) 2001, 2011 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.
Info: Proxy running in client mode with pid '5376'.
Session: Starting session at 'Thu Aug  1 18:35:04 2013'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'kde'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '12000'.
Session: Session started at 'Thu Aug  1 18:35:04 2013'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Thu Aug  1 18:35:11 2013'.
Session: Session terminated at 'Thu Aug  1 18:35:11 2013'.


I've checked that the freenx-server is running, and it says that it is. The NX client gives every appearance of trying to connect then, but looks to be being refused, though it doesn't actually say as much.

> **lah7 said:**
> I've just tested this by connecting to my Ubuntu 13.04 Desktop using the Remote Desktop Client on Windows 8.1 (Beta) and I have no issues.

Using "vnc-any" to connect to 'localhost' to give me the Unity desktop as it is to the physically logged in user, interacts with no problems. I also tried the "sesman-Xvnc" module to start a concurrent session, which uses the GNOME Classic environment ("gnome-session-fallback") and again, there are no problems with controlling my apps.

Does this happen with any RDP clients (try your distribution's built in one) or just from the Windows 8 system? Also, which desktop environment does XRDP use?

The RDP client I've been trying to use is the built-in Win8 one. I've not tried any others, mainly because it appears to work at it's most fundamental level, it just won't let me control apps once they're opened.

The desktop environment is the Kubuntu KDE SC Version 4.10.5 running on top of a 64-bit 13.04 server.

> time for tea...

Back in a bit

---

### Post by TheFu on 2013-08-01
> **Chris of Arabia said:**
> Well yesterday kind of got wiped out and I didn't manage to get too much done on there at all. However, by way of an update

I've installed both SSH and FreeNx  on the Ubuntu server, and the NoMachines NX client 3.5.0-9 on my Win8 PC. Everything looks to have installed correctly, but when I try to connect, the NX client runs through its connection sequence, shows a black full screen window for perhaps 5 seconds, then shuts itself down again. Looking at the log file reads as follows:

I've checked that the freenx-server is running, and it says that it is. The NX client gives every appearance of trying to connect then, but looks to be being refused, though it doesn't actually say as much.

Back in a bit

About NX ... 
Did you just install FreeNX or did you install it AND follow the manual setup instructions at the ubuntu freenx howto link?  There are 3 extra steps, but it is worth it - security AND performance is greater with NX.  Let me google for the page I mean ... "ubuntu freenx howto"  found it - first link: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)   So, did you retrieve and run the **nxsetup** script? Did you copy the resulting ssh-key to the client machine(s)?

BTW, I didn't change the default sshd listening port here, on the server.  I use port translation on the router and have it listen on a high port that redirects to 22 on the server.  When I'm outside the network (around town or the world), I connect to that high port for NX connections.

Does ssh work without NX? If it doesn't, NX will never work.

If you've done these things, then look for the log file on both the client AND the server - look for errors, warnings inside each. Usually, there is a clear error describing whatever the issue is. That has been my experience.

About RDP ... 
I know that Since Win-Vista, Microsoft's RDP implementation has included more security. I thought the server-side needed to reduce to the legacy version for Linux clients to work properly - I don't know if the Windows-RDP client needs to do that to connect to Linux RDP servers - sorry, I just don’t know.  I only use RDP from Linux-TO-Windows.

---

### Post by Chris of Arabia on 2013-08-01
OK, I think I'm a little closer than I was. It looks like the step I've missed is getting the public key across to the client. I've run out of day though, so I'll be taking another look in the morning. Many thanks for the help so far.

---

### Post by Chris of Arabia on 2013-08-02
I have been using the same 'Howto' as you've linked to there, which did include running the **nxsetup** script on the initial installation.

Since then, things have moved on a little...

The disappearing black screen has been replaced by a black screen that stays on screen until I close it myself. There are no error messages though, but it shows no sign of displaying what's on the server.

SSH does look to be working, as I can connect from the same Win8 PC using PuTTy.

The bit that's puzzling me now is the use of the encryption keys. Both public and private keys have been created, and I can see them sitting there on the server in /root/.ssh/ - what I'm scratching my head over is a) Do I ***need*** to use them? And b) How do I get the public key onto the Win8 box?

it is all a bit slow going with me I'm afraid, but I'm finding I'm having to re-learn an awful lot all over again. It's been quite a while since I spent time with Ubuntu, and it shows. So thanks again for all the help, it really is appreciated.

---

### Post by TheFu on 2013-08-02
I don't think root/.ssh/ has anything to do with my NX setup.  My setup uses the nx userid and keys from that user. The public key needs to be entered into the nx-client software, and your login credentials via NX GUIs are your userid and password.  In this way, both a key AND password are necessary - something you have and something you know. Good security practice.

So, I guess the first thing to check is whether an nx userid was created on your system and if the ~nx/.ssh/ directory has a public key inside that you can get to the NX client.  On my nx server machines, the keys are in /var/lib/nxserver/home/.ssh/

I think this section of the guide is what you might be missing: [https://help.ubuntu.com/community/FreeNX#Using_custom_SSH_keys](https://help.ubuntu.com/community/FreeNX#Using_custom_SSH_keys)

---

### Post by Chris of Arabia on 2013-08-03
I've tried running through the section you pointed me at (not the one that continues on to "Using Custom SSH keys on Lucid", I don't seem to be getting the results I'd expect. First thing I checked was the **/var/lib/nxserver/home/.ssh/** directory, and I could see a **client.id_dsa.key** file there that was created on 1 Aug. Given that I'd not previously run through this section of the guide, it seems logical that this was the default key mentioned.

I then ran through the line...

> sudo dpkg-reconfigure freenx-server

...and got the 'OK' prompt, selected 'Create new custom keys', then selected 'SSH'. At that point, it dropped out of the 'Configuring freenx-server' dialogue, back to the PuTTy shell, with the message 'Not starting FreeNX server, it's already started'. I've tried this a couple of times now, both with FreeNX stopped and started. Checking back in the **/var/lib/nxserver/home/.ssh/** directory, I can see that the same default key created on 1 Aug is still there untouched, though as I've not been asked to provide a password or create a key, this isn't a surprise at this point.

The other thing I've not spotted going through this is any request to either create, or inform me of, an nx userid. Is there somewhere specific I can look for that, or should it be one of the key creation steps?

---

### Post by Chris of Arabia on 2013-08-09
I've not been back to this since my last post, as I'm still sure how to proceed with it. I've been working instead on other aspects of my setup (see elsewhere), and have largely been working though PuTTy, or directly on the box itself. At some point though, I would like to be able to get the ability to remote into the desktop sorted out. Any offers of additional help on the position set out above would be appreciated.

---

### Post by lah7 on 2013-08-09
> **Chris of Arabia said:**
> I would like to be able to get the ability to remote into the desktop sorted out. Any offers of additional help on the position set out above would be appreciated.

I think we should identify which end is being problematic. If this is only affecting the Windows 8 client, and no other remote desktop application on any other platform, perhaps this is an issue with the settings used to establish the connection on the client? If it happens to any remote desktop client, then we know it's a problem on the server's end.

For example, if I was to attempt to connect using an 8-bit colour mode session, everything looks distorted, so I must use 16-bit colours or better.

If you discover it's affecting any client, it may help to share with us what processes are running on your system during your remote session:
```
 ps -u USERNAME
```
[SIZE=1]*Where USERNAME is the user you logged on as.*[/SIZE][COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]
It could potentially be a window manager or service that's not giving your applications focus, making them non-controllable. In the event we've discovered this is client side, the RDP technology or your connection settings used in Windows 8 may well be incompatible with XRDP *(which would be odd because it works for me in the W8.1 Beta)*, in which I suggest using an older version of the MSTSC client or another one altogether.

If you want, you may wish to try a different desktop environment (such as LXDE or gnome-session-fallback) in which we can identify that it's a bug or glitch with KDE.

We know so far you're using:
> [COLOR=#000000]Kubuntu KDE SC Version 4.10.5 running on top of a 64-bit 13.04 server[/COLOR]

Once we know which side is problematic, we'll be able to sort out XRDP (or the client) in no time. :)

---

### Post by Chris of Arabia on 2013-08-09
OK, thanks for that. I'll get some details pulled together in a little while, as I'm just about to head out and do a few things. I will be back though.

---

### Post by Chris of Arabia on 2013-08-10
I guess 'being out' lasted longer than I'd anticipated, but anyway...

I'll try and give you as much information as I can about what the system is and how it's all connected, as well as any other options I have for testing out where the problem may be.

[LIST=1]
[*]Firstly, the Ubuntu server itself
[LIST]
[*]O/S: Ubuntu 64-bit server 13.04, with the KDE desktop installed on it
[*]Mobo: MSI P35 Platinum
[*]CPU: Intel(R) Core Duo E4600
[*]RAM: 8Gb
[*]HDD: 2x 320Gb WD drives set up as a RAID1 pair (software RAID)
[*]GPU: [Nvidia GeForce 8400 GS]("http://www.geforce.com/hardware/desktop-gpus/geforce-8400-gs")
[/LIST]

[*]Other available clients
[LIST]
[*]Windows 8 Pro desktop - main client I've been testing from using:
[LIST]
[*]Win8 built in RDP client
[*]PuTTy
[*]NX Client
[/LIST]

[*]Windows 7 Home laptop - not tried yet
[*]Windows XP netbook - not tried yet
[*]Apple iPad2 - tried using:
[LIST]
[*]Remoter VNC app
[*]Also, see attached screen shot down below
[/LIST]
[/LIST]

[*]Local home network
[LIST]
[*]Based around a Netgear WNR2000 with a 10Mb internet feed behind it
[*]Win8 Pro desktop and Ubuntu server are on a wired connection to it
[*]All other devices connect via WiFi
[*]I'm not attempting to access the Ubuntu server from outside the LAN
[/LIST]
[/LIST]


The processes running at the moment are:

```
Last login: Fri Aug  9 13:52:29 2013 from eeyore2.local
chris@PIGLET2:~$ ps -u chris
  PID TTY          TIME CMD
 3458 ?        00:00:00 kio_http_cache_
 4590 ?        00:00:00 startkde
 4636 ?        00:00:00 ssh-agent
 4639 ?        00:00:00 dbus-launch
 4640 ?        00:00:00 dbus-daemon
 4706 ?        00:00:00 start_kdeinit
 4707 ?        00:00:00 kdeinit4
 4708 ?        00:00:00 klauncher
 4710 ?        00:00:11 kded4
 4718 ?        00:00:00 kglobalaccel
 4724 ?        00:00:00 kwalletd
 4728 ?        00:00:02 kactivitymanage
 4729 ?        00:00:00 kwrapper4
 4730 ?        00:00:01 ksmserver
 4740 ?        00:00:05 kwin
 4747 ?        00:00:01 knotify4
 4750 ?        00:01:56 plasma-desktop
 4754 ?        00:00:00 ksysguardd
 4760 ?        00:00:00 kuiserver
 4762 ?        00:00:00 mission-control
 4783 ?        00:00:00 nepomukserver
 4785 ?        00:00:02 krunner
 4786 ?        00:00:00 nepomukcontroll
 4788 ?        00:00:01 nepomukservices
 4791 ?        00:00:00 kmix
 4795 ?        00:00:00 pulseaudio
 4810 ?        00:00:51 virtuoso-t
 4827 ?        00:00:00 nepomukservices
 4828 ?        00:00:00 nepomukservices
 4853 ?        00:00:00 polkit-kde-auth
 4854 ?        00:00:00 klipper
 4983 ?        00:00:00 ck-launch-sessi
 4984 ?        00:01:33 Xvnc
 5020 ?        00:00:00 ssh-agent
 5023 ?        00:00:00 dbus-launch
 5024 ?        00:00:00 dbus-daemon
 5034 ?        00:00:00 x-session-manag
 5037 ?        00:00:00 dbus-launch
 5038 ?        00:00:00 dbus-daemon
 5097 ?        00:00:00 start_kdeinit
 5098 ?        00:00:00 kdeinit4
 5099 ?        00:00:00 klauncher
 5105 ?        00:00:00 kglobalaccel
 5113 ?        00:00:00 kwrapper4
 5116 ?        00:00:00 ksmserver
 5122 ?        00:00:00 kwin
 5124 ?        00:00:00 kactivitymanage
 5130 ?        00:00:00 knotify4
 5134 ?        00:01:38 plasma-desktop
 5141 ?        00:00:00 ksysguardd
 5145 ?        00:00:00 kwalletd
 5149 ?        00:00:00 kuiserver
 5151 ?        00:00:00 mission-control
 5171 ?        00:00:00 nepomukserver
 5173 ?        00:00:00 nepomukcontroll
 5176 ?        00:00:01 krunner
 5178 ?        00:00:00 kmix
 5204 ?        00:00:00 polkit-kde-auth
 5210 ?        00:00:00 klipper
 5231 ?        00:00:00 akonaditray
 8011 ?        00:04:24 kscreenlocker_g
 9130 ?        00:00:00 at-spi-bus-laun
 9627 ?        00:00:00 ck-launch-sessi
 9628 ?        00:00:06 Xvnc
 9662 ?        00:00:00 ssh-agent
 9674 ?        00:00:00 x-session-manag
 9677 ?        00:00:00 dbus-launch
 9678 ?        00:00:00 dbus-daemon
 9737 ?        00:00:00 start_kdeinit
 9738 ?        00:00:00 kdeinit4
 9739 ?        00:00:00 klauncher
 9741 ?        00:00:00 kded4
 9745 ?        00:00:00 kglobalaccel
 9747 ?        00:00:00 drkonqi
 9751 ?        00:00:00 kwrapper4
 9752 ?        00:00:00 ksmserver
 9761 ?        00:00:00 kwin
 9763 ?        00:00:00 kactivitymanage
 9769 ?        00:00:00 knotify4
 9773 ?        00:00:06 plasma-desktop
 9780 ?        00:00:00 ksysguardd
 9784 ?        00:00:00 kwalletd
 9788 ?        00:00:00 kuiserver
 9790 ?        00:00:00 mission-control
 9811 ?        00:00:00 nepomukserver
 9814 ?        00:00:00 nepomukservices
 9815 ?        00:00:00 krunner
 9816 ?        00:00:00 nepomukcontroll
 9818 ?        00:00:00 kmix
 9820 ?        00:00:00 khelpcenter
 9830 ?        00:00:00 khelpcenter <defunct>
 9843 ?        00:00:00 polkit-kde-auth
 9849 ?        00:00:00 klipper
 9873 ?        00:00:00 systemsettings
 9902 ?        00:00:09 kscreenlocker_g
 9991 ?        00:00:00 ck-launch-sessi
 9992 ?        00:00:02 Xvnc
10026 ?        00:00:00 ssh-agent
10038 ?        00:00:00 x-session-manag
10041 ?        00:00:00 dbus-launch
10042 ?        00:00:00 dbus-daemon
10101 ?        00:00:00 start_kdeinit
10102 ?        00:00:00 kdeinit4
10103 ?        00:00:00 klauncher
10105 ?        00:00:00 kded4
10109 ?        00:00:00 kglobalaccel
10111 ?        00:00:00 drkonqi
10118 ?        00:00:00 kwrapper4
10119 ?        00:00:00 ksmserver
10125 ?        00:00:00 kwin
10127 ?        00:00:00 kactivitymanage
10133 ?        00:00:00 knotify4
10135 ?        00:00:04 plasma-desktop
10142 ?        00:00:00 ksysguardd
10146 ?        00:00:00 kwalletd
10150 ?        00:00:00 kuiserver
10152 ?        00:00:00 mission-control
10172 ?        00:00:00 nepomukserver
10174 ?        00:00:00 krunner
10176 ?        00:00:00 nepomukservices
10177 ?        00:00:00 nepomukcontroll
10180 ?        00:00:00 kmix
10182 ?        00:00:00 khelpcenter
10192 ?        00:00:00 khelpcenter <defunct>
10209 ?        00:00:00 polkit-kde-auth
10225 ?        00:00:00 klipper
10263 ?        00:00:05 kscreenlocker_g
10373 ?        00:00:00 ck-launch-sessi
10374 ?        00:00:01 Xvnc
10408 ?        00:00:00 ssh-agent
10420 ?        00:00:00 x-session-manag
10423 ?        00:00:00 dbus-launch
10424 ?        00:00:00 dbus-daemon
10483 ?        00:00:00 start_kdeinit
10484 ?        00:00:00 kdeinit4
10485 ?        00:00:00 klauncher
10487 ?        00:00:00 kded4
10491 ?        00:00:00 kglobalaccel
10493 ?        00:00:00 drkonqi
10498 ?        00:00:00 kwrapper4
10500 ?        00:00:00 ksmserver
10507 ?        00:00:00 kwin
10509 ?        00:00:00 kactivitymanage
10515 ?        00:00:00 knotify4
10517 ?        00:00:03 plasma-desktop
10525 ?        00:00:00 ksysguardd
10529 ?        00:00:00 kwalletd
10533 ?        00:00:00 kuiserver
10535 ?        00:00:00 mission-control
10555 ?        00:00:00 nepomukserver
10557 ?        00:00:00 nepomukcontroll
10560 ?        00:00:00 krunner
10562 ?        00:00:00 kmix
10564 ?        00:00:00 khelpcenter
10574 ?        00:00:00 khelpcenter <defunct>
10589 ?        00:00:00 polkit-kde-auth
10606 ?        00:00:00 klipper
10621 ?        00:00:04 kinfocenter
10677 ?        00:00:01 kscreenlocker_g
10874 ?        00:00:00 sshd
10875 pts/3    00:00:00 bash
10981 pts/3    00:00:00 ps
chris@PIGLET2:~$

```

Given what I'm seeing at the Win8 PC and the iPad screenshot below, it looks as if I'm getting the error regardless of the client, but I'll happily go and try one of the other devices listed and see if I'm seeing the same problem on those two. Whilst I can't see it on that particular screenshot, I'm getting the same double headed cursor over any application window and can't control anything within it, but the lower tool/task bar behaves as expected. You can launch things from it, but not control them thereafter.

The screenshot also shows something that I'd completely forgotten about, which is the KDE Daemon Crash Handler message. I'd only seen it once before (on the iPad), and until I tried connecting it this morning to see if the problem with controlling applications was there also, well... I am guessing that this may well be relevant to the problem at hand. For the record, that doesn't show on the Ubuntu server at all, but is now showing if I connect from the Win8 PC using RDP, so I'm wondering whether that's something the iPad connection is causing and now shows elsewhere too.

I think that's perhaps as much pertinent information as I can provide at the moment, but if you need anything more specific over and above that, I'll dig it out for you.

If I can avoid it, I'd rather not swap desktop environments, but that's mainly down to wishing to minimise the amount of messing around with the install more than anything.

Let me know what you think.

[ATTACH=CONFIG]245247[/ATTACH]

---

### Post by Chris of Arabia on 2013-08-10
Just for completeness, I've now tried RDP into the Ubuntu server from both the Win7 laptop and the XP netbook; both exhibit the same symptoms, including the KDE Daemon Crash Handler message.

---

### Post by Chris of Arabia on 2013-08-11
In relation to the KDE Daemon Crash, I went looking for a suitable log file to see what, if anything was being reported there, only to find that there was no daemon.log file created at the time of install. As I'm not too sure whether this has any bearing on the remote connection problem, I started a [separate thread]("http://ubuntuforums.org/showthread.php?t=2166772") in the Absolute Beginners section to deal with that problem, but felt it would be worth cross-referencing here also, in case it is material.

---

### Post by Chris of Arabia on 2013-08-13
Apologies for the bump - can anyone assist, based on the additional information?

---

### Post by steeldriver on 2013-08-13
So do you want to persevere with FreeNX? or try again with xrdp?

I have played with xrdp, I *may* be speaking out of turn but my understanding is that (at least with the repository version) the xrdp 'server' is really just an intermediate layer that talks to Xvnc - in which case you're probably better off using a native VNC client (TightVNC, UltraVNC, Real VNC) on the Windows side unless the Windows 'Remote Desktop Connection' client is absolutely your only option. KDE probably has a default 'Desktop Sharing' VNC application, or if you want multiple separate sessions you can install tightvncserver. I use tightvncserver to run a remote session on Windows 7/TightVNC all day from a 13.04 box at work (although I use a lighter desktop session e.g. LXDE or Openbox).

FreeNX is supposedly faster than VNC but I have not tried it

---

### Post by Chris of Arabia on 2013-08-14
I suppose my preference is to continue down the RDP/XRDP route, as I'd prefer to be sticking with something that is a part of the default Win8 installation - essentially making life easier on that side of the equation, and then concentrating of having the 13.04 server respond to it. I went with XRDP because that was what I learned should be able to offer me the functionality I was looking for, and a little research suggested it worked well/was straightforward to set up.

FreeNX at this point, is something I have tried, but has been even less successful, as I can't see the KDE screen on that (something I can do via the RDP route). From what I see so far, that is a more complex route to making a remote session possible, as it involves installation/configuration on either side.

VNC is something I've heard of, but have never used, and know very little about. Again, it looks to be a little more complex, with setup needed on either side.

I'm not against using something other than RDP - they are my devices, so I can do pretty much what I like with them - but I would like to resolve the issue with it, rather than keep trying alternative solutions if I can, or at least until that has proved an unviable way forward. So far, I've not seen anything to suggest it won't work, so I'm willing to keep plugging away at it, if suitable advice can take me in that direction.

---

### Post by TheFu on 2013-08-14
You've already been working this for 2 weeks?
VNC should be a 30 min setup tops.
FreeNX should be a 15 min setup tops.
Clients should be 2 min.

I'm sorry that we've failed. We've failed to ask the correct questions and we've probably assumed too much because your replies have always been clear, concise and what we requested.

I completely agree that you should concentrate on the single solution that works for your platforms. NX doesn't have clients for iPad or Android that I've seen, so that could be a show stopper for you.

I don't run non-LTS releases. This is part of the reason why. I just want my systems to work. 12.04 is the current LTS release.

Running KDE in a remote session over a WAN will suck. Over a wired LAN, there will be a little lag, but it should work. Almost everyone I know always drops back to a simpler DE when they use remote desktop tools.  Could it be that you ARE seeing a remote X/Windows session, but don't recognize it?  By default, X is a blank screen. We have to click to see anything ... right or left click to see the root menu.

On the VNC-server side ... inside the**  ~/.vnc$ more xstartup **
```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
fvwm2 &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
/usr/X11R6/bin/fvwm-themes-start &
```
I have that small script.  It forces a "sane" fvwm2 setup for my remote sessions. fvwm is not really good for the uninitiated, so run whatever DE you want on that line instead and remove the last line. In fact, you can probably just put the 1 line of code that starts your desired DE in this file.

I haven't attempted RDP into a Linux machine .... ever and I don't have Win8 anywhere (don't plan to every run it).

Again, sorry we've failed. Hope this somehow helps.  At this point, it might be easier to start over from scratch, find a new "how-to" and follow those directions.

---

### Post by Chris of Arabia on 2013-08-14
It has taken a little while, but I don't want to be seen as offering criticism on the subject. I'm well aware that everything here is done on a voluntary basis, and am happy to learn from those with more experience. I work for an IT company in the Middle East, but as an Account/Project Manager. If you think what's happening here is on the slow side, you wouldn't believe what passes for support here at times... ;)

I'll take a little time later today to digest what you've responded with, then see what I want to do next. I'll readily admit I'm a Linux/Ubuntu beginner, so may well have set off down the wrong track to start off with, and should perhaps have started off with the question "What tool should I use to achieve xxxxx?". If I've picked the wrong tool for the job, then so be it - I do want to digest what you've said first though, and parse into something my (notreallyatechie) brain can make sense of.

I do genuinely appreciate the help though, and am at times baffled at some of the questions you manage to make sense of.

---

### Post by TheFu on 2013-08-14
You have been extremely helpful and kind.  I have friends in Egypt and Turkey. Visited my friend in Istanbul last fall.  We are as frustrated - perhaps moreso - than you.  This stuff sorta "just works."

I think using VNC is probably the best solution for you. It is the path that most people follow, so more people will have tested and used the exact same setup as you have with VNC.  Reading this [http://www.ubuntututorials.com/remote-desktop-ubuntu-12-04-windows-7/](http://www.ubuntututorials.com/remote-desktop-ubuntu-12-04-windows-7/) how-to makes it seem trivial. If those instructions don't work ... there must be something basic that you and we aren't seeing.

For example, can your Win8 PC "ping" the ubuntu server by name and can the Ubuntu server ping the Win8 PC by name?  I'm really asking if you have DNS or /etc/hosts configured on both machines.  If not, please always use the IP addresses.

---

### Post by Chris of Arabia on 2013-08-14
OK, a little more reading then.

The ping test was interesting. From the Win8 PC, I can ping the server by name (PIGLET2) and it responds in 1ms, even though I've never actually set anything up on there to tell it that PIGLET2 = 10.0.0.100 (static) - it has worked that out for itself with no intervention from me.

Doing the reverse though, the result is different. Using the PC name (eeyore2), the server comes back with 'Unknown Host'. This doesn't surprise me though, as I've done nothing to set up anything on the DNS side. That said, my level of knowledge suggests that this wouldn't work anyway, as the PC uses DHCP from my Netgear router and could have any one of 254 other IP addresses allocated to it when it's powered on. It will respond to the currently assigned IP address though (10.0.0.213); if left running this was averaging a response time of around .57ms, but when the -c limiter was used to send a single ping, it was around 1.25ms. Nothing about those numbers suggest I have anything to concern myself about on a networking side.

Just for clarification, so far I've only accessing the server via it's IP address, whether that be by RDP, PuTTy, FileZilla, or FreeNX, though I know that both Firefox 22.0 and IE10 will respond to either IP or name addressing.

Anyway, I'll go do that reading. :)

---

### Post by TheFu on 2013-08-14
Is there a firewall running between or on these systems?  
Is the network a /24?  i.e. is the netmask no both machines 255.255.255.0?
Sorry - I'm reaching for straws here.

---

### Post by Chris of Arabia on 2013-08-14
The Win8 PC is running McAfee Internet Suite - checking through the settings on that, it's configured to trust all addresses from the 10.0.0.* range, and I can also see that there are no restrictions on RDP accessing either the internet, or the LAN, and its port is set to 3389, as is the /etc/xrdp/xrdp.ini config file on the server. The subnet mask is 255.255.255.0

On the server, I discovered that UFW must have been installed by default when I did the build. I've now added GUFW to that and can see that UFW is actually turned off. The subnet mask here is again 255.255.255.0

On the Netgear router, there is just one static IP setup for the server, DHCP for everything else, and the subnet mask is again 255.255.255.0. There's nothing I can see in there that would restrict LAN traffic, though the firewall is operating on the WAN side of things.

Strictly speaking, the Netgear is really just behaving a LAN switch using 192.168.0.2 as its own IP, the connection to the ISP sits forward of that, with a Huawei router acting as its gateway to the ISP themselves (they have the service locked down by the Huawei MAC address I think).

All that said, it's my feeling that it's not a network issue I've got here. As I can actually see the KDE via RDP, but not control the applications once they are opened from the task bar. If it were a networking or firewall setting, then I'd be inclined to think that I wouldn't see the KDE at all; something I have been able to do using both wired and WiFi connected devices so far.

Gut feel says this is either a config issue on the server, or just possibly something to do with the GPU.

---

### Post by steeldriver on 2013-08-14
I agree - if you get as far as 'seeing' the KDE desktop then networking is not your issue (except possibly bandwidth limitations)

FWIW I just fired up a Kubuntu 12.04 VM and installed xrdp from the repository, and was then able to connect from the Win7 host without any further configuration, using the VM's bridged IP (i.e. exactly as if the two machines were on a physical LAN) and choosing the default sessman-Xvnc session (that's the only one that works iirc, unless you build xrdp from scratch with libxrdp support). I was able to open a terminal, and a browser, and browse to the ubuntuforums.org page.

---

### Post by lah7 on 2013-08-27
My apologies for taking so long to reply from when the thread started. I thought I had subscribed to the thread... :-s

**I believe this may be a bug!** Anyone can re-create this problem by firing up a live CD of Kubuntu 13.04 and installing XRDP using apt-get through the terminal. As soon as you connect and login with the username credential "Kubuntu", KDE starts and the Daeman crashes resulting in applications having improper control behaviour as the original post states.

**Here's a screenshot of what it looks like on the RDP client:**
[IMG]http://i39.tinypic.com/mhv96b.png[/IMG]

**Thank you steeldriver** for testing it with Kubuntu 12.04. This shows that there must be a newer package in Ubuntu 13.04's repositories that has broken the behaviour.

It's possible to solely use keyboard shortcuts to be capable of filling a bug report. I'm not experienced in this, since it can be easily recreated in a VM, I'd like someone to assist by completing a report if it hasn't been done already.

**As workarounds,** you can easily switch desktop environments (eg. LXDE) as suggested, wait for a daeman fix, wait until Ubuntu 13.10 for further fixes, or possibly try downgrading KDE to an older version. Of course, there's also VNC. If you're the only user of the server, a desktop screen sharing option via VNC could be used in conjunction with the "vnc-any" module in XRDP.

It's possible to re-create the problem, hopefully we can get it fixed! :)

---

### Post by Chris of Arabia on 2013-08-28
Thanks for the update. I've been out and about for the last week or so, so this hasn't been a top priority for me. I'll be starting to work on the server more though in the next few days, so I'll see if I can repeat what you did with a live CD (more likely USB) on a different device - most likely my laptop. I can't help out much with the bug report, as it's not something I've had any experience of, though I can but try.

Thanks again for getting back to this - very much appreciated. O:)

---

### Post by Chris of Arabia on 2013-08-28
Slight update - I managed to navigate around the error message using the tab and alt keys, only to find that it says there's not enough information there to issue a report. At that point, the crash handler exits and leaves the screen with just a clean desktop image. I'm not to sure where that leaves me in submitting a report - I'm assuming that's not the only way of doing it though.

---

### Post by lah7 on 2013-08-28
> **Chris of Arabia said:**
> only to find that it says there's not enough information there to issue a report.
I tried submitting a report too, and resulted in the same message. I'd like to do our bit by helping the developers fix the problem, but I'm not familiar with KDE or its bug report process, so I'm not the man. :( But if any others stop by in this thread and fancy helping out with this bug report, that would be appreciated since we *should* be able to re-create the situation.

---

### Post by WayneBrady on 2013-10-18
Hello,

sorry to say but i can confirm exactly this error in Ubuntu 13.10 and KDE 4.11.

I have to mention that i use a system without a physical monitor, so only putty and VNC access is possible. It happens after the start of the KDE which is part of the VNC configuration i use.

I can't also do any bugreporting because it says that no information can be collected.

Thank you for keeping us informed if error is fixed.

---

### Post by WayneBrady on 2013-10-20
Update: I found an error message in the syslog, will try to install debugging packages:

00007fff368e2930 error 4 in KSC_XRandR11.so[7f28aebb4000+a000]

---

### Post by Chris of Arabia on 2013-10-23
This is very odd. I updated to 13.10 a couple of days back and this evening thought I'd give RDP/XRDP another go, but not expecting much. It now works!

Why I have no idea, as I've not attempted to do anything much since my last post on the subject at the end of August. So I can't offer any help to anyone else who's having a similar issue. There are a couple of slight niggles with it, but the basic position is that's it's now usable.

---

