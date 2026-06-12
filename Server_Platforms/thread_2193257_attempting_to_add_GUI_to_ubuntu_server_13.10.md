---
title: "attempting to add GUI to ubuntu server 13.10"
date: 2013-12-11
forum: Server Platforms
---

### Post by darksidedude on 2013-12-11
I am attempting to add the Lubuntu-desktop meta package to my server. so I can run Handbrake and other apps on it as it has a lot more processing power/memory than my laptop. had I known that I wanted to harness my server to do such process I would have just installed the desktop version. with that aside. I ran ```
sudo apt-get install lubuntu-desktop
```  

and rebooted the server/workstation and LightDM did load I was presented with a rather "ugly" looking login screen (I suspect it is the very poor graphics controller on the server) so I proceeded to type in my login and password. and maybe a second or two latter the screen turned black and then the login screen came back up. the server is running 
plex,deluge,Virtualbox with phpvirtualbox, and webmin. 

the system is a Dell Poweredge 2950

if you have any ideas on how to fix this issue I would appreciate any insight. 
thanks and have a great day.

---

### Post by Bucky Ball on 2013-12-11
You don't want the desktop. Just install lxde, reboot, choose from sessions, if you have it.

Installing desktop will drag in everything from Lubuntu - apps, software, dependencies, the lot, not just the lxde desktop environment - so if you're going to do that you may as well just install Lubuntu. You don't want that on a server.

PS: Oh, just noticed you have installed lubuntu-dekstop. Not good.

---

### Post by darksidedude on 2013-12-12
I could always do ```
sudo apt-get purge lubuntu-desktop
``` and just install LXDE without the recommended packages. is it the extra packages that are causing my issue?

---

### Post by Bucky Ball on 2013-12-12
Could be. You want as few moving parts as possible really which will cut down the possible causes.

Yea, try that command. Not sure if it will remove everything back to the state you were in previously. After that command, maybe give it a:

```
sudo apt-get autoremove
```

---

### Post by darksidedude on 2013-12-12
when I ran the purge command it just removed the meta package not the actual packages. is there a possible route to take that does not install a re install? or have I passed the point of no return now.

---

### Post by Bucky Ball on 2013-12-12
As far as lubuntu-desktop goes, you could be past the point of no return, unless you can hunt down a command that uninstalls it, all dependencies and packages. 

Failing this, might be best to try and conquer the original problem. Do you get to a a list of kernels to boot when you boot the machine?

---

### Post by steeldriver on 2013-12-12
It sounds like a classic case of the chosen desktop session not being able to start - if you have physical access to the box, have you logged in to a console (Ctrl-Alt-F1) and checked the common things? like

[LIST]
[*]root-owned .Xauthority and/or .ICEauthority in the user's home dir (did you try stuff with startx before installing the desktop / DM?) 
[*]home dir unwriteable / home partition full 
[/LIST]
 You can also look in ~/.xsession-errors and/or the display manager logs (I think lubuntu-desktop uses lightdm)

---

### Post by darksidedude on 2013-12-15
I do have physical ascess to the box, but its headless. I did not do startx until trying to install LXDE. home dir for user is writeable and not full. I will look into .Xauth or .ICE and report any findings

---

### Post by steeldriver on 2013-12-15
If it is headless, how are you starting / connecting to the X server? are you running x11vnc as an upstart job?

You *may* need to create a custom /etc/X11/xorg.conf file with a dummy display

---

### Post by Bucky Ball on 2013-12-17
I thought it would be 'startlxde' as that is what you're using. 'startxfce4' is what is used for xfce4. Start x and lightdm do not work (at least for my custom mini install).

---

