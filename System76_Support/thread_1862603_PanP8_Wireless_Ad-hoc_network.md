---
title: "PanP8 Wireless Ad-hoc network"
date: 2011-10-16
forum: System76 Support
---

### Post by theplatapi on 2011-10-16
Hi, 
I'm trying to create a wireless ad-hoc network to connect my phone to the internet in my dorm (Ethernet only). The network works when I leave it unsecured but when I turn on something as simple as WEP my phone or any other device fails to connect. Is this a limitation of the wireless card in the Panp8? By the way I'm still on Ubuntu 11.04.

---

### Post by isantop on 2011-10-18
The new network manager interface in Ubuntu 11.10 offers a lot of improvements to the hot-spot management utilities. You might have a look at that.

Also keep in mind that many devices will not connect to a secured ad-hoc network. Have you tried connecting your phone to a different ad-hoc network with security?

---

### Post by theplatapi on 2011-10-19
I connected my phone to my friends Windows PC which uses connectify, does that count as a secures wireless ad-hoc? Also, I upgraded to 11.10 and now when I click on create hotspot, the hotspot disconnects after like 30 seconds. I guess I have to wait for that feature to mature before I can test again. Thanks for the response though.

---

### Post by isantop on 2011-10-19
Connectify is set up to use Infrastructure Mode (a.k.a. Access Point Mode) by default. Unless the other computer only supported Ad-hoc mode, or if they changed the settings, then you wouldn't have been using Ad-Hoc mode.

What kind of phone is it? I might be able to tell you if it's capable of connecting to Ad-Hoc networks based on the model.

---

### Post by theplatapi on 2011-10-23
My phone is a HTC G2 running Cyanogenmod 7.1.

---

### Post by isantop on 2011-10-26
Android phones aren't capable of connecting to Ad-Hoc networks. I think when you connected it to the other computer, the computer was set to rebroadcast in infrastructure mode. Ubuntu doesn't have the ability to do this.

---

### Post by theplatapi on 2011-10-27
Oh, I see. Thanks for the response!

---

