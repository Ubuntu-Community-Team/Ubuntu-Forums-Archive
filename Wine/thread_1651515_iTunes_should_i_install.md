---
title: "iTunes should i install?"
date: 2010-12-23
forum: Wine
---

### Post by 21stCenturyBreakdown on 2010-12-23
will itunes work in wine?
should i bother installing it?
and if i do will it work with my ipod?
thanks :)

---

### Post by ronnielsen1 on 2010-12-23
No, it won't work. Use gtkpod or banshee or amarok

[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

---

### Post by matt_symes on 2010-12-23
Hi

The last version that was stable under wine was 7.2 i think. I have never managed to get any later version stable under wine.

If you really want it dual boot or use a virtual machine and install windows and iTunes in that.

Or you can use the open source alternatives.

Kind regards

---

### Post by Spyderkid on 2010-12-23
install VirtualBox from the repositories then install windows then install iTunes in that.

If you really want to.



If you just want to use mess around with music on your iPod install gtkPod

---

### Post by GeekGuy1 on 2010-12-23
yes, you can really install if you want to
[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)

here is explanation oh HOW to install itunes

---

### Post by 21stCenturyBreakdown on 2010-12-23
All i want itunes for is to update my ipod touch firmware..

---

### Post by trinitydan on 2010-12-23
iTunes in Wine will not recognize the USB.  It's a waste of time.  I have personally run iTunes 8 in Wine, but no iPod sync.  Try VirtualBox if you can't get Linux software to work.  If you can get it to work, open source alternatives are better anyway, one reason being that they sync files in both directions if you want.  Not just from the computer to the iPod.

---

### Post by 21stCenturyBreakdown on 2010-12-23
will my ipod work via virtual box?

---

### Post by matt_symes on 2010-12-23
Hi

Virtual box.

Don't get the OSE edition from the repository, use the PUEL version from the oracle web site as the OSE version has _NO_ USB support.

I use wmware though.

Kind regards

---

### Post by Scottmoelker on 2010-12-24
I tried installing iTunes a while ago in Ubuntu with Wine. Didn't work, and I don't have a lot of technical no-how.

Today, I tried with the latest 10.whatever itunes on my Ubuntu 10.10 machine with the updated Wine from the default repos and it installed flawlessly. My screen went black a couple times during installation, some small rendering errors inside the program itself, but I can browse the iTunes store, download and buy music, play music... haven't tried iPod syncing yet but colour me impressed. I have been waiting a long time for this moment.

---

### Post by ImDougy on 2010-12-24
u can install itunes with wine but if that's true that it won't detect usb with wine then ur gonna have to use windows or mac to update ur ipod. but if u just need to manage it and add songs and stuff several linux media players can do that i heard, like banshee and rhytmbox (my 2 faves)

---

### Post by ImDougy on 2010-12-24
yes install windows in virtualbox (any version should work) then install itunes on windows inside the virtual machine. but usually the first time i plug in a usb device in virtuabox it doesn't work so if it doesn't work the first time restart the virtual machine or computer and then try plugging it in again

---

### Post by sffvba[e0rt on 2010-12-24
This is the second thread on Ubuntu Forums I have read with someone claiming they have gotten the latest iTunes to work in Ubuntu... I tried and failed personally and the majority of posts I have read was always a failure...

Problem with using the open source alternatives is they don't work for all iPods (like my Touch)... I would be very grateful if I could use my iPod again one day...


404

---

### Post by matt_symes on 2010-12-24
Hi

Well i can confirm it does install and you can run it in 10.04.

However there are rendering issues and it does seem a bit slow.

I will be testing it over the next couple of days and i will report back. Anybody else fancy giving it a try as well?

The devs have done a good job to get it at least to install though, so maybe they will crack it soon.

Kind regards

---

### Post by cogadh on 2010-12-24
> **21stCenturyBreakdown said:**
> All i want itunes for is to update my ipod touch firmware..
It is an unbelievably bad idea to use a Windows app through Wine to update the firmware on anything, you could very easily turn that nice iPod into a really expensive paperweight. With something that can easily go screwy like a firmware update, you are far better off not trying anything odd and just find a Mac or Win machine to update the firmware normally.

---

