---
title: "VNC Sessions"
date: 2007-04-02
forum: Server Platforms
---

### Post by wellbeing on 2007-04-02
Hi,

I'm new to Linux (about 2 days of experience).  So far, I've managed to do most things that I need (which has been great - a real sign of how far Linux has improved since my previous attempts at adopting Linux)!!  Overall, the experience has been very good.

To be honest, I am trying to do something that I'm not 100% sure if it's possible, or what it's called - which makes it difficult for me to work out where to go next.

Current Ubuntu Installation
================
Version 6.10


Background
=======
I have a server PC set up that is connected to my home theater system.  It used to run Windows 2000 - but now runs Ubuntu.  I want to continue to use the server PC to perform background tasks (downloads, rss feeds, etc.) - but also to play videos and music.

I used to use UltraVNC to log into the server PC.  UltaVNC was established as a server service on the server PC.  This meant that I could do away with the keyboard, mouse and screen because I could log a user in over UltraVNC, before any user had logged in.

I had a system set up where I had the video card set up for (dual screens??).  This was a feature of the NVidia video card driver.  One half of the screen was directed to my projector.  The other half of the screen contained my day-to-day things (eg. RSS feeds, etc).  This allowed me to log into the server PC while someone was watching movies.  The idea was that I could still tinker with the server while others watched their movie uninterrupted.

The system worked quite well, although videos would often lose focus and shrink back to "non-maximised" view, cursors would appear over the movie if I shut down the UltraVNC session, etc.


Objective
======
I think there must be a better way of achieving this.  I was thinking something like the following.

1. Setup VNC on Ubuntu
2. Allow VNC to access the server PC on two different ports (eg. 5900 and 5901)
3. The port for 5900 accesses user "A", who is currently watching videos
4. The port for 5901 accesses user "B", who has ftp and RSS feeding pograms running.

The idea would be that user "A" and user "B" could log into the same serverPC at the same time without disturbing each other.

Alternatively, "A" and "B" could be the one user, but different virtual desktops.  Alternatively, there could be another way to achieve the same goal.


What have I achieved?
==============
I've read as much as I can find about VNC on these forums.
I've tried most of the instructions, with varying degrees of success.
I can use UltraVNC to access and control my serverPC, after i've logged in on the server PC.
I can log in on three ports, 0, 5900 and 5901.
Each port accesses the same user account and the same desktop
If I am running a movie on the server PC (ie. which shows the movie on the projector) then I can't do anything else with the server PC.


Advice
======
I would appreciate any recommendations for how best to achieve the goal I discussed above.
I would appreciate any references/guidance on how to implement the recommendation.


As I mentioned before, I am still new to Linux, so best not to assume I understand anything that your average Windows User (of 15 years experience) wouldn't know.

Thanks in advance for any advice.  I have managed to work around all other issues (eg. samba not being configured, disks not being detected or mounted, mpeg playback), except I have not gotten my Twinhan Visionplus DVB-T working.  Mind you, that's for another day.

Sincerely,



WellBeing

---

### Post by elst on 2007-04-03
This is feasible - Linux is a "multi-user" system and can simultaneously run multiple desktop sessions for multiple users. The confusing things about VNC are that the Windows and Linux versions work totally differently, and the Linux versions can be run in  a couple of different ways, depending on what you want to do.

I wrote this tutorial a while ago to try to explain the VNC configurations, and how to set them up: 

[http://www.elsn.org/main/VncOnLinux](http://www.elsn.org/main/VncOnLinux)

---

### Post by huygens on 2007-04-03
One thing that people coming from Windows do not know about Linux and UNIX running X Window is that VNC is not really needed. You can - what people call - export the display or use an X-Terminal.
Exporting the display is an ugly term to simply say that you can connect to your server using ssh, telnet, rlogin, etc. and launch from the command line a graphical application and it appears on the screen of your desktop computer :-)
For example, you are on desktopA and want to edit a file on Server1 using Text Editor (gedit). Basically you open a terminal on desktopA (Applications->Accessories) and type this:
```
ssh -CX Server1 -l username
```After providing the correct password, you are logged in. Then you can edit your hosts file for example by simply typing:
```
sudo gedit /etc/hosts
```And the Text Editor is displayed on your desktopA computer.

N.B.: it requires that desktopA is running an X Server to. If it is a Linux box, it is!

You could further play with this and even export the complete server display (the whole Gnome desktop environment) to your desktop. This is however a bit more complicate (but not difficult). If you are interested, I would suggest that you look how to configure your server as an X Server for X Terminals. The advantage over VNC is that you open a session of your own, so there can be another session already open by another user (now watching a video) and it is two completely different session. So you can crash yours without affecting the other.


And many more possibilities... :-)

---

### Post by elst on 2007-04-05
Good point - I've mostly stopped using VNC in favour of SSH myself.

> The advantage over VNC is that you open a session of your own, so there can be another session already open by another user (now watching a video) and it is two completely different session. So you can crash yours without affecting the other.

The Windows version of VNC works by "exporting" existing sessions, and would have the issue that you describe. The UNIX version of VNC works differently, and actually creates new X displays. Hence my warning :)

---

### Post by joshov on 2007-07-19
> **elst said:**
> This is feasible - Linux is a "multi-user" system and can simultaneously run multiple desktop sessions for multiple users. The confusing things about VNC are that the Windows and Linux versions work totally differently, and the Linux versions can be run in  a couple of different ways, depending on what you want to do.

I wrote this tutorial a while ago to try to explain the VNC configurations, and how to set them up: 

[http://www.elsn.org/main/VncOnLinux](http://www.elsn.org/main/VncOnLinux)

Is your link dead?  I cannot get it to load.

---

### Post by elst on 2007-07-20
> **joshov said:**
> Is your link dead?  I cannot get it to load.

Sorry - the server was being rebuilt. It's now up and running again.

---

