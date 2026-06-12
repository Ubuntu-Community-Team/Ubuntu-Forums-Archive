---
title: "Remote desktop virtualized Ubuntu 17.10 in ESXi 6.5"
date: 2018-01-06
forum: Virtualisation
---

### Post by erikve on 2018-01-06
Hi all,

I'm new in the world of Ubuntu. I have a HomeLab created in ESXi 6.5, and also have a virtual machine of Ubuntu 17.10.
As virtualized ESXi virtual machines are only accessible via a remote desktop, I try to setup a decent access to the virtual machine via remote desktop. By serving over the internet I came across several possiblities; best option I found is an option with X11vnc.

As I'm pretty new in linux/Ubuntu I decided to follow a step-by-step [plan]("https://tecadmin.net/setup-x11vnc-server-on-ubuntu-linuxmint/") to make it work. However I'm facing probles in step 3 (manual start of the vnc-server), showing me an error which I cannot solve. The command "sudo x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /home/erik/.vnc/passwd -rfbport 5900 -shared" is showing me the following  message:


```
 --- x11vnc loop: 1 ---


 --- x11vnc loop: waiting for: 13927


06/01/2018 13:32:52 passing arg to libvncserver: -rfbauth
06/01/2018 13:32:52 passing arg to libvncserver: /home/erik/.vnc/passwd
06/01/2018 13:32:52 passing arg to libvncserver: -rfbport
06/01/2018 13:32:52 passing arg to libvncserver: 5900
06/01/2018 13:32:52 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 13927
**06/01/2018 13:32:52 -auth guess: failed for display=':0'**
**06/01/2018 13:32:52 -auth guess: since we are root, retrying with FD_XDM=1**
**06/01/2018 13:32:52 -auth guess: failed for display=':0'**

```

Since VNC is not working I believe error above is reason of it.

Apart from that. When starting 'x11vnc' from the command line I get following messages:

```
06/01/2018 13:34:52 x11vnc version: 0.9.13 lastmod: 2011-08-10  pid: 14059
06/01/2018 13:34:52 Using X display :0
06/01/2018 13:34:52 rootwin: 0x260 reswin: 0x2a00001 dpy: 0x81278250
06/01/2018 13:34:52 
06/01/2018 13:34:52 ------------------ USEFUL INFORMATION ------------------
06/01/2018 13:34:52 X DAMAGE available on display, using it for polling hints.
06/01/2018 13:34:52   To disable this behavior use: '-noxdamage'
06/01/2018 13:34:52 
06/01/2018 13:34:52   Most compositing window managers like 'compiz' or 'beryl'
06/01/2018 13:34:52   cause X DAMAGE to fail, and so you may not see any screen
06/01/2018 13:34:52   updates via VNC.  Either disable 'compiz' (recommended) or
06/01/2018 13:34:52   supply the x11vnc '-noxdamage' command line option.
06/01/2018 13:34:52 
06/01/2018 13:34:52 Wireframing: -wireframe mode is in effect for window moves.
06/01/2018 13:34:52   If this yields undesired behavior (poor response, painting
06/01/2018 13:34:52   errors, etc) it may be disabled:
06/01/2018 13:34:52    - use '-nowf' to disable wireframing completely.
06/01/2018 13:34:52    - use '-nowcr' to disable the Copy Rectangle after the
06/01/2018 13:34:52      moved window is released in the new position.
06/01/2018 13:34:52   Also see the -help entry for tuning parameters.
06/01/2018 13:34:52   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/01/2018 13:34:52   repaint the screen, also see the -fixscreen option for
06/01/2018 13:34:52   periodic repaints.
06/01/2018 13:34:52 
06/01/2018 13:34:52 XFIXES available on display, resetting cursor mode
06/01/2018 13:34:52   to: '-cursor most'.
06/01/2018 13:34:52   to disable this behavior use: '-cursor arrow'
06/01/2018 13:34:52   or '-noxfixes'.
06/01/2018 13:34:52 using XFIXES for cursor drawing.
06/01/2018 13:34:52 GrabServer control via XTEST.
06/01/2018 13:34:52 
06/01/2018 13:34:52 Scroll Detection: -scrollcopyrect mode is in effect to
06/01/2018 13:34:52   use RECORD extension to try to detect scrolling windows
06/01/2018 13:34:52   (induced by either user keystroke or mouse input).
06/01/2018 13:34:52   If this yields undesired behavior (poor response, painting
06/01/2018 13:34:52   errors, etc) it may be disabled via: '-noscr'
06/01/2018 13:34:52   Also see the -help entry for tuning parameters.
06/01/2018 13:34:52   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/01/2018 13:34:52   repaint the screen, also see the -fixscreen option for
06/01/2018 13:34:52   periodic repaints.
06/01/2018 13:34:52 
06/01/2018 13:34:52 XKEYBOARD: number of keysyms per keycode 7 is greater
06/01/2018 13:34:52   than 4 and 51 keysyms are mapped above 4.
06/01/2018 13:34:52   Automatically switching to -xkb mode.
06/01/2018 13:34:52   If this makes the key mapping worse you can
06/01/2018 13:34:52   disable it with the "-noxkb" option.
06/01/2018 13:34:52   Also, remember "-remap DEAD" for accenting characters.
06/01/2018 13:34:52 
06/01/2018 13:34:52 X FBPM extension not supported.
06/01/2018 13:34:52 X display is not capable of DPMS.
06/01/2018 13:34:52 --------------------------------------------------------
06/01/2018 13:34:52 
06/01/2018 13:34:52 Default visual ID: 0x24
**X Error of failed request:  BadMatch (invalid parameter attributes)**
  Major opcode of failed request:  73 (X_GetImage)
  Serial number of failed request:  41
  Current serial number in output stream:  41



```

