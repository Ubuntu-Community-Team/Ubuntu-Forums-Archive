---
title: "When to expect major linux uppgrade"
date: 2015-10-05
forum: Ubuntu, Linux and OS Chat
---

### Post by peter206 on 2015-10-05
Since no linux distribution will connect to internet on my relatively new PC I am wondering when can I expect some major (ubuntu) bugfix upgrade?

---

### Post by The Cog on 2015-10-05
Ubuntu 15.10 is due out in 3 weeks (22nd according to the road map).
The final beta has already been released if you care to try it.

Existing Ubuntu releases don't get major upgrades, only security updates. This is for stability reasons.

---

### Post by peter206 on 2015-10-05
> **The Cog said:**
> Ubuntu 15.10 is due out in 3 weeks (22nd according to the road map).
The final beta has already been released if you care to try it.

Existing Ubuntu releases don't get major upgrades, only security updates. This is for stability reasons.


Do you have a link to 15.10? Any other distro to recomend for wifi troubles?

---

### Post by kurt18947 on 2015-10-05
You could download a 15.10 image in your favorite 'flavor'(Ubuntu, Xubuntu LXDE) and create a live DVD/USB. I've been using a 15.10 Mate install for some weeks and it seems pretty stable. A live session should tell you whether your wifi adapter is recognized out of the box. If it isn't there may still be hope via a driver found elsewhere. I keep a USB wifi adapter known to be plug 'n' play even if not the latest and greatest. I can use old standby to download the drivers for the latest shiny.

---

### Post by Bucky Ball on 2015-10-05
For wifi troubles I would advise posting a support thread in Networking and Wireless if you haven't already. Re-installing the OS to a newer one in hopes of a fix is like shooting a mosiquito with an elephant gun if you haven't tried to fix the wireless issue in your current install by asking for help from some of the very experienced wireless gurus here. 

There are absolutely no guarantees an upgrade will make any difference, unless you have done some serious research to ascertain whether it will, and the same fix for your wireless will apply.

---

### Post by peter206 on 2015-10-05
> **Bucky Ball said:**
> ...**by asking for help from some of the very experienced wireless gurus here.** 




Dunno I have active [thread there]("http://ubuntuforums.org/showthread.php?t=2297423") and I even managed to run the damn wireless script but so far never got any useful advice. This is simply not normal. Ubuntu recognises all my cards, settings but it will not connect. I would set for anything right now just to make Ubuntu work, even a canon against a mosquito. :-)

---

### Post by forrestcupp on 2015-10-05
> **peter206 said:**
> Dunno I have active [thread there]("http://ubuntuforums.org/showthread.php?t=2297423") and I even managed to run the damn wireless script but so far never got any useful advice. This is simply not normal. Ubuntu recognises all my cards, settings but it will not connect. I would set for anything right now just to make Ubuntu work, even a canon against a mosquito. :-)

Well, it's an obvious question, but do other devices work with your WiFi? Have you tried unplugging your router/modem for about 15 seconds and plugging it back in? Sometimes resetting the router helps even if other devices work on it.

---

### Post by peter206 on 2015-10-06
> **forrestcupp said:**
> Well, it's an obvious question, but do other devices work with your WiFi? Have you tried unplugging your router/modem for about 15 seconds and plugging it back in? Sometimes resetting the router helps even if other devices work on it.


Everything else works fine. Yes I tried everything with my newbie linux knowledge. The problem is in really poor linux manuals, troubleshooting guides, driver support and modest community help. Everybody assume you have wired internet access and you are making wifi connection out of boredom. On top of this everybody assume you have access to updates and drivers from internet. If you check YT for some video tutorials you will find some million of them hacking wifi but only a few really basic on how to install and setup linux with wifi. Even if you try to get an up to date linux distro it is always specific to damn gui everything else is thrown in more or less by popular vote I guess.  

