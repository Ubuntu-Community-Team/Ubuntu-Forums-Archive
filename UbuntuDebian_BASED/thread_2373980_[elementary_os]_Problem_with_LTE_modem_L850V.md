---
title: "[elementary os] Problem with LTE modem L850V"
date: 2017-10-11
forum: Ubuntu/Debian BASED
---

### Post by kronosmasterofalltime on 2017-10-11
Hello Forum Users, and die-hard linux fans!

This is my last chance to solve this problem. I've tried to find some solutions on the web, but nothing really helped. But let me start from beginning.

**BACKSTORY**
My aunt (65) has an elemntary os laptop which served her well for some time. She uses only skype, solitare and certain website or email from time to time. No experience in modern computers (anything more then DOS I suppose) convinced me to install Elementary OS for her since its simple and nice looking. 
However after installing Elementary OS Loki her LTE modem is causing a lot of trouble. It works only from time to time and its reliability depends on usb port I'll stick it in (although neither guarantees 100% reliability). This is confusing and irritating and costs her a lot of nerves. Yesterday I took it (whole notebook) from her to reinstall and try to solve this problem once and for all. 


**NOTEBOOK**
Lenovo G580
Model name: 20150
It has 3 USB ports (all 2.0) I suppose. Two on left side, one on the right side near power input.
When connected to one of those two on left it usually doesn't work, and when connected to the one on the right it usually works but not always.
And since its near the power input its impossible to use usb modem and power together which might cause some problem especially one battery will run out (sooner or later, its ok until now).

[B]MODEM
[/B]Modem is:
TCT Mobile Limited MHY
One Touch L850V 02 027
L850V - 2ATBPL3
Made in China

It is rather unusual modem because it creates (when works) Local Connection, at least that what it looks like on panel. It is detected as Alcatel MobileBroadBand. 
Maybe that how those modems work, but I can access its local settings  by using website and going to [http://l850.home](http://l850.home) 
My point is that I don't have to enter neither PIN, neither APN / user / password in the system. I just connect it, and after a while (or not) LAN network is detected and it works.

I would like to solve it and to make it work in any USB port.

I must say that I tried original UBUNTU also, but it would be much more confusing for, and still problem persists there also (17.04). 

One more thing I've noticed just now.
When connected to one port on the left (the not working side) it is detected as usb0 (not as Alcatel MobileBroadBand) but it sill receives some ip and works.

[B]THE QUESTION
[/B]So, the question is - is there anything I can do to make it work all the time. Like force system to recognize this USB as particular modem?

Update 1.
This time when connected to one of left USB ports it was detected as Alcatel MobileBroadBand. 
This and previous time I said it was _detected as_ it means when I open Network Settings I see this as a third connection (others being Wifi and Ethernet)

---

### Post by deadflowr on 2017-10-11
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by kronosmasterofalltime on 2017-10-11
When I run *lsusb* i get different results regarding one usb port.

[B]lsusb (part) when modem NOT working

[/B][I]Bus 003 Device 005: ID 1bbb:f000 T & A Mobile Phone
[/I]
[B]lsusb (part) when modem IS working

[/B][I]Bus 003 Device 013: ID 1bbb:0195 T & A Mobile Phone

[/I]So (in theory) if I could force this device to be detected as 0195 it should always work, right?

---

