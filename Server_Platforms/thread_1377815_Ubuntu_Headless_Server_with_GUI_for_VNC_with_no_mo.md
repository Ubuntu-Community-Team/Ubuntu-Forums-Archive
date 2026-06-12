---
title: "Ubuntu Headless Server with GUI for VNC with no monitor issues"
date: 2010-01-10
forum: Server Platforms
---

### Post by IAmNotAUser on 2010-01-10
I have a Ubuntu Server running 9.10 that I wish to use remotely using VNC.

I have installed GNOME and everything else I need to use VNC to log in remotely. GDM is set up to automatically log into the account on boot, and then lock.

However, when I try to boot without the monitor, to begin with I was getting a 'Ubuntu is using low graphics' error. I've established this is Bulletproof-X kicking in and forcing it to this dialogue.

I've tried deleting the xorg.conf.filesafe, I've tried creating a xorg.conf file containing this

```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "DDC" "False"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 31.5-48.5
VertRefresh 50-70
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection
```I've tried to do

```
sudo dpkg-reconfigure -plow xserver-xorg
```which was apparently meant to ask me questions about auto-detection, but just goes back to the terminal input with no output.

Now when I try reboot without the monitor, it boots back to the CLI logon, no error, but no X either. I have both xorg.conf and xorg.conf.failsafe deleted still, and I cannot restore the failsafe as I did not make a backup and I cannot find it online.

What else can I do to fix this? My only option now is to reboot with a monitor attached and then remove the monitor, but this is not practical moving the monitor between rooms.

---

### Post by HermanAB on 2010-01-11
Hmm, VNC is mainly a Windows thing.  On Linux, it is almost always the wrong solution and on a server it definitely is not a good idea and may get your machine hacked before you know it.

You are on the right track though.  With Gnome installed you now have a bunch of graphical programs at the ready, but you don't actually need to run X or Gnome and you can kill or disable X11. Install ssh server and then log in remotely like this:

$ ssh -X -C -c blowfish user@server gnome-panel
and go click happy.

or

$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"
to do something specific remotely.

---

### Post by Malac on 2010-05-10
I posted my idea on brainstorm.ubuntu.com if you'd like to check it out or comment or promote the idea here's the link:
[[IMG]http://brainstorm.ubuntu.com/idea/24380/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/24380/)

---

### Post by nodnerb on 2010-06-16
Hi,
Just a thought - if you have an nvidia card and are using the proprietary drivers, you can use the ConnectedMonitor option in the config file.

More information here:
[http://www.sorgonet.com/linux/nv-online/help.html#ConnectedMonitor](http://www.sorgonet.com/linux/nv-online/help.html#ConnectedMonitor)

It works for me.  Don't know if there's equivalent options for ATI cards.

Hope that helps!

Brendon

---

### Post by Groodles on 2010-06-17
[http://ubuntuforums.org/showthread.php?p=9235045#post9235045](http://ubuntuforums.org/showthread.php?p=9235045#post9235045)

---

### Post by IAmNotAUser on 2010-06-23
> **Groodles said:**
> [http://ubuntuforums.org/showthread.php?p=9235045#post9235045](http://ubuntuforums.org/showthread.php?p=9235045#post9235045)

This has done it, thanks so much! :D

---