A complete nightmare and a really bad business model I must say....:-(

---

### Post by yoshii on 2015-10-06
If you want a Long Term Support version, you will have to wait quite a while, but look at this chart:  [https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)
It lets you know when the non-Long Term Support versions lose their support.  This is important to know.  That's why I stick to LTS versions.

---

### Post by Bucky Ball on 2015-10-06
Easiest way?

14.04 LTS. 14 = year. 04 = month. In other words, 2014, April, or April 2014 is when it was released. LTS versions are supported for five years, so ...  April 2019.

15.04. April 2015 release date, as per syntax from above. Interim releases are supported for nine months and come out every six.

LTS can upgrade to the next LTS, skipping the interim releases in between. Interim releases MUST be upgraded by moving through each consecutive interim (until it gets to an LTS, of course, then the choice is yours next time; 15.10> 16.04 LTS> 16.10 or 18.04 LTS when it comes out, for instance). Your only other option with an interim if you want to get from, say, 15.04> 16.04 LTS is a clean install.

---

### Post by peter206 on 2015-10-06
Is 15.10 going to update hardware drivers and linux kernel or it is yet another GUI improvement? Any link/info on what's cooking under the hood in 15.10?

---

### Post by mastablasta on 2015-10-06
as i read the other thread the issue is not in drivers as they work - the issue is you can't connect to your router. you said you can connect to neighbour or to unsecured network. i am not sure this has much to do with drivers).

also drivers are made by manufacturer and if they release drivers for Linux you can use those to patch the kernel with them and do not need ot wait for new kernel to come. but usually they are part of kernel anyway. and you can also upgrade kernel only.


anyway: 

Qualcomm Atheros AR9485 solved: [http://ubuntuforums.org/showthread.php?t=2260577](http://ubuntuforums.org/showthread.php?t=2260577)
Qualcomm Atheros AR9485 Wireless Network Adapter not working on Ubuntu 13.10: [http://askubuntu.com/questions/419867/qualcomm-atheros-ar9485-wireless-network-adapter-not-working-on-ubuntu-13-10](http://askubuntu.com/questions/419867/qualcomm-atheros-ar9485-wireless-network-adapter-not-working-on-ubuntu-13-10)
Wireless problems with atheros AR9485 Wireless Network Adapter.: [http://ubuntuforums.org/showthread.php?t=2082152](http://ubuntuforums.org/showthread.php?t=2082152)
Ubuntu 12.04 and Atheros AR9485 wireless:  [http://ubuntuforums.org/showthread.php?t=1983003&page=4](http://ubuntuforums.org/showthread.php?t=1983003&page=4)
AR9485 with ath9k driver not working in Ubuntu 14.04: [http://ubuntuforums.org/showthread.php?t=2221294](http://ubuntuforums.org/showthread.php?t=2221294)
How do I get an Atheros AR9485 wireless card working?: [http://askubuntu.com/questions/240234/how-do-i-get-an-atheros-ar9485-wireless-card-working](http://askubuntu.com/questions/240234/how-do-i-get-an-atheros-ar9485-wireless-card-working)


Looks like the chip has been around for about 4 years and there are various workaround, manual driver install and patched kernels available (eh kernel patches ?!) & bugfixes.

btw 15.10 has a kernel upgrade.

---

### Post by peter206 on 2015-10-06
> **mastablasta said:**
> as i read the other thread the issue is not in drivers as they work - the issue is you can't connect to your router. you said you can connect to neighbour or to unsecured network. i am not sure this has much to do with drivers).

also drivers are made by manufacturer and if they release drivers for Linux you can use those to patch the kernel with them and do not need ot wait for new kernel to come. but usually they are part of kernel anyway. and you can also upgrade kernel only.


anyway: 

Qualcomm Atheros AR9485 solved: [http://ubuntuforums.org/showthread.php?t=2260577](http://ubuntuforums.org/showthread.php?t=2260577)
Qualcomm Atheros AR9485 Wireless Network Adapter not working on Ubuntu 13.10: [http://askubuntu.com/questions/419867/qualcomm-atheros-ar9485-wireless-network-adapter-not-working-on-ubuntu-13-10](http://askubuntu.com/questions/419867/qualcomm-atheros-ar9485-wireless-network-adapter-not-working-on-ubuntu-13-10)
Wireless problems with atheros AR9485 Wireless Network Adapter.: [http://ubuntuforums.org/showthread.php?t=2082152](http://ubuntuforums.org/showthread.php?t=2082152)
Ubuntu 12.04 and Atheros AR9485 wireless:  [http://ubuntuforums.org/showthread.php?t=1983003&page=4](http://ubuntuforums.org/showthread.php?t=1983003&page=4)
AR9485 with ath9k driver not working in Ubuntu 14.04: [http://ubuntuforums.org/showthread.php?t=2221294](http://ubuntuforums.org/showthread.php?t=2221294)
How do I get an Atheros AR9485 wireless card working?: [http://askubuntu.com/questions/240234/how-do-i-get-an-atheros-ar9485-wireless-card-working](http://askubuntu.com/questions/240234/how-do-i-get-an-atheros-ar9485-wireless-card-working)


Looks like the chip has been around for about 4 years and there are various workaround, manual driver install and patched kernels available (eh kernel patches ?!) & bugfixes.

btw 15.10 has a kernel upgrade.

Thank you for your suggestions. None of above link apply to my case:

- I have NO wired internet access.
- I can't download and upgrade ANYTHING from Ubuntu repositories
- I use USB broadband modem with integrated router and wifi hotspot (not connected to my PC and yes I did try that too - gets recognised with all settings by default!! but it will not connect) 
- I have a standard AMD 64 PC with wireless card in it
- The whole system works perfectly fine on Windows OS
- I tried several linux distros and even latest Ubuntu beta 2 version 
- The chip is officially supported both from manufacturer and from Ubuntu 


My questions is quite simple:

Where EXACTLY does network manager STORES my wifi and password info? It seems like Ubuntu is not ABLE to store that info. Can I do it manualy? Where? 

Another wird anomaly is that the PC will connect to AD-HOC (no internet of course) but NOT in standard INFRASTRUCTURE mode.


This has to be a nasty bug or some really ridiculous setup feature.

---

### Post by buzzingrobot on 2015-10-06
Network Manager documentation links: 


[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

[https://en.wikipedia.org/wiki/NetworkManager](https://en.wikipedia.org/wiki/NetworkManager)

[https://wiki.archlinux.org/index.php/NetworkManager](https://wiki.archlinux.org/index.php/NetworkManager)


The web is full of posts and videos about Linux of dubious accuracy. As it is about pretty much everything.

If a hardware vendor does not release a driver that can be used by Linux, and does not release enough information to allow FOSS developers to write their own, support in Linux may not be possible.

---

### Post by forrestcupp on 2015-10-06
> **peter206 said:**
> Everything else works fine. Yes I tried everything with my newbie linux knowledge. The problem is in really poor linux manuals, troubleshooting guides, driver support and modest community help. Everybody assume you have wired internet access and you are making wifi connection out of boredom. On top of this everybody assume you have access to updates and drivers from internet. If you check YT for some video tutorials you will find some million of them hacking wifi but only a few really basic on how to install and setup linux with wifi. Even if you try to get an up to date linux distro it is always specific to damn gui everything else is thrown in more or less by popular vote I guess.  

A complete nightmare and a really bad business model I must say....:-(

You know how MacOS X can't just be installed on any PC, and how it has to be installed on specific Mac hardware? Linux is the same way. The problem is that for most people, wifi just works out of the box without any trouble at all. Most people don't have to do any configuring or screwing around; it just works. For people who have hardware that is well supported by Linux, most Linux distros work like a charm, which is the same situation with MacOS X. But for people who have hardware that isn't supported well, Linux can be an absolute nightmare.

You have to remember that, for the most part, Linux is about a bunch of developers who don't have access to hardware specs trying to reverse engineer them to create drivers without getting any support from the hardware manufacturer. It's really pretty impressive what they've been able to accomplish. But the unfortunate truth is that if you have hardware that they haven't worked out support for yet and you can't get it to work, you're probably better off just using Windows on that hardware. The best scenario is to study out what is supported, and buy a computer based on that before you try to install Linux. But just like MacOS X, you can't just install Linux on any hardware out there and expect it to work perfectly.

---

### Post by mastablasta on 2015-10-06
> **peter206 said:**
> Thank you for your suggestions. None of above link apply to my case:

- I have NO wired internet access.
- I can't download and upgrade ANYTHING from Ubuntu repositories

bummer.

> 
- The whole system works perfectly fine on Windows OS

yes it does because manufacturer made sure it works and it worked together with windows to get the drivers properly preinstalled.

note how if you buy a Linux preinstalled PC everything works on it out of the box. same goes for the laptops or desktops that have Linux support and ti says which Linux they support. for example HP will say it supports SUSE enterprise Linux. if oyu install SUSE EL or ofte this goes for Opensuse as well it will all work out of the box. with Ubuntu it will usually all work but not necessarily.

Dells will support Ubutnu on some models again if you install Ubuntu on them everything will work.

System 76 will have support for a couple of distros for example. when you get their PC everything will work.

in all these cases manufacturers made sure it works and then announced their support for the model. so if your model officially supports Linux...

> 
- The chip is officially supported both from manufacturer and from Ubuntu 

then ask manufacturer why it doesn't work if it is supported. my guess is, if you follow one of the links and get the driver somewhere else (.tar.gz file) and then patch the kernel with it - it should work.

now why it doesn't work as it should out of the box - drivers are probably not opensource so they can't be included in kernel. or for various other reason it was decided they won't be there. In this case the easiest solution is to wire up and download the driver. you will need to do something like that when drivers fall out of windows support. say when "windows 12" come out or something. you might need to hunt down the driver and install manually. and if you wont' have a wired connection...

---

### Post by peter206 on 2015-10-06
I am going to buy a new linux supported wifi card and modem/router ASAP. I won't give up. For now thanks for kind comments and suggestions.

---

### Post by forrestcupp on 2015-10-06
> **peter206 said:**
> I am going to buy a new linux supported wifi card and modem/router ASAP. I won't give up. For now thanks for kind comments and suggestions.

Great idea. I'd say to start with only the wifi card, though. I highly doubt if the modem/router is the problem. Buying a supported Wifi card should take care of your problem. I haven't used Ubuntu in a while, though, so I don't know how plug-n-play things are now. Hopefully, you don't have to reinstall Ubuntu after you get your new card.

And if you absolutely can't get it working, you may want to just try running Windows as your primary OS and installing Ubuntu in a virtual machine. The virtual hardware in the virtual machine should work with Linux without any problems.

---

### Post by buzzingrobot on 2015-10-06
FWIW, it wasn't all that long ago -- several years -- when getting any wifi hardware working on Linux was difficult.  I know I spent a few hundred dollars on cards someone swore were good for Linux, and never got them working.

I've had good luck with Intel wifi on Linux.

---

### Post by forrestcupp on 2015-10-06
> **buzzingrobot said:**
> FWIW, it wasn't all that long ago -- several years -- when getting any wifi hardware working on Linux was difficult.  I know I spent a few hundred dollars on cards someone swore were good for Linux, and never got them working.

I've had good luck with Intel wifi on Linux.

Yeah, things have come a *long* way as far as hardware compatibility is concerned.

---

### Post by cpatrick08 on 2015-10-07
[h=2][/h]echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9kfix.conf > /dev/null  Then reboot[ https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/251594]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/251594")

---

