---
title: "An ode to linux hardware support"
date: 2006-08-14
forum: Testimonials &amp; Experiences
---

### Post by rdd on 2006-08-14
I have been extremely impressed with Linux in general and Ubuntu in particular ever since I made the switch in January. I switched primarily for ideological reasons but now I wouldn't go back if XP were OSS. 

The hardware support is great in general (probably with the exception of the ATI X700 in my laptop) but this weekend Ubuntu really blew me away. 

I got a new cellphone contract with a 3g (umts) and gprs flatrate and bought myself a Nokia E60 to be able to use it. Now to get the nokia to work as a modem for my laptop i had to install ............ NOTHING. 

Plug in the phone, it is recognized as a modem and assigned a device. run wvdialconf and it configures the modem for you. Go online to look for the init string to tell it to use my providers service and add the init string. 

If you're curious [http://series60.wordpress.com/2006/07/05/series-60-and-linux-playing-nice/](http://series60.wordpress.com/2006/07/05/series-60-and-linux-playing-nice/)

Now I run wvdial and i am online. Afterwards i configured gnome-ppp to use the same parameters as I get a nice icon on the panel with that. 

Now of course you still have a cable going between the mobile and the laptop. But wait, I have bluetooth on both. 

Looked up some stuff on bluetooth and phones : [http://www.ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth+passcode](http://www.ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth+passcode)

Changed the modem device in gnome-ppp to /dev/rfcomm0 et voila! 

I now have to make exactly 2 clicks to connect to the internet from anywhere (given mobile coverage). 

And all that without installing one piece of software. It all comes with the operating system. 

It feels great. If anyone wants to do something similar and needs help, don't hesitate to contact. 

Regards

rdd

---

### Post by mostwanted on 2006-08-14
That is really impressive. Wonder if this is caused mostly by Ubuntu or by Nokia using frinedly I/O for their phones...?

---

### Post by rdd on 2006-08-14
I think it is mostly Nokia. They have behaved really strangely for a technology company. They have stuck to some standards on all or at least most of their phones. You can use the same charger on all of them, for most of them the same USB-cables and this modem stuff works the same way for all of their GPRS-phones.

And although I didn't use to like Nokia phones because of the way the menu worked, etc. I have decided to go with them because of this and their commitment to Open Source. 

I have the feeling they could be one of the 'good' companies. By that I mean the ones that open source users can support by buying their stuff.

---

### Post by mostwanted on 2006-08-14
I always liked Nokia, their text messaging design is a lot more intuitive than my current Samsung.

---

### Post by rdd on 2006-08-14
And they're from Finland. That is a very fun country with very fun people. Enjoyed my stay there. Except the mosquitos in the north. 

Alright, Nokia wins. But I read somewhere that some Sony-Ericsson Phones can also be used as modems. It should work via bluetooth on most phones because the modem interface is standardized in the bluetooth stack. So Bluetooth should work for most makes. 

I was thinking about something really neat the other day though. My phone now has UMTS and WiFi. Wouldn't it be the bomb if it had something like a router mode, where it acts as an access point and routes to the UMTS connection? 

Although judging from the past few days I would guess that the battery wouldn't even last an hour with both those enabled.

---

