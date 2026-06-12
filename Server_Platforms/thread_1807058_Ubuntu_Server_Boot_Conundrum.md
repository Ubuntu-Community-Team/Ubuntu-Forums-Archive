---
title: "Ubuntu Server Boot Conundrum"
date: 2011-07-18
forum: Server Platforms
---

### Post by Bigeasy on 2011-07-18
Greetings, 

I have been playing with the Unix platform for a couple of years, and decided as a pet project to create my first personal server out of a retired laptop. 

Installation was simple (this IS Ubuntu after all), and I have several services working properly. 

With my first remote reboot however, I have hit a snag.

My laptop(a latitude d520) has...battery issues. As such, I cannot remove the plug from its power-supply without it going dark. This is why I chose to make a server from it, to get some more use out of it before it dies and goes to laptop heaven(my trash). 

The laptop functions perfectly normal so long as the plug is in except for one detail: At start up, before the boot loader, the laptop displays a message alerting of a power-supply anomaly, and waits for user input. 

This stops booting of the system until a key is pressed. I have to call a relative to open the laptop and press F1 to continue the boot. After that, the system functions perfectly(for now).

So my question, after an admittedly long back story, is how does one continue on past this screen without the need to press the key, or bypass it altogether? I think it would be proper as well as convenient to have a more graceful boot process. 

System Specs:

**Operating system** Ubuntu Linux 11.04
**Kernel and CPU** Linux 2.6.38-10-generic-pae on i686
**Processor information** Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz, 2 cores

I will offer any other information that can be of assistance when requested.

Thank you for your time,
Bigeasy

---

### Post by terazen on 2011-07-18
Sounds like you need to buy a new cmos battery.

---

### Post by Entilza on 2011-07-18
Not sure what the message is but it could be the CMOS battery as suggested, otherwise check the BIOS settings if there is an ability to ignore F1 errors or something like that otherwise yer out of luck.  Worst case is getting a new CMOS battery or laptop battery you can check ebay for cheap compatible batteries.  The CMOS battery you should be able to get at any department store hopefully just not sure how hard yours is to take apart and replace.

Post the full message of the bios message before taking the laptop apart tho :)

---

### Post by Bigeasy on 2011-07-18
If that is the case, I guess I will have to wait until my next visit home before I can check the BIOS or change CMOS batteries. 

Thanks for the hints.

---

