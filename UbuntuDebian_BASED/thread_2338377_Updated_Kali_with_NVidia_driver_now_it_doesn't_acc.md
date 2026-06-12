---
title: "Updated Kali with NVidia driver now it doesn't accept mouse or pointer input"
date: 2016-09-27
forum: Ubuntu/Debian BASED
---

### Post by Roger_Williams on 2016-09-27
This is fun I keep breaking my machine. I'm a Linux noob, I started taking an Ethical Hacking course and decided it was the best time to learn Linux. I've got an older Dell Preceision M4300 that I finally managed to dual boot Ubuntu and Kali on. The laptop has an NVidia Quadra 350M. Today I decided to try and install the NVidia drivers in Kali following this [https://www.blackmoreops.com/2014/03/13/install-proprietary-nvidia-driver-kali-linux/3/](https://www.blackmoreops.com/2014/03/13/install-proprietary-nvidia-driver-kali-linux/3/) except after the reboot in Sep 5 now Kali doesn't accept mouse input. I'm don't have enough knowledge to know how to get rid of the NVidia driver or get the system going again. It will accept keyboard input so I can login but after anything I click on nothing happens. I can't even shut it down because I can't get to Terminal even. The Ubuntu is perfectly fine so anyone got suggestions on what I can do to fix this? I have searched and read but nothing seems to be quite the problem I'm having.

---

### Post by Roger_Williams on 2016-09-28
nothing? guess I gotta keep searching. Luckily I can always just blow it away and do a reinstall.

---

### Post by Roger_Williams on 2016-09-28
Well I solved my own issue after lots of searching and trying different things. Here is a description of exactly what was happening. When I booted to Kali the keyboard was fully functional. The mouse pointer was on the screen and the touchpad and USB mouse was tracking fine but clicking did nothing. I booted into Kali logged in under root and then used Ctrl+Alt+T to try and open the terminal. It opened a search but I searched for terminal and could start the terminal from there. Then I used information from a bunch of different sources I found to basically remove the NVidia driver and get the laptop to boot with the Nouveau driver which works perfect. In the terminal I did the following

apt-get autoremove --purge nvidia-*
[COLOR=#333333]/etc/init.d/gdm3 stop
apt-get install xserver-xorg-video-nouveau *thought it was already installed anyway
lspci -vk | grep nvidia

at this point my system froze so I did a reboot and the NVidia driver was gone so my mouse worked again! It was quite an adventure and I may try again before the end of the week to actually get the driver loaded the proper way.[/COLOR]

---

### Post by #&amp;thj^% on 2016-09-28
Not sure if you have tried this yet.
```
sudo apt-get install linux-headers-`uname -r`
```
Now install the driver you need with the same instructions you were following.

---

### Post by Roger_Williams on 2016-09-28
> **1fallen said:**
> Not sure if you have tried this yet.
```
sudo apt-get install linux-headers-`uname -r`
```
Now install the driver you need with the same instructions you were following.

Yep they are already installed. I have another guide so I may give that a shot tomorrow. I just wanted to enjoy a working system for a day lol.

---

### Post by Roger_Williams on 2016-09-29
I just had a lot of fun. I LOVE Linux, but still didn't get the NVidia drivers to install. I tried with the drivers I downloaded and the installation kept failing iwth errors. When I finally got the Nouveau drivers out and the installation continued it failed trying to install with dkms, I tried it without dkms and it failed because the kernel versions were different. This was all way over my head by that point so the best thing to do was to just abort and go back to what works. I may try with the same settings I had that actually were on the NVidia drivers I think the xorg file was what messed up my mouse. I may try that again later today.

---

### Post by #&amp;thj^% on 2016-09-29
> **Roger_Williams said:**
> I just had a lot of fun. I LOVE Linux, but still didn't get the NVidia drivers to install. I tried with the drivers I downloaded and the installation kept failing iwth errors. When I finally got the Nouveau drivers out and the installation continued it failed trying to install with dkms, I tried it without dkms and it failed because the kernel versions were different. This was all way over my head by that point so the best thing to do was to just abort and go back to what works. I may try with the same settings I had that actually were on the NVidia drivers I think the xorg file was what messed up my mouse. I may try that again later today.
*****This method dose not work on Ubuntu...Just DEBIAN*****
After you clean up the failed installs this has always worked for Debian.
There is two ways to this (Install it).
This method is Smxi:

[http://smxi.org/](http://smxi.org/)

To install,do the following as root from a terminal:

```
cd /usr/local/bin && wget -Nc smxi.org/smxi.zip && unzip smxi.zip && smxi
```

The installer will now ask to stop X,say yes and then login as root.
To run smxi,just simply type **"smxi"**.
Work through the questions asked,..like if you prefer to use aptitude or apt-get etc.
Eventually you will come to the menu where you can choose to install graphic drivers.
With smxi you have a choice of what drivers to install,from the 2d 'nv' driver to the latest beta driver from nvidia.
As it's a console application it's really as easy as pressing a number key and hitting enter.
Smxi can do a whole host of other tricks which i'm not going to go into here.
Try it,you might like it!.


**Or there is a script called sgfxi that only does graphic driver installs:**

I'm sure the smxi.zip contains sgfxi, if I'm not mistaken do:
```
cd /usr/local/bin && wget -Nc smxi.org/sfgxi && chmod +x sgfxi && sgfxi
```
So No need to go all the way through smxi if you only want to install graphics.

Hope this helped. 
BTW I use the whole smxi installer it has more features that I personally use.

---

