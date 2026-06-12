---
title: "Can only connect to certain wireless networks?"
date: 2010-09-10
forum: Security
---

### Post by LucianJJV on 2010-09-10
Hi, I just recently got an MSI Wind U135 netbook with an Atheros ar9285 network adapter. I had flaky connection problems in windows 7 starter before switching to Ubuntu 10.04. I can now connect to my dads home network with WPA security which I couldn't before, as well as my cousin's home network. however, my dad's OFFICE network which is a mirror image of the home network (same modem same router same ssid and exact same wpa key) won't connect. ? and neither will my own apartment buildings shared network.
i tried installing the ar9k drivers via ethernet (which works just fine) and it still doesn't show up in the hardware drivers but also doesnt come up as a required update anymore.
any suggestions? is the hardware garbage? or is there some setting/software issue? thanks!

<ps i posted this in the wrong section by accident... any way to move it? first time using forums :/

---

### Post by gordintoronto on 2010-09-10
If you can use some networks, the hardware works and the drivers are fine.

What encryption is used on the Apartment wireless? Did you click, "show password"? I've had passwords which I typed incorrectly, and it drove me nuts.

Having the same SSID and WPA key on two networks is an incredibly bad idea.

---

### Post by uRock on 2010-09-10
If your signal strength is really weak, then you may need to install the backports module. Open Ubuntu Software Center and search for backports and select the one for wireless.

---

### Post by cbilljones on 2010-09-15
ignore

---

