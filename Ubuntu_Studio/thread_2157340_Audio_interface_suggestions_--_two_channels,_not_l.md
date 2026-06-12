---
title: "Audio interface suggestions -- two channels, not looking for anything high end"
date: 2013-06-25
forum: Ubuntu Studio
---

### Post by rorschachwalter on 2013-06-25
I'm looking for a sub-$100 USB interface that will work with Linux OOTB. Main purpose is to record podcasts, but I might use it to do some hobby recording at some point. So nothing fancy -- just something that works and will give better sound quality than a laptop mic.

Any suggestions?

---

### Post by jejeman on 2013-06-25
Do you have mic or line input on that laptop?

---

### Post by rorschachwalter on 2013-06-25
There is a mic input on the laptop. But I'm not sure that would be sufficient for connecting something like a Shure mic to it without something in the middle to boost the signal.

---

### Post by gordintoronto on 2013-06-25
Just plugging in the mic is worth a try. I'm no fan of any form of USB audio.

The noise from the laptop itself will degrade the audio quality.

---

### Post by rorschachwalter on 2013-06-26
So maybe I'll buy a 1/4" to 1/8" adapter and give that a shot.

Could someone who understands digital recording better than I do tell me whether it would be better to use a cheap practice amp as a preamp feeding into the computer, or to plug the mic directly into the laptop? The mic is a fairly cheap Shure dynamic mic.

---

### Post by jejeman on 2013-06-26
Maybe this is for your podcast recording
[http://www.behringer.com/EN/Products/302USB.aspx](http://www.behringer.com/EN/Products/302USB.aspx)

---

### Post by cub on 2013-06-27
> **rorschachwalter said:**
> So maybe I'll buy a 1/4" to 1/8" adapter and give that a shot.

Could someone who understands digital recording better than I do tell me whether it would be better to use a cheap practice amp as a preamp feeding into the computer, or to plug the mic directly into the laptop? The mic is a fairly cheap Shure dynamic mic.
Me on the other hand would recommend not to use the direct line in or mic on the computer but to use an USB audio card for better sound quality. So I suppose it depends on who you ask. :D

Anyhow, what kind of practice amp are you talking about? Usually using like a guitar amp as a preamp for voice will not produce a great result. Which Shure model is it?

---

### Post by rorschachwalter on 2013-06-27
> **cub said:**
> Me on the other hand would recommend not to use the direct line in or mic on the computer but to use an USB audio card for better sound quality. So I suppose it depends on who you ask. :D

Anyhow, what kind of practice amp are you talking about? Usually using like a guitar amp as a preamp for voice will not produce a great result. Which Shure model is it?

I was thinking the same thing, but since I have limited knowledge of this stuff, I started wondering if people telling me to just use the mic input meant I was mistaken.

The practice amp would be probably a Squire practice amp from maybe 15 years ago. The Shure is a 14A dynamic -- nothing terribly fancy, but works for live performances.

---

### Post by David Bolton on 2013-06-30
Will a USB preamp be better than the internal sound card? Obviously it depends on the quality of the sound card in your computer (and the quality of the preamp). Unless you specifically selected an excellent sound card when you purchased the computer, or installed one yourself, chances are almost any USB preamp will do a better job. In my experience, if you connect a professional mic directly into the 8th inch jack of a consumer-grade soundcard then the volume will be very quiet and you'll get a lot of noise (hissing in the background). In other words, it works, but the sound quality is usually poor.

---

### Post by gordintoronto on 2013-06-30
Interesting. I have a cheap Chinese mic plugged into my motherboard, and I'm completely satisfied with it for voice recording. Well, not totally cheap: I found it online for $18 including shipping. It's a Salar M8, which my wife bought in China.

---

### Post by zeebe on 2013-07-04
Hi!
The post is 1 week old, but maybe it'll help anyway.
Since integrated souncards have a poor performance which will certainly bother you sooner or later (latency and quality issues), i recommend you to buy an Audio Interface. Using the integrated soundcard with a cheap microfone may be suitable for podcasts, but definitely not for any kind of "serious" audio production. 
There are many good options (normally, all class-compliant interfaces should work). 
A friend uses the old Tascam US-144, the newer US-122 should work with Linux too ([https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)). There are several out on ebay, with some luck you may get one below 60,-.

---

### Post by zeebe on 2013-07-04
> **rorschachwalter said:**
> So maybe I'll buy a 1/4" to 1/8" adapter and give that a shot.

Could someone who understands digital recording better than I do tell me whether it would be better to use a cheap practice amp as a preamp feeding into the computer, or to plug the mic directly into the laptop? The mic is a fairly cheap Shure dynamic mic.

The Shure mic probably has a XLR-jack, which is based on a synchronous signal and can not be connected to a laptop plug. So you'd need a DI Box, or better, an Audio Interface with a preamp (which is usually included).

---

### Post by leokn@yahoo.com on 2013-07-06
I'm running Ubuntu Studio 13.04 64 bit, which is already set up for low latency, ideal for recording! I use programs like Gimp, Darktable and Shotwell for my phot needs. (Also comes standard with Ubu-Studio pkg).
OpenShot video editor for sticking bits of videos together and uploading the result to YouTube (I found that upgrading my inet connection to 20/5 decreased my upload times immensely).
Ardour 3, Hydrogen, and a slew of more programs come standard for audio stuff.
Last, but not least, after trying many different recording methods, I bought for @ $150 a "Audiobox USB" for my interface. I had a learning curve initially to learn how to set up Jack, but it was way worth the effort. My rig works like a charm!
You might, if not already have done so, join the forum [http://linuxmusicians.com/](http://linuxmusicians.com/)
Those people are an awesome resource of knowledge!!

---

