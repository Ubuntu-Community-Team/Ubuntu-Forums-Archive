---
title: "Updating from 10.04LTS to 12.04LTS"
date: 2012-09-19
forum: System76 Support
---

### Post by RedRat on 2012-09-19
Does System76 provide an update disk or better yet their own version of the LiveCD? I know that they have specialized drivers for their machines. Or can you do a complete clean install from the Ubuntu LiveCD from Canonical? 

I know that in the last few month, they did provide a web page reference that took you through the update, step by step.

---

### Post by Ubun2to on 2012-09-21
I did not receive a reinstall disk, but the process is simple enough.
1. Install or upgrade Ubuntu.
2. If you did clean install, install System76 drivers application.

---

### Post by RedRat on 2012-09-21
> **Ubun2to said:**
> I did not receive a reinstall disk, but the process is simple enough.
1. Install or upgrade Ubuntu.
2. If you did clean install, install System76 drivers application.
Ok, I suppose I can download the drivers from System76. 

Another question: I am not a big fan of Unity and run Gnome Classic on my other computers. Can you do this with the System76 drivers for 12.04? The reason I ask, is that the System76 rep that writes here said that it would not be possible to run Mint 13 on a System76 laptop (I have no intention of putting MInt on my Serval Pro). However, I believe that Mint is kind of a halfway house between KDE and Gnome. Just wonderin'.

---

### Post by jbelmonte on 2012-09-22
> **RedRat said:**
> Ok, I suppose I can download the drivers from System76. 

Another question: I am not a big fan of Unity and run Gnome Classic on my other computers. Can you do this with the System76 drivers for 12.04? The reason I ask, is that the System76 rep that writes here said that it would not be possible to run Mint 13 on a System76 laptop (I have no intention of putting MInt on my Serval Pro). However, I believe that Mint is kind of a halfway house between KDE and Gnome. Just wonderin'.

The System 76 driver is an Open Source Python program that will work on System 76 hardware running Operating Systems that identify themselves as Ubuntu such as Ubuntu itself or Kubuntu. The System 76 driver will not make any modification on non-System 76 hardware or on Operating Systems that do not identify themselves as Unbutu. 

Since the System76 driver is open source, you can read the python code to see what it does for your System 76 hardware on specific flavors of Ubuntu.  A year or so ago, someone modified the System 76 driver so that it would run on Mint. This is possible because Mint is based on Ubuntu. He posted instruction on how to do that in the forum. I am not recommending that anyone do this. I have no idea if those instructions are still valid or if going down that path would void the warranty.

All that being said, I am pretty sure that you could install Mint on your Serval Pro. The only question would be whether everything would work properly without tweaking. Does Mint have a Live CD you could try?

---

### Post by bakelitedoorbell on 2012-09-22
This is the link to the clean install instructions:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

You install the standard Ubuntu and then run the System76 driver.  That's it.

---

