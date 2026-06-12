---
title: "External Monitor w/ 15&quot; Serval Pro (11.10, Unity)"
date: 2011-10-18
forum: System76 Support
---

### Post by oxsyn on 2011-10-18
Hello,

I just upgraded my serval pro to 11.10.  I'm using unity 3d for now.  Everything is stock, for the moment.  

I have not previously attempted to get my laptop working with an external monitor.

I've connected a 24" Asus display via HDMI.  When I go to "displays" and select "detect displays" it is not detected.

Is there a guide to getting this working?  I have a feeling I will need to do some modification of the X Server configuration (possibly via the nVidia X Server Settings application).  I have not done this before.

I would like to extend my display on to the external monitor when connected and just use the laptop monitor when it is not connected.  Is it possible to have it automatically detect when the monitor is connected/disconnected and make those configuration changes on its own?

---

### Post by chriscross93 on 2011-10-18
You will need to use the nvidia-settings GUI, but there have been some issues with that since the upgrade.

I found & posted a workaround here:
[http://ubuntuforums.org/showthread.php?t=1863459](http://ubuntuforums.org/showthread.php?t=1863459)

>  Is it possible to have it automatically detect when the monitor is connected/disconnected and make those configuration changes on its own?
Yes, when I disconnect/reconnect the external monitor appropriate changes are made automatically. :)

---

### Post by oxsyn on 2011-10-19
Hmm, I followed that guide.  If i do not enable Xinerma my external monitor just displays a blank white screen.  If I enable Xinerma, then it freezes when I attempt to login.

---

### Post by tmurch on 2011-10-19
I used this. It worked for me. 

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

---

### Post by Kacey on 2011-10-19
> **tmurch said:**
> I used this. It worked for me. 

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current


My only concern with the fix that you have posted is that it takes the X server updates even more bleeding edge. Do you know if that X repo is required for the fix or is it just using the current non-recommended nvidia drivers?

---

### Post by isantop on 2011-10-20
That PPA provides updates to stable X components. The Xorg Edgers PPA is the bleeding edge repository, and that's the one that may contain unstable software. You can see [This Link](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) for more information

---

### Post by Kacey on 2011-10-24
I have installed these packages and yet I still have to reboot in order to get my second monitor enabled. Also have to reboot to disable the monitor.

---

### Post by chriscross93 on 2011-10-24
> **F4RR4R said:**
> Hmm, I followed that guide.  If i do not enable Xinerma my external monitor just displays a blank white screen.  If I enable Xinerma, then it freezes when I attempt to login.

Hmm, I use twinview.  I wonder if that is the issue...

---

### Post by blitzd on 2011-10-25
> **F4RR4R said:**
> Hmm, I followed that guide.  If i do not enable Xinerma my external monitor just displays a blank white screen.  If I enable Xinerma, then it freezes when I attempt to login.

I have this exact same issue. It's like there's no desktop manager on the white screen, it's just a classic x server desktop. With xinerama I just get my login background on both monitors, and then nothing else - I eventually have to disable xinerama via the console and kill X.

---

### Post by isantop on 2011-10-26
Is your laptop using ATI graphics or Nvidia graphics?

---

### Post by bakelitedoorbell on 2011-10-26
Me too...   I have a Serp5 with an Nvidia card.  At first I had nothing, Then I used tmurch's suggestion for upgrading the driver.  Now I get a split second of my background image, and then a white screen on the external monitor.

---

### Post by blitzd on 2011-10-27
> **bakelitedoorbell said:**
> Me too...   I have a Serp5 with an Nvidia card.  At first I had nothing, Then I used tmurch's suggestion for upgrading the driver.  Now I get a split second of my background image, and then a white screen on the external monitor.

FYI I have filed both these issues as bugs here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/882143](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/882143)

and here:

[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/882134](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/882134)

---

### Post by pendlaren on 2012-06-08
Has anyone found a solution to this issue yet?

---

### Post by Gabbo2084 on 2012-06-10
Hi,
I have the same problem but no one seems to have solved it... This happens only with nvidia drivers though because with nouveau drivers once i plug in my 15" VGA monitor both monitors syncronize their resolutions and all is fine: i get two clone screens.

---

