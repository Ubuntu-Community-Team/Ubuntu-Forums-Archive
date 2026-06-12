---
title: "help with LAMP server"
date: 2008-01-07
forum: Server Platforms
---

### Post by DelusionalCookie on 2008-01-07
I have an (almost) operational lamp server and i need to be able to install a gui, as per my teachers request. its running on a dell server, and i have been having a bit of a problem. I have tried multiple times with the kde, gnome, and xubuntu desktop environments, but I am dealing with one stubborn machine. the closest i got was when i installed gnome and i got to the login screen, and after you logged in, all you got was a blank screen with the ubuntu default background, no tray, taskbar, nothing. this install i am working on right now is number 4 and fresh with openssh and vsftpd being the only things installed. i have already perused the forums and have tried the suggestions detailed in other threads, so please no referrals to other threads. thank you in advance for any help you can give me.

---

### Post by PinkFloyd102489 on 2008-01-07
You should be able to simply apt-get install ubuntu-desktop. If you cant get it working, you might want to look into Webmin.

---

### Post by DelusionalCookie on 2008-01-07
i like webmin, and i've been using it for the past couple of years now on another server and it has performed flawlessly, but i need a gui. what do you suggest, should i try to just reinstall and do it over again?

---

### Post by OpenSourceFuture on 2008-01-07
Can you right click and manually add a bar inside gnome? 

Before giving up/reinstalling I'd give fluxbox a try, its light weight, and very functional. 

Hope that helps.

---

### Post by RedSquirrel on 2008-01-07
A light window manager would be good. fluxbox, openbox, icewm...

If you've installed the Server Edition of Ubuntu (with LAMP), this is what I would do:

```
sudo apt-get update 
```

```
sudo apt-get upgrade 
```

```
sudo apt-get install xorg fluxbox
```Generate the default Fluxbox menu (see my signature for a guide to make a more detailed menu if you want one later on...):

```
sudo update-menus
```Then create the file ~/.xinitrc with the following contents:

```
#!/bin/sh

exec startfluxbox
```Make it executable:

```
chmod +x ~/.xinitrc
```and then run

```
startx
```That will get you into a GUI and you can go from there...

---

### Post by #Reistlehr- on 2008-01-07
I had the same problem (minus the school thing), but i just did, sudo apt-get remove ubuntu-desktop

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install ubuntu-desktop

and it ran flawlessly. It should install xorg and all those for you. (I was using the 7.04 Server Alternative i386 disc)

---

### Post by DelusionalCookie on 2008-01-09
Thanks! I am working on it now, was busy yesterday creating a new image for the machines here at the school. I reinstalled ubuntu because i somehow messed it up and apt-get and wget weren't working, and i could only access the server through ssh, and my ftp configuration files were messed up so i couldn't even get webmin on. oh well so it is working now. i will bring you guys up to speed when i finish. Thank you very much for all your help, I am doing the xorg fluxbox install. hope it works.

---

### Post by DelusionalCookie on 2008-01-09
nevermind

---

### Post by az on 2008-01-09
How much ram does this machine have?  You need at least 256 megs to run a desktop.

Also, try installing the desktop kernel.  The server kernel is not optimized for desktop hardware (like some mice and keyboards) and you may find that solves your problems.

sudo apt-get install linux-generic


Why does your teacher require a GUI?  It will be useless as far as the LAMP server is concerned.  LAMP has no GUI.  You will be staring at the desktop, but will still have to open a terminal to interact with your web server.

---

### Post by DelusionalCookie on 2008-01-09
> **az said:**
> How much ram does this machine have?  You need at least 256 megs to run a desktop.

Also, try installing the desktop kernel.  The server kernel is not optimized for desktop hardware (like some mice and keyboards) and you may find that solves your problems.

sudo apt-get install linux-generic


Why does your teacher require a GUI?  It will be useless as far as the LAMP server is concerned.  LAMP has no GUI.  You will be staring at the desktop, but will still have to open a terminal to interact with your web server.
yeah the mice and keyboard are compatible, and fluxbox is up and running. I will try the generic one however. He wants to try out some different software that "supposedly" require a gui to install, but hasn't yet elaborated on what yet. i would've had this done a while ago with webmin up and running and ftp configured correctly but he "had" to have a gui. oh well... its for my semester project...

---

### Post by DelusionalCookie on 2008-01-10
so one quick question, a tad off topic, but how do you create a linux command? i'm not quite sure how and google refuses to be helpful... if there is a thread can you post a link to it please? Thanks!

---

### Post by az on 2008-01-11
> **DelusionalCookie said:**
> He wants to try out some different software that "supposedly" require a gui to install, but hasn't yet elaborated on what yet.

You can just install the xorg package.  Then, ssh into your server with the -X argument and run your GUI app on a remote box with an X server.   There is an Xming Xserver for windows.

You can run a GUI app from an Ubuntu server without the desktop actually being run on the server.  You need putty and Xming on the windows client.

---

### Post by DelusionalCookie on 2008-01-14
thanks you so much, it works perfect now.

---

