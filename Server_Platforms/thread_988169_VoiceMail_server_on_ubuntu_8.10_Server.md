---
title: "VoiceMail server on ubuntu 8.10 Server"
date: 2008-11-20
forum: Server Platforms
---

### Post by newbuntuxx on 2008-11-20
Greetings,

I've been researching this for a few days now, and I didn't find a satisfactory answer. I found many how-tos, tried them and failed. So, I just want to ask a few basic questions here.

I have an ubuntu 8.10 server, with an old modem on it (connected to a PCI slot on the motherboard and not through a serial port). I am trying to install an answering machine software on my ubuntu server.

I want to be able to have my server answer the phone after say 3 rings and play a message followed by a beep, then record whatever the other end is saying. So, its really your classic answering machine device.

Now, during my research, I found a lot of talk about Mgetty and Vgetty (mind you i still dont know what the differene is except that Vgetty is a package of Mgetty!?). 

I did try to install them, but, in the config files, i am asked for the port the modem is connected to. The default is the serial port, but i dont have a serial modem.

So, if anyone can provide me with a set of instructions to do this for a PCI modem, or direct me to a how-to, that would really be appreciated.

---

### Post by newbuntuxx on 2008-11-20
I forgot to mention that I did come acrss Asterisk server. But, it looks ilke its an operating system on its on! You can not install it as an application on your ubuntu server. It does, however, provide amazing features.

