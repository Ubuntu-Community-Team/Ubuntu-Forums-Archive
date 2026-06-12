---
title: "Goodbye Ubuntu. After 7 years I'm changing my distro. Ubuntu is not usable any longer"
date: 2011-08-09
forum: Testimonials &amp; Experiences
---

### Post by Repgahroll on 2011-08-09
Hello there.

Just posted this to say that I'm giving up on Ubuntu, I've been using Ubuntu since the first release and maybe the opinion of a long-term user is important to someone.

On my desktop I'm using the LTS version.

The reasons why I'm moving to another distro are:

On the year of 2008 I bought an Acer Netbook model ZG5/AOA150. At that time I tested Ubuntu from a Live USB and a lot of things worked perfectly, Wifi was the only hardware that didn't work at all, however, I gave up mostly because of the very short battery life and the fan and HDD problem. I repeated the procedure the next year and the Wifi was working, but still not usable because of the HDD and fan.

Last month I was browsing the Ubuntu website and found that "Certified Hardware" page, where my Netbook is listed as a certified hardware, and it displayed the link to download the latest Ubuntu version.

I was on Windows 7 and it displayed the step-by-step on how to transfer Ubuntu to a USB drive, so I followed it, and it was very frustrating because that software took 1 hour to copy the contents of the downloaded ISO to the USB drive. What's wrong with UNetBootin?

Okay, after that I booted it on my netbook and launched the installation. I partitioned the HD manually (an ext4 part mounted as / and a 2GB swap) and installed.

It was working okay, however, there were no indication regarding the Wifi card state, I asked on the forums and after 5 days upping the post frequently no one answered not even to say "it's not possible". So i figured out by myself that it was possible to get the information from system commands, so I programmed a tray icon that shows the Wifi card state and let the user access basic functions like turning it on/off and reloading the module (ath5k).

Next issue is that the mic has an unacceptable amount of noise, this issue doesn't seem to have a solution, maybe it's a pulseaudio issue but I'm not sure, it's okay to me anyway, I don't need the mic at all.

After solving the Wifi issue and living with the noisy mic, I decided to test the webcam, and for my surprise, it wasn't working. I googled two entire days and tried everything, lots of modules and applications, after trying exhaustively to get it to work, I filled a Bug on Launchpad.

