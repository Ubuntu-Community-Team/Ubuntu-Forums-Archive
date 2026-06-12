---
title: "How Do I Access Software Over Server???"
date: 2007-02-21
forum: Server Platforms
---

### Post by smileyClan on 2007-02-21
I am a CS major and a complete newbie to Ubuntu (and to Linux in general).  My boss is running the newest Ubuntu server and has asked me to create a website that allows users to login and use Open Office applications (mainly the word processor and spreadsheet).  He has these products installed on his server, and he wants to be able to have others log on to his server and use these applications without having to install them on their local machines (which could be running either Windows or Linux).  He wants to allow multiple people to use the applications at the same time. 

I have done quite a bit of web design, so I am taken care of there - I just don't know how to access the software on his server and allow others to use it without installing it locally.  I have no idea where to even start on this...  Does anyone have any pointers that can get me started in the right direction?

:confused:

Thanks

---

### Post by kidders on 2007-02-22
Hi there and welcome,

I'm not quite sure how you intend to make something like OpenOffice accessible over the web. Ordinarly, a user would expect to be able to launch remote applications over SSH, an RDP, or perhaps a VPN. In such environments, it would make no difference to the server whether the user running the application was local or not.

---

### Post by evilspoons on 2007-02-22
Well, if you wanted to be a sneaky bugger, you could have it create a VNC session that accessed a desktop with the programs you need, and then pass that VNC session to the user through a Java VNC applet (I believe the UltraVNC project has one).

This seems sort of moronic though, and a huge security hazard if it's not set up right, plus it'd be really hard to get files off of the server to the user and printing would be a nightmare.

An alternative would be to just do X-forwarding through SSH, but this is painfully slow, and on windows you'd have to install Cygwin-X, which is more difficult to set up than just installing OpenOffice in the first place.

---

### Post by PilotJLR on 2007-02-22
VNC is the only real option here... unless you have linux client and use X forwarding over SSH, as the other posters mention.

Using a term services / vnc like service to provide ONLY certain apps (and not an entire desktop environment) would require a Citrix presentation server.

---

### Post by wayne_za on 2007-03-17
The only success I had to use remote apps was using XDM and running X terminal

Running Remote X Applications on Gnome would be GDM
 [http://www.ubuntuforums.org/showthread.php?t=98670]("http://www.ubuntuforums.org/showthread.php?t=98670")

---

### Post by Frosty Cold Drink on 2007-03-17
What you will want to do is set up on-demand VNC sessions. You can use Xvnc (should be in the vncserver package) with xinetd to create VNC sessions on demand and tie them to a GDM session. don't password protect the VNC connection as the user will have to log in via the display manager anyway.

Then create a custom session for the user(s). Your session file can be a simple shell script that runs a minimal window manager OpenOffice without firing up Gnome. So long as you don't background anything, the session will drop with OpenOffice closes.

---

### Post by johnbradbury on 2007-03-27
I've been looking at converting to Linux myself over the past few weeks and as a Windows Systems admin I've started my research by looking for direct replacements for MS products and setups.

In this instance for Windows I'd be using Terminal Services with a third party software product. The most popular is Citrix but you can find cheaper alternatives. However using MS software for this type of setup would require pretty deep pockets.

In Linux I've been looking at LTSP-5 which is included as part of Ubuntu 6.10, this can provide a thin or web client with access to a full desktop and it's installed applications. 

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/WebHome](http://wiki.ltsp.org/twiki/bin/view/Ltsp/WebHome)

Hope this helps

---

