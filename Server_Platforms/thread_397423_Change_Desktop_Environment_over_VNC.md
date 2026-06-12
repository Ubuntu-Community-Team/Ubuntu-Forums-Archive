---
title: "Change Desktop Environment over VNC"
date: 2007-03-30
forum: Server Platforms
---

### Post by vadimolen on 2007-03-30
Hello,

I have a headless "server" in my house now that is running Kubuntu Edgy and I've come to understand that KDE is just taking up extra resources that a server doesn't need taken up.  I would like to switch to Xubuntu.  Everything I've read about switching involves 
```
sudo apt-get install xubuntu-desktop
```
but there are two problems with this that I was hoping you guys could help with.

First, as I understand it, that will install not only xfce but also other apps (like xubuntu's text editor, etc.) in addition to the kde apps that I already have.  Will ```
sudo apt-get remove kubuntu-desktop
``` get rid of the kde duplicates?  Also, will it mess up anything that I've already configured on the server (samba, ssh, apache, php)?

Second, when I switched from ubuntu to kubuntu before, I had both installed and had to select a Desktop Environment at the login screen.  However, the only way I can get to this server is by VNC and ssh, so I can only connect after the login screen (right?).  So, how can I set the default Desktop Environment without being at the login screen?

Sorry for being so verbose and thanks in advance! :)

---

### Post by Nikron on 2007-03-30
I don't think kubuntu-desktop depends on anything a server needs.  I believe doing sudo aptitude remove kubuntu-desktop may get rid of what you want..  But there was a guide some where, on someone's sig.

EDIT:

Here's a link you're probably interested in
[How to get pure XFCE.]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by vadimolen on 2007-03-30
Thanks for the quick reply!  

I used kcontrol to setup automatic login (so that I can get into it with VNC after a reboot).  
If I do```

sudo aptitude install xubuntu-desktop
sudo aptitude remove kubuntu-desktop
```
will it still know to automatically login into xubuntu on the next boot? The problems is that if it doesn't I'll need to hook up a monitor/keyboard/mouse, and it's hard for me to physically get a monitor to this computer. So if there are problems that stop me from being able to VNC in after I do this (and things that I need the GUI in order to configure), I'm pretty much out of luck.

Or is there a way to set up an automatic login to xcfe without using the GUI?

---

### Post by Nikron on 2007-03-31
> **vadimolen said:**
> Thanks for the quick reply!  

I used kcontrol to setup automatic login (so that I can get into it with VNC after a reboot).  
If I do```

sudo aptitude install xubuntu-desktop
sudo aptitude remove kubuntu-desktop
```
will it still know to automatically login into xubuntu on the next boot? The problems is that if it doesn't I'll need to hook up a monitor/keyboard/mouse, and it's hard for me to physically get a monitor to this computer. So if there are problems that stop me from being able to VNC in after I do this (and things that I need the GUI in order to configure), I'm pretty much out of luck.

Or is there a way to set up an automatic login to xcfe without using the GUI?

Well, I just have fluxbox and xorg installed, so I don't know if it applicable to your situation, but fluxbox just starts automatically when xorg starts.  So I"m pretty sure if you log in via ssh do the whole "vncserver :1" (Or whatever port you want)  and then connect, you'll already be logged into the environment.

---

### Post by pppetter on 2007-03-31
I don't know what login manager xubuntu uses, but it should be possible to do the same with xubuntu. Here's a guide on how to do it, but I just don't think that xubuntu uses gdm....

[https://help.ubuntu.com/community/VNC#head-77f3890451112de1f92fb9628503806e0441d963](https://help.ubuntu.com/community/VNC#head-77f3890451112de1f92fb9628503806e0441d963)

---