Somebody who could help me out?

---

### Post by TheFu on 2018-01-06
Accessing VNC over the internet is a terrible idea.  All VNC implementations **require** a VPN or sshtunnel to be secure.  Which is why the vnc-server has a localhost option.  This mandates that someone has to connect to VNC only after they already connect to the VNC server.

Some people here would recommend running  X11 forwarding over ssh for something like this. I find the performance fine, but only when on the same LAN. Over the internet, I find the performance terrible - and that is saying it nicely.  **ssh -X user@server program-to-run**.

For internet based GUI access, I've settled on NX protocol as "the best" for my needs.  It feels 2-3x faster than any VNC, includes/requires ssh for authentication, and if you use x2go, setup is pretty bonehead.  It works best with light GUIs, so use LXDE, XFCE, or pure openbox.  Avoid 3D accel desktops.  People who switch to x2go say it is like daylight with other options a dark, moonless, night.  There are ubuntu PPAs for x2go servers and clients. They work well.

Hope this is helpful to you, but there are reasons to use VNC.  Mainly if your clients don't support X11 or x2go.

---

### Post by erikve on 2018-01-06
Hi TheFu,

thank you for your answer. It is not an answer on my question, but a good recommendation is appreciated! I'l give the NX protocol a try.
However originally the Ubuntu server I'm using is meant for internal use: within the same LAN, -no access from the internet-. Which basically opens the opportunity again to use X11... and actually after some hours debugging myself I really would like to understand what's wrong (got the same setup working without problem on Kubuntu).

---

### Post by TheFu on 2018-01-06
Ubuntu Desktop 17.10 uses wayland as the display server by default, not X11.  I don't know if that is related or not, just something for your consideration.  Plus, DEs that require 3D accel GPU support tend not to work with remote desktops at all.

The GUI is just another program, unlike on Windows.  Swapping from Gnome3 or Unity to XFCE or LXDE is about 3 minutes of effort.  KDE might be smart about how/when it uses 3D accel capabilities.

Last time I touched VNC was on CentOS. Just followed a normal how-to that included an ssh tunnel.  I don't recall anything funny being required.  I was studying for the RHEL tests.  Haven't touched it as a server on Ubuntu in over a year - I was trying to get TurboVNC with openGL extensions working.  My distro wasn't bleeding edge enough, so I quickly cut bait.  If a solution requires rebuilding a kernel, I'm not interested. I did my kernel rebuilding time in the 1990s. No need to do that anymore for my needs.  I ended up getting QXL graphics working from kvm instead for local stuff.  It was a little flakey and I dropped back to using ssh X11Forwarding and x2go.

Of course, your requirements are probably different.  And again, I'm ZERO help. Sorry.

---

### Post by Herbon on 2018-01-10
Any updates?

---