[http://www.voip-info.org/wiki/view/Asterisk%40home+Handbook+Wiki](http://www.voip-info.org/wiki/view/Asterisk%40home+Handbook+Wiki)

---

### Post by newbuntuxx on 2008-11-21
bump!

---

### Post by volkswagner on 2008-11-21
> **newbuntuxx said:**
> I forgot to mention that I did come acrss Asterisk server. But, it looks ilke its an operating system on its on! You can not install it as an application on your ubuntu server. It does, however, provide amazing features.

Asterisk is in the repository.  It is an application.

---

### Post by bgsneeze on 2008-11-27
As I under stand it, modems will not work the way you want. Modems are for data transfer, you want to have a ATA, or analog telephone adapter. Linksys and many other companies make these. If you install Asterisk and configure it you can then make a very flexable voicemail system.

---

### Post by Fish_Kungfu on 2009-01-18
You need something like this:

[http://www.telephonydepot.com/Catalog/Linksys-Analog-Adapters](http://www.telephonydepot.com/Catalog/Linksys-Analog-Adapters)

---

### Post by volkswagner on 2009-01-18
I know this is an old thread.  I am still curious about this myself.

Shouldn't a voice/fax hardware modem be enough?

Many years ago, I used a freeware app in windows '98.  It did just what the OP wants.  It would even email, or forward a prerecorded message to another phone number, indicating a new voicemail has arrived.

Is this a limitation of Linux Kernel, or a matter of no program yet exists.

Reading about Asterisk, I see a special modem is required.  Pricing seems to be like a hundred bucks or more for these spec'd modems.

---

### Post by cariboo on 2009-01-18
I got software with a modem years ago that added an answering machine, it was probably for Win95, I did use it for a while, but a dedicated answering machine was a lot easier to setup. There is answering machine software in the repositories called mgetty-voice, I haven't tried it so I can't recommend it.

Jim

---

### Post by megacrypto on 2009-02-02
I was wondering the same thing myself. i remember that such an app existed on windows using the normal modem.

---

### Post by Elludium_Q-36 on 2009-04-30
Not that I'm an authority, but I posted some related info here:

[http://ubuntuforums.org/showthread.php?t=1003467#post7132174](http://ubuntuforums.org/showthread.php?t=1003467#post7132174)

First of all, it needs to be a voice modem or data/fax/voice modem.
a data modem (MOdulator/DEModulator) changes digital data into an AF (audio frequency), audible means of sending that data.  

Read me:
[http://en.m.wikipedia.org/wiki/modem#Voice_modem](http://en.m.wikipedia.org/wiki/modem#Voice_modem)

Imagine a man in the old west sending a message at the Western Union office.  He'd talk to the clerk who'd write down the message and modulate the keyer to send morse code over the line and it was demodulated at the other end, so to speak.  If you asked to talk to the person at the other end you might spend a night in the Sheriff's jail next to the town drunk. 

We know that Alexander Graham Bell received the patent that used the same wires to send voice.

Now in the early days of Local Area Networks, sending voice over data lines was unimaginable for most but now, the same ethernet wires carry VoIP.

Point is that you need the right hardware and software.  A data or data/fax modem usually won't "cut the mustard" even for package pstngw.

* pstngw
* H.323 to PSTN gateway
* Very simple PSTN (normal telephone) to H.323 gateway program using
* the OpenH323 library. It allows H.323 clients to make outgoing calls,
* and incoming calls to be routed to a specific H.323 client. It needs
* special hardware to do this.
i.e. a data/fax/voice modem.  There are even data/fax/voice/speaker-phone modems...

It should be a quality voice modem.  Wikipedia says:
"Because voice mode is not the prototypical use for a modem, many modems on the market have poor or buggy support for their voice modes."
Read on:
[http://en.m.wikipedia.org/wiki/Voice_Modem](http://en.m.wikipedia.org/wiki/Voice_Modem)


NOW*****

The phone jack on your wall will supply power, ring voltage and signal to an Analog phone and can be thought of exactly like an ATA jack on an Analog Telephone Adapter.  In PBX (Private Branch eXchange)/asterisk parlance, the wall jack is the same as an FXS or Foreign eXchange Subscriber where the telephone company Office is considered Foreign eXchange and you or your Analog telephone or modem are the Subscriber or subscriber device. Your telephone is plugging into the jack that gives it the Subscriber service.  In other words, the FXS jack PROVIDES the service to your phone or modem.

In PBX/Asterisk terms, the FXO (Foreign eXchange Office) jacks are for RECEIVING the service from the "Foreign" Office's eXchange and you can feed that to your Private Branch eXchange if you like.  In most low-tech households, the jack on the back or bottom of the telephone is the only FXO jack and RECEIVES the supply power, ring voltage and telephony signal from the telco Office; POTS (Plain Old Telephone Service).

Now if you are keen on KIAX/IAX or some other H.323/SIP/VoIP client, there's no reason for an ATA/FXS jack to supply ring power and run an Analog phone but for grandma, the kids or a home office setting for the technologically impaired...  
UNLESS YOU NEED TO ANSWER ON AN OLD SCHOOL PHONE OR TRANSFER TO CALLS TO SOMEONE WHO NEEDS TO USE AN ANALOG PHONE, YOU DON'T NEED AN ATA OR FXS JACK!!!  Headphones to a sound card and an SIP/Voip or even WiFi phone take the place of an Analog phone for those in the know.

An asterisk type server can answer a PSTN (public switched telephone network/POTS) line from anywhere in the world and route the call anywhere in the world, it receives the call in the voice modem's FXO jack.  If you want to send that call to an analog phone, tape answering machine or what not, that's when you need an ATA or FXS jack so the Analog phone behaves like it's plugged into the FXS on the wall...

That's a mandatory primer for those who were unsure.  People mix up FXS, FXO and use them interchangeably on the net but they are NOT interchangeable connections!

I had answering machine programs from Bill Gates' boxes, then I got a little wiser and  *nixed no-win-dos...

* If you have an SIP/VoIP/H.323 client, package pstngw is an H.323 to PSTN gateway,

* openam is an answering machine for H.323/SIP/VoIP.

* isdnvbox is an ISDN answering machine.

Search adept or synaptic for mgetty and vgetty for related packages but mgetty-voice is the pertinent one to your query.  You still need a voice modem, not just what the computer vendor or last owner jammed in the PCI slot.  

Experienced advice:  If you wind up with a conexant modem, plan on pulling out the credit card for linuxant.com to get linux drivers.


There's Yate which is a budding telephony engine.  Bayonne has some promise but Asterisk seems to be the most developed, supported and documented.  Asterisk has answering machine functionality and much more...

[http://ubuntuforums.org/showthread.php?t=1003467#post7132174](http://ubuntuforums.org/showthread.php?t=1003467#post7132174)

---

