---
title: "Any thoughts on the Odroid U3 running Ubuntu?"
date: 2014-06-15
forum: The Cafe
---

### Post by Bucky Ball on 2014-06-15
Hi all,

I have a Raspberry Pi and, while it's been great, our relationship has been a little rocky (actually, the Pi has been fairly rock solid, it is the plugins that have been flaky). Thinking about purchasing the Odroid U3. 

[http://www.hardkernel.com/main/main.php](http://www.hardkernel.com/main/main.php)

It will be plugged into the TV and used as a media server and a regular Ubuntu computer (there is a 14.04 dev release which apparently runs well).

They have an active forum, but thought I'd ask here first. Anyone had any experience running Ubuntu on the Odroid U3? Eager to hear any feedback before I fork out the cash. I know it is a development board, but from most reports, seems fairly solid for what I want to use it for. Is there another beast in the same price range (US$65 + $25 postage) that might be comparable? Couldn't find one. 

Thanks in advance for all thoughts and ideas.

Da Buckster.

---

### Post by Warpnow on 2014-06-16
...so many options...

There's the cubox-i, which ranges in price from $55 and up depending on version, but its a "complete" product with case.

There's the J1900 which is an SOC from intel that runs about $70. Will probably use more electricity but also offer much more power in return. Several different companies make versions of this.

There's the IFC6410 snapdragon for $149 which should offer a good amount of power for not much electricity. 

There's the Gigabye brix for about $130 in barebones form.

There's the mars board RK3066 which is a $60 dual core cortex a9 board. 

There's both the bananapi and the hummingboard which are "upgrades" to the raspberry pi. Same shape, same ports, faster cpu/more ram. 

There's the beaglebone which is ridiculously tiny for $55.

---

### Post by Bucky Ball on 2014-06-16
> **Warpnow said:**
> ...so many options...

There's the cubox-i, which ranges in price from $55 and up depending on version, but its a "complete" product with case.

There's the J1900 which is an SOC from intel that runs about $70. Will probably use more electricity but also offer much more power in return. Several different companies make versions of this.

There's the IFC6410 snapdragon for $149 which should offer a good amount of power for not much electricity. 

There's the Gigabye brix for about $130 in barebones form.

There's the mars board RK3066 which is a $60 dual core cortex a9 board. 

There's both the bananapi and the hummingboard which are "upgrades" to the raspberry pi. Same shape, same ports, faster cpu/more ram. 

There's the beaglebone which is ridiculously tiny for $55.

Umm, thanks, but the question is actually has anyone had experience with Ubuntu on the Odroid U3, not what are the alternatives to the Odroid U3. :-k

Anyone? I've already bought one so any links or tips or experiences would be great. ;)

---

### Post by Warpnow on 2014-06-17
> **Bucky Ball said:**
> Umm, thanks, but the question is actually has anyone had experience with Ubuntu on the Odroid U3, not what are the alternatives to the Odroid U3. :-k

Anyone? I've already bought one so any links or tips or experiences would be great. ;)

You asked, specially... :-p

> Is there another beast in the same price range (US$65 + $25 postage) that might be comparable? 

I don't have any personal experience with the U3. I think most of the ubuntu users are on the odroid XU though its a good bit more expensive. 

Here's a 13.10 download link for a custom version of ubuntu for the U3: [http://com.odroid.com/sigong/nf_file_board/nfile_board_view.php?keyword=&tag=&bid=202](http://com.odroid.com/sigong/nf_file_board/nfile_board_view.php?keyword=&tag=&bid=202)

Also here's how to put Arch Linux on it... [http://archlinuxarm.org/platforms/armv7/samsung/odroid-u3](http://archlinuxarm.org/platforms/armv7/samsung/odroid-u3)

Though I usually am not that into a Arch, Arch is probably a better fit for the odriod given you only want to install the absolute minimum. Having things installed you won't use could lag it quite a bit.

---

### Post by Bucky Ball on 2014-06-17
Thanks. I intend putting a minimal custom install on it, if that is possible. I only use minimal installations with Xfce4 and the few apps I need/want so very pared back approach I have anyhow. I'm not into running a full blown Xubuntu or Ubuntu on it, even though that's what comes pre-installed on the eMMC card. I intend to flash that. 

On the Odroid forums there is a 14.04 devs thread where there is a version of 14.04 LTS ready to download, flash and install ...

---

### Post by mikewhatever on 2014-07-19
I have one, and it's really good. I've ordered it with the PSU and the HDMI cable from Hardkernel, cause you can't power it by a usb cable, and it's microHDMI on the board, so I didn't want to look for the right gear myself. It's been used as a desktop PC for a while with 13.10, then as a multimedia PC with Android. Now it has 14.04 server with transmission daemon.
...as said, no complains, works well indeed, the only problem is the kernel never gets any security updates, ...ever.

---

### Post by Bucky Ball on 2014-07-20
Forgot about this thread. Had my U3 for about a month now and apart from a few teething problems fairly happy with it. Has been running as a media server with Lubuntu 14.04, then with xfce4 desktop environment and currently looking at other options, namely Ubuntu-core armhf image. Hopefully get that up and running this week sometime. ;)

---

