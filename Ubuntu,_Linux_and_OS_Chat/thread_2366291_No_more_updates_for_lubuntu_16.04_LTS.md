---
title: "No more updates for lubuntu 16.04 LTS"
date: 2017-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Hankbonk on 2017-07-15
I haven't received any automatic updates for my lubuntu 16.04 LTS for months now : Why is that ?

---

### Post by vasa1 on 2017-07-15
Run```
sudo apt-get update
```and```
sudo apt-get upgrade
```and post the output here between code tags.

---

### Post by ardouronerous on 2017-07-16
I've also experienced this on Lubuntu 16.04, I have unattended-updates installed and running, but didn't get updates for a couple of days, that was until I pressed 'Reload' and 'Mark All Upgrades' in Synaptic Package Manager, then all the updates started pouring in.

Reload on Synaptic is the same as [FONT=courier new]sudo apt-get update[/FONT] right? Anyway to automate it?

---

### Post by poorguy on 2017-07-16
I guess out of habit I always run the software updater twice a week and most of the time have an update or two.

---

### Post by Hankbonk on 2017-07-29
[SIZE=2][SIZE=3]@ vasa1 : Sorry for this late response, I was ill .

the output for sudo apt-get update is :
> [/SIZE][/SIZE]Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:3 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:4 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) xenial InRelease          
Hit:5 [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) xenial InRelease                
Get:6 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:7 [http://ppa.launchpad.net/jonathonf/firefox-esr/ubuntu](http://ppa.launchpad.net/jonathonf/firefox-esr/ubuntu) xenial InRelease   
Hit:8 [http://ppa.launchpad.net/meebey/smuxi-stable/ubuntu](http://ppa.launchpad.net/meebey/smuxi-stable/ubuntu) xenial InRelease     
Hit:9 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) xenial InRelease               
Hit:10 [http://ppa.launchpad.net/mkusb/unstable/ubuntu](http://ppa.launchpad.net/mkusb/unstable/ubuntu) xenial InRelease   
Get:11 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Hit:12 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease       
Get:13 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [572 kB]
Get:14 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [493 kB]
Fetched 1.372 kB in 2s (546 kB/s)                                              

Reading package lists... Done[SIZE=2][SIZE=3]
[/SIZE]
[/SIZE]

---

### Post by Hankbonk on 2017-07-29
@ vasa1 and poorguy : 

I ran the software updater for the first time I use Lubuntu LTS, because I used to receive an updater alert before .
It performed a whole series of updates .

Has this changed, meaning : Don't updates come automatically anymore ?

---