Until that moment I was using a mobile broadband (USB Modem), then my quota reached the limit and i had to plug the netbook on a wired network. After setting up the DSL I had to reboot the computer because the newly created connection didn't showed on the network manager and even after rebooting and trying to connect it didn't work. I had to use a router to connect to the wired internet. (I didn't try pppoeconfig from terminal... anyways)

After that, I wanted to try updating the kernel to see if with a new one the webcam works, however, after updating to the latest one and rebooting, for my surprise the wired interface and the card readers weren't working any longer, nor the webcam. I've rebooted and still the same, so I uninstalled the latest kernel (the linux-image-generic-x) package and rebooted, and after that the wired interface was still not working.

At that time I decided ubuntu is not usable any longer. It's easier to configure linux from scratch than getting ubuntu to work.

Is this what they call "Certified Hardware"? Only the keyboard and the screen works and it's already certified?

The best Ubuntu version ever in my humble opinion was Dapper. The community was small but helpful, and every package was tested before being added to the repo. After that the developers prioritized appearance over stability and usability, so it collapsed in the disastrous nowadays versions. The community is bloated an only answers stupid questions. The real issues no one helps.

I know it's not ubuntu devs fault, because they didn't program the faulty software (like the kernel or kernel modules, pulseaudio, etc). But the packages should be better chosen.

I'm looking for another distro preferably a debian-based one, but if it's not possible I'm gonna stick with Arch.

Thank you for reading.
Goodbye.

PS:Sorry my English

---

### Post by XubuRoxMySox on 2011-08-09
Wow, I'm so sorry you had all that trouble! I'm not sure how the "certified hardware" thing works, but it sounds like it completely failed you this time.

The good news is that there are a zillion Linux distros to choose from! I will stick with the LTS versions of Ubu, Xubu or Lubu until they no longer work for me. If/when that happens I'll bid a fond farewell to my beloved first - and currently exclusive) distro with no hard feelings, just gratitude for the introduction to Linux and FOSS.

Good luck, and stop by to say hello sometimes!

-Robin

---

### Post by snowpine on 2011-08-09
Sorry to hear about your problems with Ubuntu on your Acer netbook. I agree with much of what you say (and I am not an Ubuntu user myself for many of the same reasons).

However are you aware that your A110 ZG5 model is specifically **not** certified for 11.04, possibly for the exact reasons you mention?

[http://www.ubuntu.com/certification/hardware/200905-2911](http://www.ubuntu.com/certification/hardware/200905-2911)

---

### Post by leclerc65 on 2011-08-09
I have exactly the same machine, and it serves me well with Lubuntu 11.04 and virtualboxed XP. The only hack I have to put in is the Fan Noise control and the only complaint of mine is not long enough battery time.

---

### Post by Repgahroll on 2011-08-09
Thank you very much for your support and kindness guys.

That's unusual leclerc65, Ubuntu 11.04 provided long hours of battery life (2h10m). With wifi and sound hardwares turned off. The very same hardware only lasts 1h30m running Windows. Possibly because I don't know a way to actually turn the Wifi and Sound cards "off" on Windows instead of just disabling/muting them. Also, the HDD spindown configuration helps to improve the battery life.

Does the wired network, webcam, microphone adn wifi works? Even after updating the kernel to the .30 version? Is yours a ZG5 HDD AOA150? Could you post the returns of lspci and lsusb please?

Thank you.

---

### Post by hakermania on 2011-08-09
Bye, I hope you'll switch back when 12.04 comes out :)

---

### Post by FormatSeize on 2011-08-09
> **Repgahroll said:**
> At that time I decided ubuntu is not usable any longer. It's easier to configure linux from scratch than getting ubuntu to work.
:D
There might be some truth to this statement. I've successfully completed LFS, but it still just might take me ten minutes to get the sound working in *buntu. But it seems to me that *buntu seems to be less and less stable as the years go by is because of the sheer amount of things that could possibly go wrong, in addition to there being more new users that don't know what to expect from GNU/Linux. In other words, not everyone is going to install an OS fully aware that things are definitely going to break, if they aren't broken already.
 
When I first began on this adventure, I really didn't have any problems, because I really didn't have anything. I had an ancient laptop, and the only components was a wireless card. All I had to do was go in the menu and cut it on (which, at the time, I thought was stupid), and I never did any other configuration other than updates. But now, there are more and more people with more and more crap attached to their computers and programs to run them. Of course, devs and whoever else can't possibly account for all of this stuff, and then someone like you comes along with the perfect storm of hardware/software incompatibilities and it seems as if your computer is caving in. Then people recall how everything in Windows "just worked", and think about going back because, of course, Linux sucks now. 
 
Truthfully, it's not the distro. The distro is never to blame. Even if it was the case that the distro is terrible, the user has the ability to change whatever it is that is bothering you. Also, I don't see why Ubuntu configuration problems cause people to flee to another Linux/GNU distro. They're the same thing, it's just Ubuntu has a much higher concentration of useless (but pretty!) things to look at and applications designed to waste your time (but only you get to sit in front of your computer while you waste your time). Arch just takes all that stuff out and lets you install it if you can do the impossible and install the distro itself.

---

### Post by el_koraco on 2011-08-09
You have a lot of patience. When I'm test driving a distro or a distro release, and encounter more than three PITA bugs, I just wipe the thing off the hard drive and forget about it.

---

### Post by leclerc65 on 2011-08-09
2 1/2 hrs is not enough for me.:D
I don't have a microphone to test.

Yes the model is ZG5.
Here is the output of lscpi & lsusb. 


```
** lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
** lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
```

---

### Post by Tamlynmac on 2011-08-09
> Repgahroll

Sorry you had problems.

For my family & I 11.04 was deemed unacceptable (refuse to argue the merits of 11.04 in this section of the forums - per sectional guidelines). Another member in the forums advised trying Xubuntu and after installing it on our two desktops the family feedback has been extremely positive. After support runs out for 10.04 (2013), I'll switch our other 3 systems over.

Bottom line is that one should use what works for them and not worry about that which doesn't. I wish you the best and hope you find success with which ever OS meets your needs. Fortunately, there's plenty of Linux distros to pick from, including Arch. ;-)

Good Luck

---

### Post by wolfen69 on 2011-08-10
> **Tamlynmac said:**
> 

Bottom line is that one should use what works for them and not worry about that which doesn't.

That sounds familiar. <scratches head>

---

### Post by Tamlynmac on 2011-08-10
> wolfen69
That sounds familiar. <scratches head> 	


:lolflag: Never said it was my theory.

Perhaps, I may have been inspired by another member, you might even be that member. :wink:

I hate realizing that my memory isn't what it used to be. Guess I might be getting hmmm (delayed response) "not younger". :)

Mac

---

### Post by stalkingwolf on 2011-08-11
RE battery life.  FWIW i recently purchased an IBM T42p,  i set it up dual boot.  The battery life was almost double with superos 10.10 compared to XP.

---

### Post by vcrpex on 2011-08-14
Goodbye. I agree with using what works for them as well. I started since 9.04, still using 9.04 on my wife's machine and 10.10 on my desktop and netbook. Sometimes the latest doesnt mean it will definitely be better.

---

