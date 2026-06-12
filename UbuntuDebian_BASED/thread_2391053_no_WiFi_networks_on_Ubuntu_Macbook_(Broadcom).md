---
title: "no WiFi networks on Ubuntu Macbook (Broadcom)"
date: 2018-05-05
forum: Ubuntu/Debian BASED
---

### Post by bad-and-ugly on 2018-05-05
Hi everyone [=


I installed Ubuntu 18.04 on an old MacBook Pro 7,1 (Intel Core 2 Duo, 2010) and I don't have a Mac OS to return to (single boot [=). Wifi hardware was not detected and after a lot of work, I was able to install it, chasing down all the dependencies.
The two things I installed at first (along with dependencies, of course) were:
 bcmwl-kernel-source
 dkms


So now the Wifi hardware is there, but it doesn't see any networks. Today, trying to solve this problem, I also installed this
 b43-fwcutter


My Broadcom is 4322 (pci.id is 14e4:432b)


I know a lot of people with Macs and Broadcoms have these problems, and I read through a lot of them. Still, I post this because I see that the problems and the solutions often turn out to be too specific in one way or another. Right now I don't remember everything I tried to fix this problem, but I guess the most important instructions (that led me to install those three things) are [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)


I appreciate your time and attention, thank you [=

EDIT: let me add that if I press and hold alt/option while booting, I get to this pre booting screen where WiFi works normally.

---

### Post by ank2 on 2018-05-05
> **bad-and-ugly said:**
> Hi everyone [=


I installed Ubuntu 18.04 on an old MacBook Pro 7,1 (Intel Core 2 Duo, 2010) and I don't have a Mac OS to return to (single boot [=). Wifi hardware was not detected and after a lot of work, I was able to install it, chasing down all the dependencies.
The two things I installed at first (along with dependencies, of course) were:
 bcmwl-kernel-source
 dkms


So now the Wifi hardware is there, but it doesn't see any networks. Today, trying to solve this problem, I also installed this
 b43-fwcutter


My Broadcom is 4322 (pci.id is 14e4:432b)


I know a lot of people with Macs and Broadcoms have these problems, and I read through a lot of them. Still, I post this because I see that the problems and the solutions often turn out to be too specific in one way or another. Right now I don't remember everything I tried to fix this problem, but I guess the most important instructions (that led me to install those three things) are [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)


I appreciate your time and attention, thank you [=
Not knowing or having a Mac so cannot tell how device names are named there. Here on PC hardware my (not Broadcom) WIFI hardware is named wlan0.

I would first look if the OS disabled the hardware using **rfkill list**. Unblock if it was. Then I would see what **ifconfig** says. If your device is listed. If not try also **ifconfig -show**. If it doesn't show up I am stuck here as well. If it does show up try **iwlist <DEVICENAME> scan** to see if it lists some sources. Replace DEVICENAME with whatever name your device is named.

---

### Post by bad-and-ugly on 2018-05-06
Thank you for responding. 
It's not blocked on rfkill list. Couldn't run ifconfig because I'm out of net-tools... I'll try to fix that. In another forum somebody told me to run iwlist wlan0 scan, and what I got was a message saying the interface doesn't support scanning. Also, let me add that if I press and hold alt/option while booting, I get to this pre booting screen where WiFi works normally.

---

### Post by ank2 on 2018-05-06
> **bad-and-ugly said:**
> Thank you for responding. 
It's not blocked on rfkill list. Couldn't run ifconfig because I'm out of net-tools... I'll try to fix that. In another forum somebody told me to run iwlist wlan0 scan, and what I got was a message saying the interface doesn't support scanning. Also, let me add that if I press and hold alt/option while booting, I get to this pre booting screen where WiFi works normally.
So WIFI does generally work. Good.

My next guess is that you might have loaded the wrong driver module, or the driver isn't loaded at all. Does an **lsmod** list a driver there? Or can you do **lsmod**&#8203; when on the pre-booting screen to compare?

---

### Post by bad-and-ugly on 2018-05-06
Lsmod lists a lot of things, one of them is wl, which is being used by 0. Is this my problem? That pre booting screen is all gui, I can't type anything =/

---

### Post by bad-and-ugly on 2018-05-06
I guess my thing may be called wlp2s0. The command iwlist wlp2s0 scan gives "no scan results"

---

### Post by ank2 on 2018-05-09
> **bad-and-ugly said:**
> I guess my thing may be called wlp2s0. The command iwlist wlp2s0 scan gives "no scan results"
Does **lsmod | [COLOR=#000000]wlp2s0[/COLOR]**[COLOR=#000000] come up with something?

Also does **ifconfig -1**&#8203; list the device?[/COLOR]

---

### Post by ank2 on 2018-05-09
> **bad-and-ugly said:**
> Lsmod lists a lot of things, one of them is wl, which is being used by 0. Is this my problem? That pre booting screen is all gui, I can't type anything =/
How do you know you have WIFI running?

---

### Post by bad-and-ugly on 2018-05-11
Hey Ankman 
Lsmod lists wlp2s0 being used by 0 and cfg80211 being used by 1 wl. Ifconfig lists wlp2s0,yes. I think WiFi id's running because i can turn it on or off on the system preferences gui.

---

### Post by wildmanne39 on 2018-05-11
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by bad-and-ugly on 2018-05-12
Hello
Now that I have a cable, I realize wired connection is not working either ): anyway, here are the results [https://pastebin.ubuntu.com/p/37rxcTVKzK/](https://pastebin.ubuntu.com/p/37rxcTVKzK/)

---

### Post by wildmanne39 on 2018-05-12
Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer
```
Reboot and let us know if that worked if not do 
```
sudo apt purge broadcom-sta-dkms
sudo modprobe -r wl
sudo modprobe b43
```

Thanks

---

### Post by wildmanne39 on 2018-05-12
You can tether your cell phone to your computer to install the other driver in my previous post if you have a hotspot on your phone.

---

### Post by bad-and-ugly on 2018-05-12
> **bad-and-ugly said:**
> Hello
Now that I have a cable I realize that the wired connection isn't working either )= here's all the information from the script 
[https://pastebin.ubuntu.com/p/37rxcTVKzK/](https://pastebin.ubuntu.com/p/37rxcTVKzK/)

I thought my first post didn't go because I didn't see it was on a second page!!! =P let me try your instructions.

---

### Post by bad-and-ugly on 2018-05-12
Praise the lords, wired connection started working! (on its own)

```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer
```

After reboot, the previous two still didn't work. I believe firmware-b43 was already installed.

```
sudo apt purge broadcom-sta-dkms
sudo modprobe -r wl
sudo modprobe b43
```

Broadcom-sta-dkms was not present, wl was not found. modprobe b43 didn't give any messages. No networks =|

I hope you guys really enjoy doing this cause I stopped investigating on my own last week, I'm basically following instructions here and on linuxquestions.org. so thank you again!

---

### Post by wildmanne39 on 2018-05-12
Wired connection started working because running the commands I gave you removed the driver the wired connection needed from the blacklist file and allowed it to load and it should have also worked for your wifi in this particular case. Please run the wireless script again and post the results so we can see the current state of your wifi, please do not do anything that I do not ask you to do like from another site that is usually counter productive.

---

### Post by bad-and-ugly on 2018-05-12
Thank you for your time [= Look, these are the new results from the script [https://pastebin.com/7veVj5xD](https://pastebin.com/7veVj5xD)

---

### Post by wildmanne39 on 2018-05-12
*Thread moved to **Ubuntu/Debian BASED for a more appropriate fit**.*

This report shows you changed operating systems and I do not know anything about this one, and there are always subtitle differences between an OS based on ubuntu and ubuntu, also the report does not show the changes I asked you to make so I have no new information to work with, if you run the commands in post 12 and post the results of the script after you run those commands then I will take a look but I may not be able to help with elementary OS.

 Please do not make changes that I have not asked you to make it only complicates the process of resolving your issue.

Thanks!

---

### Post by bad-and-ugly on 2018-05-13
Ai! &#128584;
I was dying to try Pantheon DE eversince I got this computer, so that's what I tried to do as soon as I got a wired connection. Didn't work though.
Anyway, I'm really using the same system as before.

So I follow the first two steps, reboot and now WiFi is working. Thank you so much!! How did you do it?

> **wildmanne39 said:**
> *Thread moved to **Ubuntu/Debian BASED for a more appropriate fit**.*

This report shows you changed operating systems and I do not know anything about this one, and there are always subtitle differences between an OS based on ubuntu and ubuntu, also the report does not show the changes I asked you to make so I have no new information to work with, if you run the commands in post 12 and post the results of the script after you run those commands then I will take a look but I may not be able to help with elementary OS.

 Please do not make changes that I have not asked you to make it only complicates the process of resolving your issue.

Thanks!

---

### Post by wildmanne39 on 2018-05-13
We removed the wl driver which did not work for your device and activated the b43 driver by installing the firmware it needed and when we did both of those things it also allowed your broadcom wired device to activate.

Enjoy!

---

### Post by bad-and-ugly on 2018-05-13
> **wildmanne39 said:**
> We removed the wl driver which did not work for your device and activated the b43 driver by installing the firmware it needed and when we did both of those things it also allowed your broadcom wired device to activate.

Enjoy!

Thank you [= I went through your profile just now - you're helping everyone! Who knows, maybe we'll talk again - I'm about to ask for help in a different subforum here... (trying to install a different desktop environment has kind of screwed some things around here)

---

### Post by bennywas on 2018-09-26
Thank you so much for this -- just wante[FONT=arial]d to[/FONT] say that this advice worked for me, too, with slightly different specs:
MacBook Pro Late 2012
Ubuntu 18.04 with Linux kernel 4.15.0-29-generic
[FONT=courier new]sudo lshw -C network[/FONT] says my Broadcom is BCM[FONT=arial]433[/FONT]1

I had already tried a bunch of things, including reinstalling bcmwl-kernel-source, but what got it to work was following the first part of wildmanne39's advice and rebooting. I didn't have to follow the second part with purging broadcom-sta-dkms. When I rebooted my wifi options were showing!! Thank you!!

---

### Post by dudufish on 2019-07-22
TYVM! I did the wireless script in your signature then the codes as you said... works perfectly!

Running Ubuntu 19.04 on a Macbook Pro mid 2010

---

