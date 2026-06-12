---
title: "2 things to kill linux"
date: 2008-02-14
forum: The Cafe
---

### Post by Circus-Killer on 2008-02-14
okay, here are two things that i feel have the potential to kill off linux in the future.

the first one is exotic hardware and services. it took so long to get wireless  cards working in ubuntu, and even current solutions aren't the best ones. a better example could even be my 3G modem. its a vodafone branded huawei e220. it works well in ubuntu, but not that well. first of all, i needed an internet connection to get the software needed to install the vodafone mobile connect driver for linux. bit hard to download if my only source for internet is what requires the downloading. so it was a bit of a bother that i had to go to another pc and download the dependencies. furthermore, the vodafone connect driver for linux is community developed, so this means that if it stops getting maintained by the current developers, it can really all go downhill.

this is in contrast with windows, where not only does the modem automatically install software when you plug it in (stored in its own flash memory), but that you know the software will keep working for a long time to come, and that vodafone will keep updating their software as needed. but the fact that you dont have to download and install software just to get your modem working is a big plus on the windows side. and even then, the vodafone mobile connect driver for linux is less-than-stable.

and as time marches on, so more and more exotic hardware comes out, and tend to rely more on software than the previous generation. whilst i can currently use my 3G modem from linux, how long till the necessary packages stop getting maintained?

the second thing to kill linux is this move to having software not stored on the pc. microsoft are planning that their next version of office not be stored on the users machine, but rather on a server that is accessed over the internet. this could be both good or bad, depending on how its done, and how linux in general react to this change in paradigm. personally, i dont like the idea. i like having my software locally, so if i need to do some word processing or whatever whilst my internet connection is down, i still can.

the second one isnt too much of a worry, but i think the first one is. if linux cannot keep up with technology, then we will face a most certain doom. what developers in the open source world need to start doing, is stop letting ms telling us where technology should go, and play catch up. rather we should be creating the technology first, and let ms play catch up, thereby forcing them to stick to our standards, instead of us tryna "fit in" with their standards, which makes no room for us.

just a few thoughts, like to here your thoughts.

---

### Post by DoctorMO on 2008-02-14
> this is in contrast with windows, where not only does the modem automatically install software when you plug it in (stored in its own flash memory), but that you know the software will keep working for a long time to come, and that vodafone will keep updating their software as needed. but the fact that you dont have to download and install software just to get your modem working is a big plus on the windows side. and even then, the vodafone mobile connect driver for linux is less-than-stable.

The hardware support from vendors is quite important, I'm on kernel mailing lists so I can see big named firms working on driver support. What you fail to understand is that just because it's linux doesn't mean that your hardware company isn't working on the drivers. As time marches on and linux gains further ground in desktop mindshare, mobile platforms etc we'll only see more of this kind of involvement.

As for installing software when you plug the device in, Ewww, do you understand how horribly unsecured that is? How in the world are they signing their packages? is the operating system supposed to run any jolly thing plugged into the usb port? Providing software on a mem chip is one thing, installing it by default is a gross security flaw.

> the second thing to kill linux is this move to having software not stored on the pc. microsoft are planning that their next version of office not be stored on the users machine, but rather on a server that is accessed over the internet. this could be both good or bad, depending on how its done, and how linux in general react to this change in paradigm. personally, i dont like the idea. i like having my software locally, so if i need to do some word processing or whatever whilst my internet connection is down, i still can.

A lot of it is hype, it's true that applications will move online, but one thing the internet isn't really very good at is latency. low latency applications are still in demand. even web applications port back to the desktop for this feature, just look at Miro.

---

### Post by angryfirelord on 2008-02-14
> 
the first one is exotic hardware and services. it took so long to get wireless cards working in ubuntu, and even current solutions aren't the best ones. a better example could even be my 3G modem. its a vodafone branded huawei e220. it works well in ubuntu, but not that well. first of all, i needed an internet connection to get the software needed to install the vodafone mobile connect driver for linux. bit hard to download if my only source for internet is what requires the downloading. so it was a bit of a bother that i had to go to another pc and download the dependencies. furthermore, the vodafone connect driver for linux is community developed, so this means that if it stops getting maintained by the current developers, it can really all go downhill.

