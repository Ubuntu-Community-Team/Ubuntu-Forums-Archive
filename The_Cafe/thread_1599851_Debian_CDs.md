---
title: "Debian CDs"
date: 2010-10-18
forum: The Cafe
---

### Post by Oxwivi on 2010-10-18
I was thinking of downloading and trying Debian, but I was faced with the impossible task of downloading and burning 31 CDs - do they like Baskins 31 Robins or something?

What's up with that frekaing huge collection of CDs? Please advise me!

---

### Post by Spice Weasel on 2010-10-18
[http://debian.org/distrib/netinst](http://debian.org/distrib/netinst)

[http://cdimage.debian.org/debian-cd/5.0.6/i386/iso-cd/debian-506-i386-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.6/i386/iso-cd/debian-506-i386-netinst.iso)

[http://cdimage.debian.org/debian-cd/5.0.6/amd64/iso-cd/debian-506-amd64-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.6/amd64/iso-cd/debian-506-amd64-netinst.iso)

Change the repositories in /etc/apt/sources.list to testing or unstable and then apt-get update | apt-get upgrade if you want one of those.

---

### Post by NightwishFan on 2010-10-18
You only need "CD 1" of any collection for a base install. Please install Debian with an available wired connection. I am pretty experienced with Debian what are you trying to get? Stable, Testing, etc?

---

### Post by m4tic on 2010-10-18
They're still on lenny, so no changes in the desktop experience. I'm not sure whether the download link gives 5.0.6 has been out for a month now

---

### Post by kaldor on 2010-10-18
LMDE :)!

Only CD1 or DVD1 is needed.

---

### Post by CharlesA on 2010-10-18
I actually downloaded and installed off the net install a few minutes ago. Having no unneccessary packages = win! :D

---

### Post by Oxwivi on 2010-10-18
> **NightwishFan said:**
> You only need "CD 1" of any collection for a base install. Please install Debian with an available wired connection. I am pretty experienced with Debian what are you trying to get? Stable, Testing, etc?
Just a stable version, for testing it out. I'm neither experienced nor technical enough with Linux for beta. If only CD 1 is required, what are the others for? Net installer is not for me, my internet speed is too slow.

---

### Post by m4tic on 2010-10-18
> **Oxwivi said:**
> Just a stable version, for testing it out. I'm neither experienced nor technical enough with Linux for beta. If only CD 1 is required, what are the others for? Net installer is not for me, my internet speed is too slow.

Stick with ubuntu

---

### Post by Spice Weasel on 2010-10-18
> **Oxwivi said:**
> Just a stable version, for testing it out. I'm neither experienced nor technical enough with Linux for beta. If only CD 1 is required, what are the others for? Net installer is not for me, my internet speed is too slow.

If you don't want to install over the net then you'll have to download a few separate images or order a CD. That's the choice.

---

### Post by NightwishFan on 2010-10-18
I am inclined to agree perhaps Ubuntu would be a better option however Debian is not that hard except at first. I would say test it in a virtual machine first. I will put it this way. I like both a lot however 90% of the time I am on Ubuntu.

Installing from the CD1 or the net install is no different. However the install process will take a lot longer on the netinstall if you have slow internet. (It will take just as long to download the CD1 however you can multitask while doing that).

This site is a bit dead however the information is less than a year out of date (which is fine for Debian). I used to contribute here and it has some nice tutorials.
[http://www.linuxadventures.net/](http://www.linuxadventures.net/)

Debian has forums as well.
[http://forums.debian.net/](http://forums.debian.net/)

And Debian Support:
[http://www.debian.org/support](http://www.debian.org/support)

Have fun. You will be surprised to learn there is not much difference. Debian even has the software center and plymouth (if you want)l.

---

### Post by CharlesA on 2010-10-18
> **Spice Weasel said:**
> If you don't want to install over the net then you'll have to download a couple massive DVD images or order a CD. That's the choice.

Yep. I've messed around with debian and that was a huge "put off" for me, since my net connection isn't that good and the downloads would take a while.

However, I just downloaded the net install and deselected everything during install, so I can only install what I actually need, and it's not that bad tbh. :)

---

### Post by snowpine on 2010-10-18
The multi-CD/DVD sets contain the entire Debian repository and are useful if you have no internet connection at all.

If you are connected to the web (even a slow connection) you only need CD 1 (or the netinstall).

Also keep in mind the Debian installer is **not** a Live CD (unlike Ubuntu) so if all you want to do is "try Debian" check out Debian Live: [http://live.debian.net/](http://live.debian.net/)

---

### Post by Oxwivi on 2010-10-18
I just need a functional web browser (Fx), IMer (Empathy), Office (LibreOffice/OOo), video and audio player (Rhythmbox and Movie Player), torrent download manager (Transmission) and CD/DVD burner (Brasero). If I can get them trhough CD1 - doesn't matter if I have to download only those - then I'm more than happy.

---

### Post by NightwishFan on 2010-10-18
You will find CD1 quite lacking, some of that software is on there however it will certainly require downloading. How slow? My net is around 200kb/s and I found Debian manageable. (About an hour of downloading, I just left and had lunch).

---

### Post by limestone on 2010-10-18
[http://cdimage.debian.org/debian-cd/5.0.6/i386/bt-cd/](http://cdimage.debian.org/debian-cd/5.0.6/i386/bt-cd/)
You'll only need the first one. The other Cd's contains more packages wich you can download later.
These other Cd's are for thoes with less bandwidth.

If you want more package option during install i recommend the DVD.

---

### Post by Oxwivi on 2010-10-18
> **NightwishFan said:**
> You will find CD1 quite lacking, some of that software is on there however it will certainly require downloading. How slow? My net is around 200kb/s and I found Debian manageable. (About an hour of downloading, I just left and had lunch).
Mine is about half of yours. I've been downloading since I read CD1 would be enough (not done yet). Does CD1 support a functional GUI with all the hardware support? What about proprietary drivers?

---

### Post by snowpine on 2010-10-18
> **Oxwivi said:**
> Mine is about half of yours. I've been downloading since I read CD1 would be enough (not done yet). Does CD1 support a functional GUI with all the hardware support? What about proprietary drivers?

CD1 will give you a functional Gnome desktop (if you choose) and plenty of "free" drivers. If you know anything about Debian at all, you would know there are no proprietary drivers in the default install. ;)

Curious if you took the basic investigatory step of trying a Debian Live CD to see if it supports your hardware (and if you like it)? That is what I do when I'm curious about a new distro, but not sure whether I want to commit to a full install.

---

### Post by Oxwivi on 2010-10-18
> **snowpine said:**
> CD1 will give you a functional Gnome desktop (if you choose) and plenty of "free" drivers. If you know anything about Debian at all, you would know there are no proprietary drivers in the default install. ;)
Neither does Ubuntu, but I'd like to know if I can download em from their repo or something.

---

### Post by snowpine on 2010-10-18
> **Oxwivi said:**
> Neither does Ubuntu, but I'd like to know if I can download em from their repo or something.

Please be specific. Since I do not know which proprietary drivers you need, I cannot possibly answer the question, except to say that Debian is not Ubuntu, and you'll need to learn a new style of "[asking the right question in the right place]("http://www.catb.org/esr/faqs/smart-questions.html")" if you want to have a pleasant voyage beyond the safe waters of Ubuntu. :)

Generally speaking, most "non free" hardware needs are well-documented on the Debian wiki. For example if you need help with Nvidia graphics, google "debian wiki nvidia" and you get: [http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)

---

### Post by Oxwivi on 2010-10-18
I realise Debian is not Ubuntu which is why I'm asking in the first place. I was asking if nonfree drivers are available generally.

---

### Post by kaldor on 2010-10-18
> **Oxwivi said:**
> I realise Debian is not Ubuntu which is why I'm asking in the first place. I was asking if nonfree drivers are available generally.

Yes, they are.

By default, Debian uses only free software. The only thing keeping it from being recognized as "Free" by the Stallman Cult is the fact they have a non-free repo (disabled by default) and encourage use of non-free software ( drivers, etc)

Maybe LMDE might be the best choice for you to try something new. Check my sig :)

---

### Post by snowpine on 2010-10-18
> **Oxwivi said:**
> I realise Debian is not Ubuntu which is why I'm asking in the first place. I was asking if nonfree drivers are available generally.

This question is much too broad to answer. Which particular "nonfree drivers" are you having trouble finding information about in the Debian Wiki? When you tested the Live CD, which specific hardware devices were problematic, and what were the exact symptoms or error messages? Have you registered for Debian Forums yet to ask your question in the right place?

---

### Post by Oxwivi on 2010-10-18
Ah~ please don't get so worked up, I'm just gathering info about what Debian does, and how it deals with stuff before using it. If I decide to seriously take it up, I'd bother the Debian forums rather than this place.

> **kaldor said:**
> By default, Debian uses only free software. The only thing keeping it  from being recognized as "Free" by the Stallman Cult is the fact they  have a non-free repo (disabled by default) and encourage use of non-free  software ( drivers, etc)
IMO, nonfree solutions should be encouraged if there are no alternatives - same goes for drivers on Ubuntu.

---

### Post by snowpine on 2010-10-18
> **Oxwivi said:**
> Ah~ please don't get so worked up, I'm just gathering info about what Debian does, and how it deals with stuff before using it. If I decide to seriously take it up, I'd bother the Debian forums rather than this place.

I am not getting "worked up" but there is a big difference between "gathering info" and "asking other people to gather info for you." "What Debian does" and "how it deals with stuff" are both questions you can easily answer yourself with a trip to [debian.org]("http://debian.org"). (Hint: the 4th word is "free" with a link to their definition of the word :))

I am not trying to be mean to you, but Ubuntu Forums is a very friendly, warm, fuzzy place... Debian Forums not so much, so take my advice and read [How To Ask Questions The Smart Way]("http://www.catb.org/esr/faqs/smart-questions.html") before you start asking questions over there.

---

### Post by Oxwivi on 2010-10-19
Yeah well, I count more on user's experience than the guides; they don't help much in unique situations or don't cover everything. I'm facing such problems myself, but yet to be helped by anyone on the forum or the IRC.

Thanks for the heads up about the Debian Forums!

---

### Post by NightwishFan on 2010-10-19
On the contrary. I am a member myself at Debian forums and get along with everyone quite well (an I am a jerk).

---

### Post by Oxwivi on 2010-10-19
Hope I meet you there someday. :D

---

### Post by Oxwivi on 2010-10-21
Okay, first impression: Frustrating! I installed with the CD1, there was enough stuff, but Debian painfully lacked in one thing -  wireless adapter detection and usage. Couldn't do nothing without internet.

---

### Post by snowpine on 2010-10-21
> **Oxwivi said:**
> Okay, first impression: Frustrating! I installed with the CD1, there was enough stuff, but Debian painfully lacked in one thing -  wireless adapter detection and usage. Couldn't do nothing without internet.

You were warned several times that Debian only includes "free" drivers in the default install. If your card requires "nonfree" firmware or drivers, you need to figure out which card you have and read the excellent how-to's at [debian.org]("http://wiki.debian.org/WiFi").

---

### Post by NightwishFan on 2010-10-21
I said before ensure you have a wired connection when installing Debian. Unless you are an expert it is essential. Do not judge it by it's cover. If you had a wired connection, it would resemble Ubuntu a lot in the default install and be quite easy to use. :)

If you get the net afterwards you can get the full desktop by running this in a terminal.
```
tasksel install gnome-desktop --new-install
```

---

### Post by Oxwivi on 2010-10-21
It's not a nonfree driver, the adapter connects with a fresh install of Ubuntu.

I guess I missed the part about of wired connection. It's impossible to get it since the ISPs just installed the wireless AP at the telecommunication stuff spot in the house. There are no LAN sockets in any other rooms, and I prefer wired connection too...

---

### Post by NightwishFan on 2010-10-21
Ubuntu includes some non-free drivers. You might need to install zd1211-firmware or etc, depends on your chip.

---

### Post by Oxwivi on 2010-10-21
I thought Ubuntu asks when it needs to install nonfree drivers? Well either way, I guess it won't work out until I get wired net.

---

### Post by NightwishFan on 2010-10-21
Use Ubuntu cd to download Debian package. (Yes at times you have to do strange stuff like this for Debian, you would not believe!) :D
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

Once I did not have any CDs so I was forced to copy a debian cd init archive to the flash drive. Then copy a minimal image in the spare space and manually boot it from usb using a custom grub entry (no usb boot on that machine). Only to find out that someone borrowed my ethernet cord for their xbox360, and I had to boot into an ubuntu live cd to get the zd1211-firmware and place it in my debian drive, and then FINALLY reboot into debian install the firmware. Oh wait cd1 did not have network-manager, so I had to manually connect to wireless using ifconfig/iwconfig/dhclient. Then when that worked I could install the rest of the stuff I needed. I think I actually left out some wizardry I did with it, it was rough but worth it.

Debian is not actually hard to use it is hard to set up sometimes! If you have a wired connection by default it sets up a full desktop for you. :D

---

### Post by Oxwivi on 2010-10-21
So can you tell me how and what package do I install to enable my wireless adapter? I just remember the name starting with RTL-numbers. Oh, and the only Ubuntu CD I have is the alternate CD. Oh, what's the network manager on Debian? Didn't see nm-applet around.

---

### Post by NightwishFan on 2010-10-21
It is the same as Ubuntu, the package is called network-manager-gnome. nm-applet is the command to start it. No I do not believe it is included in CD1.

Try running lspci or lshw -C network to find out what your hardware is named.

---

### Post by Oxwivi on 2010-10-21
What do I do after finding the name of my hardware?

---

### Post by NightwishFan on 2010-10-21
Search debian packages for the firmware or google "linux *nameofhardware* driver". Or tell me and I can search as well. Then you can manually install it, however you will not get far without a network manager. :/

---

### Post by Oxwivi on 2010-10-21
I shall install the network manager, what command?

---

### Post by Oxwivi on 2010-10-21
Oh, and wouldn't I find the driver on the Ubuntu CD as well?

---

### Post by NightwishFan on 2010-10-21
No, I would use the Debian one. Ubuntu and Debian are not "completely compatible". Also (sadly :( ), it is not "what command" you need the packages from the net. If you get the driver you can connect to an unencrypted wireless using the command line running these three commands. If it says command not found the package "wireless-tools" is certainly on the Debian CD1.

```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid NAMEOFWIFI
sudo dhclient wlan0
```

---

### Post by Oxwivi on 2010-10-21
I found the hardware to be RTL8187, is it possible to install the driver from the Ubuntu CD?

---

### Post by malspa on 2010-10-21
Oxwivi, no offense, but I've installed Debian a few times; there's plenty of documentation available, have you followed any of it?  It pretty much walks you through things.

As for the CDs, when I was on dial-up I was able to obtain 5-CD sets from a vendor for Etch, and then again for Lenny.  I had a high-speed connection for Squeeze, so I downloaded the 1st CD and then downloaded the rest of the stuff I needed.  Basically just following the instructions from Debian's documentation.

Not as easy to install and set up as something like Ubuntu, but I haven't ended up having to ask many (if any) questions at the Debian forums (although there are points during the installation where I didn't know how to proceed and I just winged it).

---

### Post by NightwishFan on 2010-10-21
Seems like this might be complicated actually. :O The Lenny (Debian Stable) kernel does not have the module included yet.
[http://wiki.debian.org/rtl818x](http://wiki.debian.org/rtl818x)

---

### Post by Oxwivi on 2010-10-21
I'm too lazy! But seriously, the Debian guides are daunting, and I seriously doubt they've anything with USB wireless adapters, but will try looking through them.

---

### Post by Oxwivi on 2010-10-21
Just found the link as I posted the last message. It's not loading. I'm thinking of giving up Debian for the future.

---

### Post by NightwishFan on 2010-10-21
Quite alright. It is still a bit iffy for newer users. However it is in essence just out of date for your hardware. :/ The next release "Squeeze" is due out soon with a more modern kernel. When finally set up Debian and Ubuntu are not different much. Debian even has the "Software Center".

---

### Post by Oxwivi on 2010-10-21
Okay, so it loaded, how the hell am I supposed to take the package to that PC? I mean how do I download the package in the first place?

---

### Post by NightwishFan on 2010-10-21
I do not have an answer for you. You can manually download packages from any pc and use a flash drive to transport them. I do not recommend this method as you can run into dependency issues. :/ You really do need the net (or the dvd/first 2-3 cds) to set up Debian offline.

---

### Post by Oxwivi on 2010-10-21
I don't see the way to manually download. Dammit, it looks like I'll go nowhere on Debian on net. I'll take care it when the normal Ubuntu CD download completes.

TT_TT

---

