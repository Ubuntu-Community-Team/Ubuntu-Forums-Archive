---
title: "Why I won't stay on Ubuntu and will be back on Windows"
date: 2010-03-08
forum: Testimonials &amp; Experiences
---

### Post by tamiii on 2010-03-08
Hi there,

Here is my story: I got an Asus UL30V laptop provided with Windows 7 and it was working really fine.
I just wanted to install Debian at first for professional reasons but it appeared the network interface and my wireless were not known. It was kinda of a pain to restart on windows, download the drivers and install them on debian.

So I decided to switch for Ubuntu, as I knew the driver support for the recent computers was really great. And yes indeed everything is working fine so far EXCEPT this wireless which is deconnecting all the time (Atheros AR9285 Wireless).
I dont know where it comes from but Ubuntu keeps deconnecting me from the wireless network and reconnect straight after... While on windows I never had this problem.

So I will just end this post by saying: Ubuntu is not ready (yet) for my business purpose as it still lacking a bit of driver support... "I just (almost) works".

---

### Post by DeadSuperHero on 2010-03-08
> **tamiii said:**
> Hi there,

Here is my story: I got an Asus UL30V laptop provided with Windows 7 and it was working really fine.
I just wanted to install Debian at first for professional reasons but it appeared the network interface and my wireless were not known. It was kinda of a pain to restart on windows, download the drivers and install them on debian.

So I decided to switch for Ubuntu, as I knew the driver support for the recent computers was really great. And yes indeed everything is working fine so far EXCEPT this wireless which is deconnecting all the time (Atheros AR9285 Wireless).
I dont know where it comes from but Ubuntu keeps deconnecting me from the wireless network and reconnect straight after... While on windows I never had this problem.

So I will just end this post by saying: Ubuntu is not ready (yet) for my business purpose as it still lacking a bit of driver support... "I just (almost) works".

Sorry to hear that, buddy. =/

Did you try wpasupplicant, if it wasn't already installed?

I could've sworn that Atheros Wifi natively had a Linux driver.

---

### Post by Rainstride on 2010-03-08
> **Mr. Psychopath said:**
> Sorry to hear that, buddy. =/

Did you try wpasupplicant, if it wasn't already installed?

I could've sworn that Atheros Wifi natively had a Linux driver.

it does have a native driver, but you have to install it...
(system > administration > hardware drivers)

---

### Post by NightwishFan on 2010-03-08
Your concerns are valid, and thank you for posting them. Criticism can only make free software better when it is correctly given. Please note this. If you installed Windows Xp on your hardware, do you think there is a chance wireless would work out of the box? Probably not, however Windows has the advantage of being a must have for support due to it's large market share. It will obviously have drivers available *somewhere* or the vendor would go out of business.

On Linux, developers, sometimes non paid volunteers have to reverse engineer hardware to scrap up open source support. Though most hardware works great, not all is expected to run perfectly. However, if you want to fix your problem and continue to use Ubuntu, please post a thread in the the general help or beginner talk forums, and link the thread here.

My first bit of advice is to run this command in a terminal so we can find out your exact hardware and locate support for it.

```
sudo lshw -C network
```

---

### Post by tamiii on 2010-03-08
@Mr. Psychopath: I didnt try wpasupplicant (yet!)
@Rainstride: nothing available in the Hardware Drivers

@NightwishFan:
[PHP]
pierre@debian:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:7c:8f:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.168 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:5b:96:8f
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:febc0000-febfffff ioport:ec00(size=128)
[/PHP]

---

### Post by realzippy on 2010-03-08
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)


...could help.

---

### Post by NightwishFan on 2010-03-08
Some random responses I got were:
> The ath9k driver which handles the AR9285 chipset is standard in kernel 2.6.29 and greater.

Try:
```
sudo apt-get install linux-backports-modules-karmic-generic && sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

---

### Post by 3rdalbum on 2010-03-08
Or try Lucid. My new netbook's Atheros wifi works rock-solid on Lucid.

---

### Post by coldraven on 2010-03-08
A couple of years ago I was running Ubuntu on an ancient Dell laptop (433Mhz) with an Atheros PCMCIA card. It worked just fine!
I can't believe this is a problem with a recent version.
I read somewhere that if wi-fi is turned off (with a button on your laptop) when you install Ubuntu then it can cause problems.
I always make sure that wi-fi is ON in windows before doing a Linux install.
Some of these "buttons" are software enabled.
Hope you persevere and find the answer.

---

### Post by Post Monkeh on 2010-03-08
> **NightwishFan said:**
> Some random responses I got were:


Try:
```
sudo apt-get install linux-backports-modules-karmic-generic && sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

i had to do this to get my atheros card to stop dropping its connection. been a couple of months since and everything's been great.

---

### Post by coffeecat on 2010-03-08
> **NightwishFan said:**
> Try:
```
sudo apt-get install linux-backports-modules-karmic-generic && sudo apt-get install linux-backports-modules-wireless-karmic-generic
```

+1 with that.

The backports modules give you the ath9k driver from the 2.6.32 kernel, which works much better - you don't get the disconnects. A lot of people with the Atheros AR9285 and AR928X chipsets are finding this fix helpful.

If this is the only problem that has driven you back to Windows, then I am surprised and saddened. There are plenty of threads describing the backports fix for Atheros wireless.

---

### Post by tamiii on 2010-03-11
Guys,

I upgraded to lucid alpha and the wifi is working really great. Now the only problems is that it's not stable at all for the moment :x

But anyways I'll wait till the LTS release :)

I'm back to ubuntu now.

---

### Post by bonethug on 2010-03-11
> **tamiii said:**
> 

I'm back to ubuntu now.

Tamiii, just to let you know..
Since I've cleaned up my Windows partitions on my HP mini and installed Ubuntu,
I never thought about to switch back to Windows. Ever.

Why? Ok, I'll give you some main reasons. ;)


#1
Ubuntu is free (remember to support the cool developers!) and I really don't like to spend my hard made earnings to pay for an unstable, buggy, memory eating monster called Windows. No matter which version of Windows you have currently in mind. I don't like them and I never did, though I was using them for years..

#2
Ubuntu supports so many desktop modes with beautiful themes. Windows design is odd (for me at least) and I'm again not interested into buying an 3rd party, memory eating graphical application that would pimp up my GUI look. 

#3
Ubuntu has wonderful package tools like apt-get, aptitude and synaptic packet manager. Let's not forget the cool terminal!

#4
Ubuntu is more secure from viruses and spyware and It gives the user more control of the computer.

#5
You can do in Ubuntu the same things as in Windows, plus many, many more! 

#6 
Ubuntu's support and community forums are good and people always provided me fast the right informations I was asking about. No matter how dumb did they sound..



I'm recommending Ubuntu to everyone who is currently using Windows, and I guarantee much more fun with it. And what's also important, you'll build up your computer knowledge, which will definitely be useful for you in the future, if you want to become an advanced user.


Regards,
bonethug

---

