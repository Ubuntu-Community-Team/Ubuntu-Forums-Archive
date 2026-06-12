---
title: "OK!!!  Intrepid Rocks!"
date: 2009-02-20
forum: Testimonials &amp; Experiences
---

### Post by Bean Street on 2009-02-20
We finally got something decent working on our Advantech PCM-3353 Geode LX800 PC/104 board!  Blessed be Xubuntu 8.10, the perfect companion for the 500Mhz Geode...

I just don't know how to say thanks enough!!!

The Hardy build was very tough, and we were stuck on a patched up Centos because of several sticky issues involving Geode/IDE/IT8888 and timers.  But no more!

Our system is a remote, weather-hardened geophysical instrument that has multiple Analog-to-Digital converters, High-Precision clocks, and GPS synchronized sampling.  The real list of lessons learned would fill this page, so I'll just cite a few:

1) Speed settings of IT8888 in BIOS (emulation of ports in our case) are CRITICAL.  Go too fast and the kernel will hang for 2-6 seconds, and you won't be able to figure out why.

2) We were stuck with Jiffie timing until we built a custom kernel.  Ignore the boot message about not being able to allocate a timer.  It worked.

3) 44pin to 40pin IDE adapters work with 80 conductor cables and enable 100 Meg speed.

4) Turning PnP OS on in BIOS, while at the same time disabling ACPI, allowed us to properly reserve the two IRQs that we need, 5 & 10.

5) Not all USB sticks are created equal.  Rebooting only mounts sticks from certain vendors BEWARE!!

So as of just about now, we are switching our OS to Xubuntu.

Just one more time:  THANKS!!!

---

### Post by Armor Nick on 2009-02-20
I don't know what you just said but it sounds cool. Anyways, it's great that Xubuntu works for your computer :D .

---

### Post by Therion on 2009-02-20
> **Bean Street said:**
> 

Our system is a remote, weather-hardened geophysical instrument that has multiple Analog-to-Digital converters, High-Precision clocks, and GPS synchronized sampling.

Sooooooo... You mean to say you can finally watch YouTube videos?  

Cool!

---

### Post by Bean Street on 2009-04-20
A few more notes:  (Xubuntu)

1. Must set BIOS to boot without keyboard attached.

2. The Network-Manager widget thingie fought our static IP address, argh.  Until we modified /etc/networking/interfaces to include a static entry, it doggedly put forth a DHCP connection.  It still does, so there are still two devices, and it protects the one it added "ifupdn" and will not let us remove it?

3. Also, the presence of the Network-Manager thingie does not apparently complete initialization of the network interface until login occurs.  We had to enable automatic login...  HUnh?  This is what I must do today... Find out how to remove it.

All-in-all though we are in now, and the first of our fifth-generation systems is activated!  So again my thanks  Ubunut/Xubuntu team...

B.S.

---

### Post by LiamWilson on 2009-04-20
> **Bean Street said:**
> 
Our system is a remote, weather-hardened geophysical instrument that has multiple Analog-to-Digital converters, High-Precision clocks, and GPS synchronized sampling.  

Wow, is this thing some sort of Mainframe Pc from the 70's?

Glad to know the Gnu/Linux Xubuntu experiance is working out for you though.

---

### Post by lukjad on 2009-04-20
> **Armor Nick said:**
> I don't know what you just said but it sounds cool. Anyways, it's great that Xubuntu works for your computer :D .
+1 :D

I'm happy to hear of satisfied customers.

---

### Post by Crafty Kisses on 2009-04-20
He's working on Xubuntu right now! [http://www.softsmith.ca/Professional/Portfolio/images/IBM%20360%20Model%2050.jpg](http://www.softsmith.ca/Professional/Portfolio/images/IBM%20360%20Model%2050.jpg)

---

### Post by Bean Street on 2009-04-22
D'oh!  That was back when I had HAIR

---

### Post by Comhra on 2009-04-22
F-Spot hasn't worked since Feisty, other than that, no complaints.

---

