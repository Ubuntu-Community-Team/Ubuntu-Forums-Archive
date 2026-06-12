---
title: "Installing Nvidia and Firmware Driver on Ubuntu Server 16.04."
date: 2017-01-03
forum: Server Platforms
---

### Post by sethanath2 on 2017-01-03
Hi,

I would like to install Nvidia and Firmware Drivers on Ubuntu Server 16.04, which is running on my PC.
I could not find any instruction on the server guide. How would I know that I would not miss any important drivers that I may need for my Ubuntu Server?

Please help.

Thanks.

---

### Post by sethanath2 on 2017-01-04
Hi,

My knowledge with Ubuntu server is limited. I also believe I need to install amd64-microcode on this fresh installation of Ubuntu Server 16.04 as well.

How would I know that I would not miss any of these firmware? Do you have any sticky that I can follow?

Thank you so much.

---

### Post by deadflowr on 2017-01-04
Not sure if it's installed on a server, but if not install the ubuntu-drivers package,
```
sudo apt install ubuntu-drivers-common
```
then run
```
ubuntu-drivers device
```
this will show what drivers can be installed for the various devices on the system.
and
```
sudo ubuntu-drivers autoinstall
```
should install all drivers.

All that said, if you are on a server why install the nvidia drivers?

---

### Post by sethanath2 on 2017-01-04
> **deadflowr said:**
>  All that said, if you are on a server why install the nvidia drivers? 

Right now, it is slows. I need to try it with Nvidia driver in order to tell.

Thank you so much.

---

### Post by sethanath2 on 2017-01-06
Hi,

After executing the command below, my Ubuntu server executes a lot faster. 

sudo ubuntu-drivers autoinstall

However, after the reboot, I got the login prompt similar to the one from Unity desktop, but I did not have any DE at the time. It also gave me the error message "Failed to start session". I fixed it by using command below, but it did not seem right.

sudo apt install --no-install-recommends ubuntu-desktop

I will need to find better DE that is a lot smaller.

Thanks.

---

### Post by The Cog on 2017-01-06
If you want a desktop, why did you install the server edition? 
The primary difference with Ubuntu server is that it has no desktop GUI. Servers in a rack don't need them.

If you want a desktop, I would suggest that you install either Ubuntu or Xubuntu. 
Xubuntu has a more lightweight GUI, a little like Win XP to my mind, but the choice is largely one of personal taste.
Why do you say you will need to find better DE that is a lot smaller?

---

### Post by sethanath2 on 2017-01-06
> **The Cog said:**
> If you want a desktop, why did you install the server edition? 
The primary difference with Ubuntu server is that it has no desktop GUI. Servers in a rack don't need them.

If you want a desktop, I would suggest that you install either Ubuntu or Xubuntu. 
Xubuntu has a more lightweight GUI, a little like Win XP to my mind, but the choice is largely one of personal taste.
Why do you say you will need to find better DE that is a lot smaller?

I think the proper term that I found on google is "GUI". Many people prefer to use GUI on their server.
I have just removed unity desktop, and use Openbox instead. It is a lot smaller than Unity.

sudo apt remove ubuntu-desktop
sudo apt install openbox obconf

Thanks.

---

### Post by TheFu on 2017-01-06
Adding a GUI to the server doesn't add any GUI programs to manage it.

For the greatest stability, servers shouldn't have any GUI code on them. X/Windows is full of bugs, leaks, backdoors, security issues. Best to leave that stuff off a server.

OTOH, if this is a dev machine - have at it.

I should admit that my "desktop" is really Ubuntu Server with  openbox loaded.  I prefer having control over the programs installed. Generally don't want all the applications a DE adds that I'll never use.  Also, don't need/want a menu/panel.  These are personal preferences for me. I wouldn't expect others to follow them.  The flexibility of Linux allows this, which is great!

But my servers don't have GUIs.

---