this is in contrast with windows, where not only does the modem automatically install software when you plug it in (stored in its own flash memory), but that you know the software will keep working for a long time to come, and that vodafone will keep updating their software as needed. but the fact that you dont have to download and install software just to get your modem working is a big plus on the windows side. and even then, the vodafone mobile connect driver for linux is less-than-stable.
So ask yourself something: Is this really a fault of Linux? If the manufacturer is only willing to provide decent drivers for Windows, then someone (or a group of people) have to show that there is demand for this hardware on a linux platform.
> and as time marches on, so more and more exotic hardware comes out, and tend to rely more on software than the previous generation. whilst i can currently use my 3G modem from linux, how long till the necessary packages stop getting maintained?
Depends on who's maintaining it. If it's by the manufacturer, then yes, support may end. However, if it's being maintained with the open-source community or by an open-source driver, then support for that hardware will be around for a long time. (Another reason why drivers should be open-sourced)
> the second thing to kill linux is this move to having software not stored on the pc. microsoft are planning that their next version of office not be stored on the users machine, but rather on a server that is accessed over the internet. this could be both good or bad, depending on how its done, and how linux in general react to this change in paradigm. personally, i dont like the idea. i like having my software locally, so if i need to do some word processing or whatever whilst my internet connection is down, i still can.
Heh, have you tried using the current online version of office? It sucks to tell you the truth and Microsoft has always been slow to the internet thing. Unless everyone adopts their proprietary protocol, I don't see that much of a threat. Google Docs will probably be the thing to use.
> the second one isnt too much of a worry, but i think the first one is. if linux cannot keep up with technology, then we will face a most certain doom. what developers in the open source world need to start doing, is stop letting ms telling us where technology should go, and play catch up. rather we should be creating the technology first, and let ms play catch up, thereby forcing them to stick to our standards, instead of us tryna "fit in" with their standards, which makes no room for us.
Oh, but we are setting our own path! It's just that when 90% or less of the desktop market is Windows, you do have to provide some sort of transition for them Otherwise, the linux project has been going on at a steady pace even without Microsoft's interference. It's Microsoft that should be worried, not us.

---

### Post by Trail on 2008-02-14
> how long till the necessary packages stop getting maintained?

Likely the opposite. Packages are getting maintained all this time voluntarily. Microsoft(tm) does whatever it does for money. Think of Windows(tm) XP Service Pack2. After installing it, you have 30 days to activate it online, else it locks you out. Now imagine 10 years from now where Microsoft(tm) decides to drop XP support for the cool Vista2020. Guess what, the 20 year old trusty usb stick you have cannot be installed on vista2020 because the software in its flash memory is for xp. And you cannot activate Xp. Pity.

Besides, Vista(tm) has worse hardware support than Linux, so there, you got your comparison.

---

### Post by tageiru on 2008-02-14
> **Circus-Killer said:**
> 
this is in contrast with windows, where not only does the modem automatically install software when you plug it in (stored in its own flash memory), but that you know the software will keep working for a long time to come, and that vodafone will keep updating their software as needed. but the fact that you dont have to download and install software just to get your modem working is a big plus on the windows side. and even then, the vodafone mobile connect driver for linux is less-than-stable.
Yeah, unless you use Vista. The pain I went through trying to get that POS to work on Windows Vista was intolerable. The driver-from-flash didn't work and needed bizarre hacks to get around, I had to upgrade the firmware...

I actually gave up in the end.

---

### Post by SZF2001 on 2008-02-14
These are two completely different operating systems with two different goals. We shouldn't be looking into their goals for our trouble.

---

### Post by tigerpants on 2008-02-14
Nothing can kill linux, not Microsoft, not even Linus Torvalds. It grows and evolves constantly. 

It has the backing of IBM and Google and other IT heavyweights. Have you seen Android for example?

Linux isnt going away in my lifetime, thats for sure. I'd more worried if I was a Microsoft employee.

---

### Post by tombott on 2008-02-14
What a load of rubbish.
If anything Linux is becoming more and more mainstream by the day.

And it's not that hard to plug your laptop into a network and download the drivers is it?

Try re-installing a modern laptop with windows XP SP2, I did for a client 2 days ago.

LAN didn't work
WAN didn't work
Graphics restritced to 1024*768
Bluetooth didn't work
PCMCIA card reader didn't work

---

### Post by aysiu on 2008-02-14
1. Don't buy exotic hardware.

2. The more people move to web-based applications, the better for Linux. Both Everex's gOS and the Xandrofied Eee PC rely heavily on web-based applications.

---

### Post by aimran on 2008-02-14
Recurring discussion?

---

### Post by FuturePilot on 2008-02-14
The way I see it is kind of the opposite. The more popular Linux becomes, the more hardware manufacturers will start supporting it.
As for web based applications, I don't like that idea. First I would like to be able to do work if my internet connection happens to go down (and with my current ISP that seems to be pretty often :roll: ) Second of all web based applications tend to be slow.

---

### Post by SomeGuyDude on 2008-02-14
People need to stop saying "it's not Linux's fault!" It's mostly accurate but doesn't change the fact that it's a HUGE problem facing Linux users. 

While it's not directly Linux/Canonical/whoever's fault that hardware vendors do not often make drivers for Linux users, the fact is that unless they start to do so, there will be no solution. So can Linux devs just sit around waiting for hardware producers to come around?

