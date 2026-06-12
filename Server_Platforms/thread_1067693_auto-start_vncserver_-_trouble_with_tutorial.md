---
title: "auto-start vncserver - trouble with tutorial"
date: 2009-02-12
forum: Server Platforms
---

### Post by gobbledigook on 2009-02-12
Hi!

I'm running a headless server at home and wanted to install vncserver to access a desktop environment for things like running utorrent and moving files about etc...

i'm following [**_[SIZE="2"]this [/SIZE]_**]("http://ubuntuforums.org/showthread.php?t=261366")tutorial, which seems simple and it was going well until i saw the comments at the end.

it doesn't work unless you change some settings within the desktop environment:

> OK, I had the same problem before until I performed the following

System->Administration->Login Window
Click on Remote Tab
Changed style to "Same as Local"
Click on the "Configure XDMCP..." buton
Uncheck "Honor indirect request"
Click Close on both windows

reboot

any ideas how i can do this from command line? or can anyone point me in the direction of a tutorial which doesn't rely on a gui?

any help much appreciated!!

Dan:)

---

### Post by RealPSL on 2009-02-12
These settings are actually in the the file /etc/gdm/gdm.conf. However the changes should not be made in this file. The changes should be made to /etc/gdm/gdm.conf-custom. Identify the changes you want to make in the gdm.conf file and the sections they are in and then set the parameters in the gdm.conf-custom file. As an example you want to "Honor indirect request" that setting is in the [xdmcp] section and variable #HonorIndirect=true. You would add it to the gdm.conf-custom section as 
```

[xdmcp]
HonorIndirect=false

```

I have not personally attempted this but it should work. The file is pretty well documented so you should be able to figure it out based on the comments.

---

### Post by HermanAB on 2009-02-12
VNC is almost always the wrong solution on Linux.  Rather use SSH and Webmin.

Try this:
$ ssh user@server gnome-panel

or
$ ssh user@server "gedit /etc/fstab"

Cheers,

Herman

---

### Post by gobbledigook on 2009-02-12
Thanx for your feedback guys! 

tried editing the /gdm.conf-custom file but this only brought me more trouble! i had to yank out my server and hook up a screen to find out what was going on, it was hanging on an error like could not find the font file for gnome... so had to go into safe mode in order to uninstall GDM before i could regain access via ssh! 

i have realised that the tutorial has had me install a gnome environment type desktop thingy.... when i already had a version of kde-light with fluxbox which i was really happy with:(

going to try and backtrack a little and get back to my origional set-up and then try following **_[this ]("http://ubuntuforums.org/archive/index.php/t-438138.html")_**thread i found instead!

thanks for the tips!

Dan

---

