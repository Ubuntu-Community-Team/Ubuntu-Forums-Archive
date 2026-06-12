---
title: "Hot Hand 3 as Controller"
date: 2015-08-16
forum: Ubuntu Studio
---

### Post by ~Glim~ on 2015-08-16
Hi, so I'm looking into the 'Source Audio - Hot Hand 3' as a way to control different sounds. It looks very promising, but can not find anything about using it with Ubuntu Studio. It does state that it can be used by any midi compatible software. It has software included, but I don't see how you would connect it all, please help.

[http://www.sourceaudio.net/products/hothand/hothand_usb.php](http://www.sourceaudio.net/products/hothand/hothand_usb.php)

Does anyone have any experience using this tool and how do you make it work and with what program? 

Firmware in wine -> Jack -> Ardour?

---

### Post by CrocoDuck on 2015-08-17
Hi!

I see that the specifications state "Driverless USB midi operation". This usually means that the device is class compliant. I would expect Linux to be able to talk MIDI with it, but I cannot be sure. In the past, people has been running firmware stuff in wine to configure devices. It was common with some motorized MIDI controllers, so it could actually work. However, I think that the only way to find out is to try. Honestly, I do not recommend to purchase hardware with unknown support, unless you are ready to face quite a struggle. Moreover, I do not recommend to purchase devices that need to be configured with utilities that are not written for your chosen platform. Chances that they will not operate properly are too high. I would suggest to contact the [Source Audio tech support]("http://www.sourceaudio.net/support/tech-support"). The usual answer is "sorry, we do not support Linux at this moment, so we don't know whether it can work"... but who knows, sometimes people do get an answer (like with [Focusrite]("https://focusritedevelopmentteam.wordpress.com/2012/04/23/linux-and-focusrite-novation-products/")).

---

