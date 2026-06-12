---
title: "md5 hash never correct and cant install server via usb"
date: 2015-05-22
forum: Server Platforms
---

### Post by Silman on 2015-05-22
I am trying to install ubuntu server for the first time, have downloaded the 14.04.2 64 bit version twice and both times i get the same md5 hash which is NOT the one listed on the webpage

i keep downloaded iso with this hash:
6760D110781CF915A283AFCB25868DE8

but the ubuntu website says
[COLOR=#333333][FONT=Ubuntu]83aabd8dcf1e8f469f3c72fff2375195
is the hash it should be.

Moreover i tried to install this anyway via USB by burning the iso to a usb using uNetBoot in windows and I get a problem when it tries to detect my CD ROM

i says something like "cannot detect and mount CD ROM," even though i DO have a CD Drive on the computer i am attempting to install it on I am just trying to get it to install via usb. I tried doing the fixes listed [here]("http://ubuntuforums.org/showthread.php?t=1750464") to fix it but when i attempt to mount /dev/sdb (or sdb1 as it as was listed for me, but i attempted both with the same result) it says the device is busy or its resources or being used or something to that effect.

How come the hash is wrong and how the hell do i install via usb? You would figure canonical would make usb installations easier now that they are basically the most common method.....

Please help i have been attempting a fix for hours and havent gotten anywhere...[/FONT][/COLOR]

---

### Post by QIII on 2015-05-22
Hello!

By what means did you download it and from where?

---

### Post by Silman on 2015-05-22
> **QIII said:**
> Hello!

By what means did you download it and from where?

i clicked the big orange download button located here

[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

---

### Post by QIII on 2015-05-23
Did you torrent it?  I usually get better downloads using a torrent client.

---

### Post by sudodus on 2015-05-23
> **QIII said:**
> Did you torrent it?  I usually get better downloads using a torrent client.

+1

The torrent method has a built-in check of the md5sum.

And when you have a good iso file (that matches the md5sum), you can go ahead with some help from the following link (in spite of its name)
[URL="http://ubuntuforums.org/showthread.php?t=2279303"]
Cannot install Ubuntu server from USB[/URL]

There might be a minor bug, but

> In "Your installation CD-couldn't be mounted." message window. I just click [no] and magically it started to work                  

---

