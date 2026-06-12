---
title: "Ubuntu on dual GSM/Wifi mobile phone"
date: 2007-07-15
forum: The Cafe
---

### Post by Dafydd on 2007-07-15
Hi
Anyone have ideas at to the best dual mode GSM/Wifi mobile phone to buy, preferably running Ubuntu or Linux?

---

### Post by LodeRunner on 2007-07-15
> **Dafydd said:**
> Hi
Anyone have ideas at to the best dual mode GSM/Wifi mobile phone to buy, preferably running Ubuntu or Linux?

The [Neo1973]("http://en.wikipedia.org/wiki/Neo1973") has just been released, and it runs [OpenMoko]("http://en.wikipedia.org/wiki/Openmoko") Linux.  However, I would suggest that you try to wait a few more months--a much better, consumer-oriented version of the phone (including WiFi b/g, GPS, and 3d accelerometers) is due to be released in October.

The only other real contender (assuming you discount Motorola's recent JUIX phones, which aren't really recognizable or modifiable/customizable as Linux) is the [Greenphone]("http://en.wikipedia.org/wiki/Greenphone"), an overpriced, underfeatured, Qt-based phone  aimed at developers (as opposed to end users.)

Trust me... if you want a Linux phone, you're going to want the Neo1973. It's GTK+ based (meaning that you should be able to run many--though not all--of your favorite Ubuntu programs), and has some very impressive hardware under the hood (some sources give a whopping 256MB of RAM for the mass market version!)

And yes, it looks kinda like the iPhone, but it's aimed at an entirely different market entirely...

---

### Post by sublime on 2007-07-15
> **LodeRunner said:**
> The [Neo1973]("http://en.wikipedia.org/wiki/Neo1973") has just been released, and it runs [OpenMoko]("http://en.wikipedia.org/wiki/Openmoko") Linux.  However, I would suggest that you try to wait a few more months--a much better, consumer-oriented version of the phone (including WiFi b/g, GPS, and 3d accelerometers) is due to be released in October.

The only other real contender (assuming you discount Motorola's recent JUIX phones, which aren't really recognizable or modifiable/customizable as Linux) is the [Greenphone]("http://en.wikipedia.org/wiki/Greenphone"), an overpriced, underfeatured, Qt-based phone  aimed at developers (as opposed to end users.)

Trust me... if you want a Linux phone, you're going to want the Neo1973. It's GTK+ based (meaning that you should be able to run many--though not all--of your favorite Ubuntu programs), and has some very impressive hardware under the hood (some sources give a whopping 256MB of RAM for the mass market version!)

And yes, it looks kinda like the iPhone, but it's aimed at an entirely different market entirely...

Actually it's aimed pretty much directly at the iPhone.  The thing is that the Neo1973 was announced several months before the iPhone so initially it was meant to be its own project with no real goal in mind other than to create an opensource phone.  Everything else you said I agree with though but if the OP has experience in development and you want a new toy to play with the phone they just released and have started to sell is still very cool and with some very nice hardware including AGPS and the nicest touchscreen of any smartphone available.

---

### Post by Andrewie on 2007-07-15
> **LodeRunner said:**
> The [Neo1973]("http://en.wikipedia.org/wiki/Neo1973") has just been released, and it runs [OpenMoko]("http://en.wikipedia.org/wiki/Openmoko") Linux.  However, I would suggest that you try to wait a few more months--a much better, consumer-oriented version of the phone (including WiFi b/g, GPS, and 3d accelerometers) is due to be released in October.

The only other real contender (assuming you discount Motorola's recent JUIX phones, which aren't really recognizable or modifiable/customizable as Linux) is the [Greenphone]("http://en.wikipedia.org/wiki/Greenphone"), an overpriced, underfeatured, Qt-based phone  aimed at developers (as opposed to end users.)

Trust me... if you want a Linux phone, you're going to want the Neo1973. It's GTK+ based (meaning that you should be able to run many--though not all--of your favorite Ubuntu programs), and has some very impressive hardware under the hood (some sources give a whopping 256MB of RAM for the mass market version!)

And yes, it looks kinda like the iPhone, but it's aimed at an entirely different market entirely...

