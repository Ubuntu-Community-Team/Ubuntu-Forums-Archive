---
title: "Installing Nvidia and Firmware Driver on Ubuntu Server 16.04."
date: 2017-02-27
forum: Server Platforms
---

### Post by sethanath2 on 2017-02-27
Hi,

I have just performed fresh installation of Ubuntu Server 16.04. I did the three steps next, because I notice this server would perform faster with Nvidia driver.

sudo apt install ubuntu-drivers-common
ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

My question to you is why I keep getting the login similar to the one from the Unity desktop after I rebooted. However, I can't login there. I have to press Ctrl + Alt + F1 in order to use server login prompt.

Please show me how to fix it.

Thank you in advance.

---

### Post by Habitual on 2017-02-27
You installed a desktop on this "server"?
a cursory check using 
```
sudo apt-cache rdepends ubuntu-drivers-common | grep desktop
``` shows what may been installed.
```
  kubuntu-desktop
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-gnome-desktop
  kubuntu-desktop
  ubuntu-desktop
  kubuntu-desktop
```

---

### Post by sethanath2 on 2017-02-27
> **Habitual said:**
> You installed a desktop on this "server"?
a cursory check using 
```
sudo apt-cache rdepends ubuntu-drivers-common | grep desktop
``` shows what may been installed.
```
  kubuntu-desktop
  xubuntu-desktop
  ubuntustudio-desktop
  ubuntu-gnome-desktop
  kubuntu-desktop
  ubuntu-desktop
  kubuntu-desktop
```

Hi, 

By executing the commands "sudo apt-cache rdepends ubuntu-drivers-common | grep desktop", I received the results exactly as you mentioned. I tried removing such desktops, one by one, but each is not working.

```
sudo apt remove kubuntu-desktop
```
```
Package 'kubuntu-desktop' is not installed, so not removed
```

Please help. Thank you.

---

### Post by Habitual on 2017-02-27
Servers don't have desktops. You installed one.
> **sethanath2 said:**
> My question to you is why I keep getting the  login similar to the one from the Unity desktop after I rebooted.  
This is why you get greeted with a graphical login to your "server".

I don't know how to undo an unknown. Sorry.

Start over.
No nVidia necessary.

---

### Post by sethanath2 on 2017-02-27
> **Habitual said:**
> Servers don't have desktops. You installed one.

This is why you get greeted with a graphical login to your "server".

I don't know how to undo an unknown. Sorry.

Start over.
No nVidia necessary.
  
Thanks for your help. I have just performed another fresh installation of Ubuntu Server 16.04. I need to practice so I end up start over. How do I install only AMD Microcode, by the way?

---

### Post by Habitual on 2017-02-27
That I don't know. Sorry, I'd have a look at [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) and await further instruction/help.

There is much to learn from failure.

Peace.

---

### Post by sethanath2 on 2017-03-01
Hi,

I still wonder if there is any way to install Nvidia driver and AMD-Microcode without any Ubuntu desktop.

Thank you in advance.

---

### Post by mastablasta on 2017-03-03
not sure about AMD microcode, but for nVidia what you do is add the nVidia PPA, then install the driver you want.

another option is to download the driver from nVidia website (using *wget* or on desktop on another PC and then move it to server) then extract it and run the install script.

more here (under no X): [SIZE=2]https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
[/SIZE] 
here: [SIZE=2]https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa
[/SIZE]
for manual install there shoul dbe a readme file when you download the drivers. it's Quite complicated as i rember.

if you do not have a desktop installed on server you will have text mode anyway. but maybe it can be usefull for some bitcoin mining. how would i know? :-k

---