NO. An effort must be made via some kind of discussions/meetings/whatever to pressure hardware companies to start catering to Linux users. Without any reason to do so, why will they? These companies need to be convinced that there is a market for Linux users (which there certainly is).

---

### Post by SomeGuyDude on 2008-02-14
> **FuturePilot said:**
> The way I see it is kind of the opposite. The more popular Linux becomes, the more hardware manufacturers will start supporting it.
As for web based applications, I don't like that idea. First I would like to be able to do work if my internet connection happens to go down (and with my current ISP that seems to be pretty often :roll: ) Second of all web based applications tend to be slow.

Hah, I remember when Google announced the idea of the internet-based OS complete with a drive situated online. Because, obviously, what the people want is the inability to use their computer at all when there's a storm and the internet goes out.

---

### Post by 23meg on 2008-02-14
[QUOTE=SomeGuyDude]People need to stop saying "it's not Linux's fault!" It's mostly accurate but doesn't change the fact that it's a HUGE problem facing Linux users.[/QUOTE]

It also doesn't mean nothing is being done about the problem, and that people are just sitting down and waiting for manufacturers to come around. It's just a typical half-informed defensive reflex.

---

### Post by SomeGuyDude on 2008-02-14
> **23meg said:**
> It also doesn't mean nothing is being done about the problem, and that people are just sitting down and waiting for manufacturers to come around. It's just a typical half-informed defensive reflex.

Good point, good point. I just get tired of hearing it.

---

### Post by rune0077 on 2008-02-14
> **tigerpants said:**
> 
Linux isnt going away in my lifetime, thats for sure. I'd more worried if I was a Microsoft employee.

Market surveys and the numder-of-millionaires-per-100-employees suggest you'd have nothing at all to worry about if you were a Microsoft employee.

---

### Post by dca on 2008-02-14
If SCO couldn't do it....  and that wasn't even 2 things...

---

### Post by original_jamingrit on 2008-02-14
To the OP's two killers (these are my opinions and not really backed up by real evidence, but just what I've heard.)

1.Hardware; The western economy is slowly starting to fall into a recession.  It would be much more affordable to have a homogeneous hardware market, with less exotic hardware.

2. Centralized server apps are becoming something that may happen in the future.  In which case, there are already open source services that are also building that technology.  See [http://eyeos.org/](http://eyeos.org/).  
In which case, Linux and other open source software will certainly still serve a purpose for you personal computer, especially if you are a person or business that prefers not to use web apps for day to day work, or create your own local web app server, or even centralized servers with thin clients.

Although, I've heard people express great fears that in the future, everything will be run on several big servers owned by a few rich people, and the rest of us will have nothing but thin clients in our homes.

---

### Post by Vitamin-Carrot on 2008-02-14
All I can Say is

AND?

---

### Post by karellen on 2008-02-14
3 days ago I bought a Kingston usb stick with ReadyBoost (supposedly designed with Vista in mind or so). guess what was written on its compatibility table:
Windows Vista
Windows 200/XP
Mac OS (10.x and above)
Linux (2.4 and above)
so you see...for me it seems that hardware support gets better and better

---

### Post by %hMa@?b&lt;C on 2008-02-14
> **karellen said:**
> 3 days ago I bought a Kingston usb stick with ReadyBoost (supposedly designed with Vista in mind or so). guess what was written on its compatibility table:
Windows Vista
Windows 200/XP
Mac OS (10.x and above)
Linux (2.4 and above)
so you see...for me it seems that hardware support gets better and better

props to kingston.
I got a Kingston SD card reader for Xmas and it came with the following table

MobiLite System Requirements
Systems with USB support
Windows Vista (tm) (readyboost (tm) not supported)
Windows 2000 SP3 or XP SP1
Mac (10.x and above)
Linux (2.4 and above)

even though it is on the bottom, its still on the table :P

---

### Post by karellen on 2008-02-14
> **jeffc313 said:**
> props to kingston.
I got a Kingston SD card reader for Xmas and it came with the following table

MobiLite System Requirements
Systems with USB support
Windows Vista (tm) (readyboost (tm) not supported)
Windows 2000 SP3 or XP SP1
Mac (10.x and above)
Linux (2.4 and above)

even though it is on the bottom, its still on the table :P

:) nice. they've gained me

---

### Post by phaed on 2008-02-14
Even Vista is having compatibility issues.  I read an article the other day where a guy switched back to XP because he couldn't get his printer to work.

As the number of gadgets that we expect our computer to interact with increases exponentially, this will be a mounting issue for all operating systems.

I just wish I could use my iPhone to work on Linux.  Right now the only thing I can do is extract pictures.

---

### Post by rune0077 on 2008-02-14
> **phaed said:**
> 
I just wish I could use my iPhone to work on Linux.  Right now the only thing I can do is extract pictures.

If you have wireless, use Amarok: I got it to transfer music to my iPhone without a hitch.

---