The phone really isn't gtk based, their going to have bindings for qt. Your current programs will not run on the phone, unless someone ports them.

not sure where the 256mb rumor came from but I haven't seen anything in the wiki

[www.openmoko.com](www.openmoko.com)
[www.openmoko.org](www.openmoko.org)

check those sites for more information

---

### Post by LodeRunner on 2007-07-15
> **Andrewie said:**
> Your current programs will not run on the phone, unless someone ports them. 

not sure where the 256mb rumor came from but I haven't seen anything in the wiki
[www.openmoko.com](www.openmoko.com) 

Well, a lot of the more popular programs have already been ported to the ARM architecture.  I've got a Sharpe Zaurus C1000 (a PDA) and after installing OpenZaurus/GPE (which is GTK+ based and, like OpenMoko, uses Matchbox) it runs Firefox, GAIM, Abiword, Gnumeric, etc.

As far as the 256MB rumor goes, I admit it is just a rumor at this point (since I can't seem to track down the source I had for it), but I believe that 128MB has been confirmed for the (developer-aimed) device currently released.  


> **sublime said:**
> Actually it's aimed pretty much directly at the iPhone.  The thing is that the Neo1973 was announced several months before the iPhone so initially it was meant to be its own project with no real goal in mind other than to create an opensource phone. 

Errr, didn't you just contradict yourself there?

Regardless of the designers' intentions, I confidently predict that this device is not going to be appealing to the vast majority of the iPod/iPhone crowd.  It's will not have Apple's polished UI (or Job's RDF, either), and it will not have the mass marketing blitz and media hype     to propel it into the mainstream. This will be a phone aimed at technical and semi-technical users (people who don't mind getting their hands at least a *little* dirty), who will in turn try to sell their friends and family on it.  Eventually--hopefully--OpenMoko will mature to a level comparable to Ubuntu and even computer novices will be able to fiddle and customize it with ease.

The iPhone presents you with a complete (and static) package. It's got the polish (and some actual features, e.g. the much-discussed "visual voicemail") that OpenMoko lacks, but it's proprietary and locked-down... it doesn't have the open-ended *potential* of OpenMoko.

Also, people should keep in mind that OpenMoko and the Neo1973 aren't the same thing--it's currently the only phone officially supported, but (in time) that will change.

---

### Post by sublime on 2007-07-15
> **LodeRunner said:**
> [QUOTE=Andrewie;3024488]Your current programs will not run on the phone, unless someone ports them.

not sure where the 256mb rumor came from but I haven't seen anything in the wiki
[www.openmoko.com](www.openmoko.com)

Well, a lot of the more popular programs have already been ported to the ARM architecture.  I've got a Sharpe Zaurus C1000 (a PDA) and after installing OpenZaurus/GPE (which is GTK+ based and, like OpenMoko, uses Matchbox) it runs Firefox, GAIM, Abiword, Gnumeric, etc.

As far as the 256MB rumor goes, I admit it is just a rumor at this point (since I can't seem to track down the source I had for it), but I believe that 128MB has been confirmed for the (developer-aimed) device currently released.  




Errr, didn't you just contradict yourself there?

Regardless of the designers' intentions, I confidently predict that this device is not going to be appealing to the vast majority of the iPod/iPhone crowd.  It's will not have Apple's polished UI (or Job's RDF, either), and it will not have the mass marketing blitz and media hype     to propel it into the mainstream. This will be a phone aimed at technical and semi-technical users (people who don't mind getting their hands at least a *little* dirty), who will in turn try to sell their friends and family on it.  Eventually--hopefully--OpenMoko will mature to a level comparable to Ubuntu and even computer novices will be able to fiddle and customize it with ease.

The iPhone presents you with a complete (and static) package. It's got the polish (and some actual features, e.g. the much-discussed "visual voicemail") that OpenMoko lacks, but it's proprietary and locked-down... it doesn't have the open-ended *potential* of OpenMoko.

Also, people should keep in mind that OpenMoko and the Neo1973 aren't the same thing--it's currently the only phone officially supported, but (in time) that will change.

What I meant was that the Neo wasn't intended to compete with anything, however, since the release of the iPhone the community has dirrected it's attention to competing with it.

---

### Post by LodeRunner on 2007-07-15
--dupe--

---

