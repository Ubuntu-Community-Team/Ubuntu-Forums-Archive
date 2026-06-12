---
title: "Panp7 wireless issue after Natty Clean install"
date: 2011-05-01
forum: System76 Support
---

### Post by scarey9 on 2011-05-01
Wireless wont connect to any networks with any kind of security. It attempts to connect then asks me for the network key. I have a Panp7 with the Intel Centrino 6300 ultimate. 

I had to do a clean upgrade to Natty due to my internet failing halfway through the install portion of the upgrade, it was ugly thanks Comcast. I had to do a full clean install using the 64bit version. I installed the restricted extras and restored the System76 drivers. Everything else seems to work fine. I will attempt to upgrade the firmware to my router(Cisco Linksys E4200) while i wait for a response on this thread.

---

### Post by isantop on 2011-05-02
Does it work on unsecured networks?

---

### Post by scarey9 on 2011-05-02
It works on Unsecured networks. I tried upgrading the firmware on my router, still no dice. Right now i am having to use my guest network.

---

### Post by isantop on 2011-05-05
What is the encryption method you use on your router? We've seen lots of issues with WEP in the past, and I would recommend using WPA2, if possible. It's much more secure to boot.

---

### Post by scarey9 on 2011-05-07
I fixed it.....I feel kinda dumb......Open Network Connections Application and edit the wireless connection. Then go to the wireless security tab and make sure the connection is available to all users. Fixed. 

Thank you for your Support, you guys rock and i know your are really busy with this upgrade.

---

### Post by smarmytime on 2011-05-08
I've had problems with staying online since getting my PanP7 in January, but it's much worse since upgrading to 11.04 (Gnome 3). Unfortunately, my internet provider is Verizon FIOS, so I have to use the router that they gave me, or I lose a ton of functionality on my tv, menus, dvr, etc. It's WEP only, with a 1kb NAT table. I reckon I'll have to figure out a way to bridge it, now that I know WEP is part of the problem.

---

### Post by scarey9 on 2011-05-08
you can plug another router into that router. Just run a patch cable from a switch port on your verizon router to the WAN port on the router you intend to use. I had to do that for a friend who used Verizon's crappy router. He was cool with it when i showed him how easy it was to break his WEP key.

---

### Post by smarmytime on 2011-05-08
Will that disable the wireless on the Verizon router? Or would I have to shut that down manually? And I run an ethernet cable from it to my desktop - can I keep that in place, or should I run a cable from the wireless router I want to use?

---

### Post by scarey9 on 2011-05-09
No, the wireless will not be disabled on your Verizon router, unless you turn it off your self. You can still run a cable from your verizon router to your desktop, no issues. Just plug your second router into a switchport on your verizon router and it should work. The second router will use your Verizon router as a gateway to the Internet, no work needed on your part.

---

### Post by smarmytime on 2011-05-10
Cool man, thanks!

---

