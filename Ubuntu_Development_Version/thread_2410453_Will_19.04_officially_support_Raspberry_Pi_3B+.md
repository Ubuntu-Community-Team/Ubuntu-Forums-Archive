---
title: "Will 19.04 officially support Raspberry Pi 3B+"
date: 2019-01-15
forum: Ubuntu Development Version
---

### Post by mrjohnc on 2019-01-15
Hi all

I realise this may be in the wrong place (I really tried to find the right place). I'm looking at the support for Raspberry Pi 3B+ [https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi) and it it seems possible to install Ubuntu 18.04 (not the Mate version) with some changes to the bootloader and kernel database etc, which is all beyond me. My question is is it planned for 19.04 to make images available that won't require these changes to make it easier for less technically able people to install it on a RP? If not is there a place I can make request that this happens?

Thanks

---

### Post by him610 on 2019-01-15
I have a couple of Raspberry Pi Model B and a Model 3B. I tried unsuccessfully with *buntu on the Model B, but it did not boot - probably incompatable. I think I will just stick with Raspbian on both of my Pi models. The developers have done a good job on Raspbian, and its fairly easy to configure the way one wants it. Many, many how-tos can be found on [https://www.raspberrypi.org]("https://www.raspberrypi.org")

---

### Post by Topsiho on 2019-01-16
The Raspberry processor is different from the processors used in ordinary laptops and desktops, so the normal images cannot be used.
The instructions for the install of the available special images for Raspberry are, to my opinion (have never done this), very intricate, and probably beyond anyone who doesn't fully understand what he is trying to do :(.
I doubt that for Ubuntu 19.04, which is not LTS and only supported for 6 months, things will be made easier to do.

But maybe you could do what him610 suggests and find a howto you could use. But he was unsuccessful too.

Topsiho

---

### Post by HermanAB on 2019-01-16
Linux, is Linux, is Linux...

Both Ubuntu and Raspbian are based on Debian.

So, just install Raspbian and have fun.  If you want a GUI, do apt install xfce4.

[https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html](https://www.aeronetworks.ca/2017/12/raspberrypi-3-headless-with-ssh.html)
[https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html](https://www.aeronetworks.ca/2018/04/raspberry-pi-video-streaming.html)

---

### Post by howefield on 2019-01-16
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by rsavage on 2019-01-16
To answer the opening post, yes I believe there are (armhf and arm64) pi3 images planned for 19.04. I am not part of the development team, but there is an effort at the moment to make 18.04.2 images available so 19.04 will probably follow if that is successful.  There are problems with how this is implemented at the moment, so the 18.04.2 date is not guaranteed.

I wrote a lot of the instructions in the wiki quoted.  I read a lot about how they are difficult to follow, but I don't see it.  They are not aimed at beginners (it is a server image after all), but there is nothing complicated asked.  Open a couple of text files, copy some files.  That's it for armhf.  You could do it all from a Raspbian or Ubuntu desktop. I am genuinely interested how they can be improved so if you have any suggestions then please let me hear them.

The arm64 instructions do require some previous knowledge, or a bit of reading around about how the debian-installer works.  These definitely could be improved, but the need for arm64 on the pi is pretty niche.  There are problems with using the generic arm64 kernel on the pi, so in part the instructions are meant to deter people.  If you genuinely need arm64 you should have the skills and motivation to figure it out.

Finally the mate desktop works well on the pi.  Nothing to stop you installing that on top of the server image.

---

### Post by mrjohnc on 2019-01-16
Thanks very much for the replies, that's very nice to hear there is movement towards making 19.04 available.

I've tried using Raspbian and found a lot of bugs (e.g I can't connect my bluetooth keyboard) and the bug reporting is very confusing. I've also had issues installing Mate, I don't know what's wrong, just never boots.

As you say I think the reason I'm having issues is that I'm not because your instructions are difficult, just they assume a certain level of knowledge I don't have.

Looks like I'll wait for the 19.04 image, would be really nice to have it working well, I think that RP could be a way of making low cost computers accessible to a lot of people who can afford normal desktop machines (although the currently generation doesn't quite have the hardware specs).

Thanks again

---

### Post by QIII on 2019-01-16
Hello!

I don't know what issues you might be experiencing, but I am running Raspian MATE on my R Pi B3+ without issue.

Were you trying to install MATE after installing Rasbian?

I'd not really count on a port for an interim Ubuntu release.    Canonical will probably produce an ARM port, but the folks at R Pi might not be interested in tailoring it for their products.  That's a lot of resource expenditure.

---

### Post by rsavage on 2019-01-17
@mjohnc I would encourage you to have another look at the instructions.  Have a go at following them, and if you get stuck then have a search on t'internet.  This is the way to learn stuff.  If you really get stuck, then ask on here.  This woud really help me to see what the problem is.

Bluetooth does not work out of the box (don't think this will change in 19.04), but Gentoo have instructions for the pi that can be followed.  I have no experience with Bluetooth.

Not sure what QIII is on about.  Interim releases have always been made for the pi.

---

### Post by rsavage on 2019-01-18
[http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/) but please be aware of [https://bugs.launchpad.net/ubuntu/bionic/+source/raspi3-firmware/+bug/1805668](https://bugs.launchpad.net/ubuntu/bionic/+source/raspi3-firmware/+bug/1805668) (don't be fooled by the 'fix released' status).

---

