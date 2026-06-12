---
title: "Windows not recognizing Internet"
date: 2008-07-16
forum: Windows
---

### Post by Bbman90 on 2008-07-16
I know it is blasphemous to have Linux and Windows, but I have a family that refuses to move on. I recently was forced to reinstall Windows. Everything came out fine, but now the internet doesn't work. It still works fine on Linux. Does anybody know how to get it up and running? I have a modem installed, and it's working fine. My Internet Service Provider is RoadRunner HighSpeed.

---

### Post by aysiu on 2008-07-16
You have to find the right driver for the modem or ethernet card.

Do you get the yellow question marks?

---

### Post by lisati on 2008-07-16
I've done this after a reinstall often enough that I should have been able to describe it, but just had to boot up XP to remind myself

If you have a setup disk from your ISP, go for it!

The following should work for XP, there are a couple of minor differences for 98SE, and I don't know about Vista.

Assuming that your modem is working, go to the Control Panel. If you're using XP's category view, click on "Network and internet connections".  Then go to Internet Options, and select the connections tabe.

From there, if you're using dial-up, click on "add" and fill in your ISP's details.

You also have the option of a "setup" button to complete the process - don't forget to select "Automatically detect netowrk settings.

---

### Post by Canis familiaris on 2008-07-16
I think you have to look for the drivers for your hardware. If you know the name of the hardware(In Windows, you use device drivers for that) then search for it and find the drivers.
If you do nto manage tto find the drivers which I think is unlikely, you have two options:
(1) Buy a new ethernet card.
(2) Run Windows in Virtualbox in Ubuntu. Since Ubuntu recognises hardware, so the Virtualised Windows will too and your Windows needs except games would be fulfilled.

[See here to get the feel of it]("http://amitech.50webs.com/ultimate.html")

---

### Post by Bbman90 on 2008-07-16
I do have those question marks. However, I don't know if my computer has the drivers for my modem and whatever else. I don't know if the drivers would still be there after a reinstall. The modem did not come with a CD as far as I know. It says ARRIS on the top, and on the side it says Touchstone Telephony Modem. Does that help?

---

### Post by fiddledd on 2008-07-16
You need to get drivers for your Modem. You'll have to download them from the manufacturer's Website. If you can't identify all your hardware this might help:

[http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)

---

### Post by fiddledd on 2008-07-16
Just found the drivers for you, go here:

[http://www.arrisi.com/support/usb/index.asp](http://www.arrisi.com/support/usb/index.asp)

---

### Post by Bbman90 on 2008-07-16
Thank You! I have the TM5 version. I downloaded the drivers and put them on my Windows desktop. I went to the device manager, and hit update driver. It won't find it. I tried going to the folder manually and selecting the .inf file, but it still won't recognize it. I even burned the folder to a CD, but Windows always claims my driver isn't there. I know I downloaded the right one. Does the name of the CD affect anything?

---

