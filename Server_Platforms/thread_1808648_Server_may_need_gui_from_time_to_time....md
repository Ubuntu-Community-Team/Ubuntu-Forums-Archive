---
title: "Server may need gui from time to time..."
date: 2011-07-20
forum: Server Platforms
---

### Post by berinde on 2011-07-20
Hello all, apologies if repost/redundant.

tl;dr: How do I start Xubuntu gui located on another drive?

I can't seem to find an article around that explains this. I recently installed Ubuntu 10.10 x64 server to a flash drive to get familiar with the environment. I plan on purchasing a low power htpc setup in the next few months that will run as a headless unit. I have configured it to mount several drives that I have in the computer at boot up and set up samba to share these drives in my home network. My question is, is it possible I start up the Xubuntu gui (currently installed on another hard drive) if I need it? I think it may be useful for configuring the wireless network if I need to put it away from the router. I prefer ethernet for the speed, but that may not be possible. I'm not scared of the command line. 

Thanks,
Berinde

---

### Post by cariboo on 2011-07-20
I would suggest that you install whatever desktop environment you want to use, then purge gdm/xdm/kdm/lightdm, then when you need a gui just log on as a normal user, then type:

```
startx
```

when done, just log out, and the desktop is no longer available until you type:

```
startx
```

again.

---

### Post by berinde on 2011-07-22
Where would the "gdm/xdm/kdm/lightdm" be located on Xubuntu 11.04? I have searched for the folders you listed and I have several gdm folders scattered about. 

Also, would simply changing it the folder name from "nameOfFolder" to "nameOfFolderOld" work?

---

### Post by Sorky on 2011-07-22
**I just did something that you may find useful... **
 
Ubuntu Server 64 [with SSH Server, PRINT and SAMBA]
> Install and then login
 
Add XINIT
> sudo apt-get install xinit
 
Add awesome
> sudo apt-get install awesome
 
Link awesome as part of xinit
> echo "exec awesome" > ~/xinit.rc
 
Start the GUI
> xinit
 
**That's the ENTIRE PROCESS to get a simple & useful GUI working on Ubuntu server!**
 
Just to save some typing and allow a little more function in the GUI I also added a file manager and web browser
> sudo apt-get install xfe
> sudo apt-get install firefox
 
PS: XFE and Firefox are in the default awesome menu, so they are ready to use. Otherwise, just open a terminal windows inside the GUI and launch away!
 
**Enjoy!**

---

