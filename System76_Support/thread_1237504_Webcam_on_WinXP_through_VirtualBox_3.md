---
title: "Webcam on WinXP through VirtualBox 3"
date: 2009-08-11
forum: System76 Support
---

### Post by samalex on 2009-08-11
I've installed Windows XP through VirtualBox on my PanP laptop (Ubuntu 9.04), and first off the install went smooth and perfect!  Also video playback from several training sites I use (proprietary Windows codecs) works great!

Just curious though, is there anyway to get the webcam to work through Windows?  Just curious... Skype 2 on Linux works and does pick-up the webcam, but Skype 4 on Windows blows all others away.

Thanks --

Sam

---

### Post by miniyak on 2009-08-11
i think getting the webcam to work is a virtual box thing but im not sure

if not, may be you can install the driver and it will work. found here-

[http://knowledge76.com/index.php/Panp4/Panp5]("http://knowledge76.com/index.php/Panp4/Panp5")

---

### Post by samalex on 2009-08-12
[QUOTE="miniyak"]i think getting the webcam to work is a virtual box thing but im not sure

if not, may be you can install the driver and it will work. found here-

[http://knowledge76.com/index.php/Panp4/Panp5](http://knowledge76.com/index.php/Panp4/Panp5)[/QUOTE]

*wince* I didn't think of that :)  I'll install the webcam driver and see if it picks it up.  I just wasn't sure if VirtualBox would've mapped the hardware over since I don't know if it sees the webcam as a USB device or what.

Thanks --

Sam

---

### Post by thomasaaron on 2009-08-13
I'm not really set up to test things under Windows, but the webcam actually *is* a usb device. It's connected to an internal bus. So maybe...

---

### Post by miniyak on 2009-08-13
last time i used virtualbox usb was only included in the non-free version

---

### Post by samalex on 2009-08-13
I tried it yesterday and the driver under Windows XP (through VirtualBox) didn't see the webcam at all, nor is it showing up in the Device Manager.  I did some digging and miniyak is correct that the non-free version does not support USB - [https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB) .  I didn't realize there was an Open Source and Closed Source version... figured it was only open source.  At any rate I didn't see any mention of how to obtain the closed source (non-free) version, so oh well.  Not a big deal I guess.

Sam

---

### Post by miniyak on 2009-08-13
i think the closed source version is free as in beer. It was just a matter of proprietary driver blobs or something. I would have to look more into it.

---

### Post by JeSTeR7 on 2009-08-13
> **miniyak said:**
> i think the closed source version is free as in beer. It was just a matter of proprietary driver blobs or something. I would have to look more into it.

This is correct.  I simply added the official virtualbox repos to my sources and installed it for free.  I can also confirm that enabling usb allows my USB webcam (Acer CrystalEye) to work flawlessly in XP on VirtualBox.

---

