---
title: "Terminal server???"
date: 2007-05-10
forum: Server Platforms
---

### Post by borahshadow on 2007-05-10
I am setting up a sever for my family and am wondering what the best way to have them be able to log in with is
I have gnome and KDE installed and would like them to be able to chose one of their choice and have each username have a deafault I don't know if that is possible or if it has to be a system default
Most of them (all except me) use windows on their computers but the best way (in my opinion) for them to start using linux is to use it transperently (samba file server) and to be able to log onto their linux account from windows to slowly start using it for a few tasks and to do things like change their password etc
I was thinking VNC but I don't know how to go about this and how things like each users default session come into play with VNC
Thanks
ps I will be rnning vmware server for them to run vm's in but I want to option for them to log onto their linux account too
I want to be able to log onto my linux account from linux or windows which from what I've read about VNC is entirely possible

---

### Post by craigp84 on 2007-05-13
Hi BorahShadow,

> I have gnome and KDE installed and would like them to be able to chose one of their choice and have each username have a deafault

Yes, on the login screen on the linux box, there's a button called "session". Clicking this allows you to choose GNOME, KDE or whatever other environments you have installed.

If one user chooses GNOME, this will not affect the ability of another to use KDE, and they will continue to login to their chosen desktop, until they choose otherwise via the session menu again on the login screen.

> I was thinking VNC

Yeah you can certainly use VNC. You'll need to install the VNC client on their desktops, and "sudo apt-get install vnc4server" on the server. You'll then need to add a line - Load "vnc" - into the modules section of xorg.conf which you can edit by typing "sudo gedit /etc/X11/xorg.conf". You'll then need to restart X for it to take effect (CTRL+ALT+Backspace for a quick X restart).

> Most of them (all except me) use windows on their computers but the best way (in my opinion) for them to start using linux is to use it transperently

If they're happy to try linux, why not just dump them in the thick of it, give them a local install :-) You can always dual boot. Also the new feisty installer will attempt to drag over some basic settings from their windows partition.

Hope this helps,

Craig

---

### Post by borahshadow on 2007-05-13
> Yeah you can certainly use VNC. You'll need to install the VNC client on their desktops, and "sudo apt-get install vnc4server" on the server. You'll then need to add a line - Load "vnc" - into the modules section of xorg.conf which you can edit by typing "sudo gedit /etc/X11/xorg.conf". You'll then need to restart X for it to take effect (CTRL+ALT+Backspace for a quick X restart).
thanks that is what I wanted to know I'll try that and see how it goes
I installed the vnc4server package and added that to my xorg.conf and restarted x but now how do I connect from a different computer
and do you have any recommended clients for windows and linux?

---

### Post by borahshadow on 2007-05-14
I downloaded realvnc and added this in my config like their site said to 
>   Section "Screen"
          ...
          Option "SecurityTypes" "None"
  EndSection
and was able to see the login screen of KDM (no one was logged in at the time ) great that is what I wanted then I logged in ok great
But just now I tried again (I was already logged in locally) and just got a black screen?
I'll play around with this some more tommorrow but that confused me
also can more than one pero\son me on at a time? like can I be remotely logged in to my account and have my mom remotely logged from her account to?

---

### Post by craigp84 on 2007-05-14
> can I be remotely logged in to my account and have my mom remotely logged from her account to?

Yes.

-c

---

