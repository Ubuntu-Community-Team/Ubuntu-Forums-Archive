---
title: "multipul sound card installation?"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by zzprop on 2009-11-02
ok so I got this yamaha multitrack sw1000xg midi audio sound card that will only work on windows and I use it with cakewalk pro audio9. (lotsa money invested in the two.)
I have ubuntu installed (and lovin it) next to windows in another partition  and there are no drivers to support the yamaha for linux.
now If I get a linux supported sound card and install it on the machine with the proper drivers and the yamaha with the windows drivers will it work if I want to do some audio midi work  can I go to windows and do my thing there with the yamaha card only and then when I want to use ubuntu just use the other card for audio playback for say Youtube and general audio stuff?.
I have a funny feeling it won't work but I am sure there is someone out there that can enlightin me.
I wish I could get away from windows entirely but I have to have my recording pc. This is a new machine and I would like to utilize both OS's with sound

thanks zz

---

### Post by GraysonPeddie on 2009-11-02
You can try it.

I have a motherboard with on-board sound chip and a Creative Labs X-Fi sound card. Both work at the same time with no hardware conflicts.

If I remember correctly, I saw in the SW1000XG website (discontinued and not available online) that it does not use hardware interrupts, so it should work.

Back during the days before Windows Vista (I don't have Windows XP, unfortunately), I think only consumer-level sound cards have hardware **interrupt request**s (IRQ). That includes the Crystal SoundFusion that I remember since it's built-in to the motherboard in an IBM Aptiva L/R series computer.

Oh, and by the way, read this:
[http://lalists.stanford.edu/lau/2006/01/1045.html](http://lalists.stanford.edu/lau/2006/01/1045.html)

---

### Post by AutoStatic on 2009-11-03
In Ubuntu it's no problem. I have 4 or 5 audio devices hooked up to my recording PC and no problems at all.
The Yamaha card will probably never work though in Ubuntu.

---

### Post by zzprop on 2009-11-03
> **GraysonPeddie said:**
> You can try it.

I have a motherboard with on-board sound chip and a Creative Labs X-Fi sound card. Both work at the same time with no hardware conflicts.

If I remember correctly, I saw in the SW1000XG website (discontinued and not available online) that it does not use hardware interrupts, so it should work.

Back during the days before Windows Vista (I don't have Windows XP, unfortunately), I think only consumer-level sound cards have hardware **interrupt request**s (IRQ). That includes the Crystal SoundFusion that I remember since it's built-in to the motherboard in an IBM Aptiva L/R series computer.

Oh, and by the way, read this:
[http://lalists.stanford.edu/lau/2006/01/1045.html](http://lalists.stanford.edu/lau/2006/01/1045.html)

GP
well I have had this card for I can't remember how long I think when I was running 98 paid close to 500 for it back then it's a great card and to set it up in xp was kinda a pain. I had to look for a while to find the driver to make it work and it wasn't just an install I had to do a copy paste .ini and some other stuff but it works. I am no programmer for sure I just keep stabbing at stuff until I make or break
I have an onboard audio nvidia and when I plug in a sound card it cuts the onboard off Maybe I need to look further into the mobo bios and see if i can force it to stay on.
so how do you choose between sound cards they don't all work at once do they?
I just like the ubuntu OS and if I can't get my xg to work I'll just have to stay with xp
and the stupid virus software.
by the way my mobo nvidia sound on the asus works great with ubuntu.

zz

---

### Post by zzprop on 2009-11-03
> **AutoStatic said:**
> In Ubuntu it's no problem. I have 4 or 5 audio devices hooked up to my recording PC and no problems at all.
The Yamaha card will probably never work though in Ubuntu.


Autostatic
Sorry I don't know how to multi quote yet I tried the button but it didn't work
How have you got your sound cards set up and what kind are they. 
Do you have to go to control panel and select?
Is there a good mixing and editing program out there for linux.
I have guitars,  key board, midi drums and love to record.

zz

---

### Post by AutoStatic on 2009-11-03
Hello zzprop, I have the following audio devices:
- Edirol UA-25 USB soundcard
- Korg nanoKONTROL MIDI controller
- Midiman Oxygen8 MIDI controller
- Focusrite Saffire Pro 10 IO Firewire soundcard
- Onboard HDA Intel soundcard

For the Focusrite I use [FFADO]("http://ffado.org/") together with JACK. All the other cards are set up with */etc/modprobe.d/alsa-base.conf*. In that file I've assigned specific index numbers to each device so they always get the same hardware ID. In Qjackctl I've set up different profiles for the different devices.
For audio production I only use JACK as a sound daemon so no control panels other than Qjackctl are involved. For editing I use Audacity. For mixing I use JACK-Rack with different plugins.

---

### Post by GraysonPeddie on 2009-11-04
> **zzprop said:**
> GP
well I have had this card for I can't remember how long I think when I was running 98 paid close to 500 for it back then it's a great card and to set it up in xp was kinda a pain. I had to look for a while to find the driver to make it work and it wasn't just an install I had to do a copy paste .ini and some other stuff but it works. I am no programmer for sure I just keep stabbing at stuff until I make or break
I have an onboard audio nvidia and when I plug in a sound card it cuts the onboard off Maybe I need to look further into the mobo bios and see if i can force it to stay on.
so how do you choose between sound cards they don't all work at once do they?
I just like the ubuntu OS and if I can't get my xg to work I'll just have to stay with xp
and the stupid virus software.
by the way my mobo nvidia sound on the asus works great with ubuntu.

zz

Well, you know what? Since you brang up Yamaha SW1000XG, that card really took me back to the old days before Yamaha discontinued Yamaha XG around -- *sigh* maybe 2003? Boy I had so much fun with Yamaha SY-XG softsynth and that I was glad that Yamaha provided support for Windows XP -- sometime around 2002 if memory serves. It started when I got Final Fantasy 7 sometime around 1997 (or is it 1998?) and it came with a combination of Yamaha SY-XG20 and Yamaha SY-XG50 called Yamaha SY-XG70. SW-XG50 sounded crap, but I don't know how it sounds like when SW1000XG is used to drive MIDI through that sound card when playing Final Fantasy VII. Gee-- I wish my parent could afford $500 for that sound card during my teenage days, but oh well...

I felt like posting this even though I went off-topic. I was a big fan of Yamaha XG until Yamaha discontinued it. Man, it's very sad but times are good those days. When I speak of teenage days, I'm going to be 27 years old on November 23rd.

It'd be nice if Yamaha could develop a Yamaha XG softsynth for Linux, but for me, it's time to move in.

---

### Post by AutoStatic on 2009-11-04
Maybe you could ask Rui Nuno Capela, the author of Qtractor. He's into Yamaha XG stuff too: [http://www.rncbc.org/drupal/node/151](http://www.rncbc.org/drupal/node/151)

---

### Post by mango42 on 2009-11-05
Slightly off topic as I'm only in the preparatory stages of considering Studio64 right now - need to get the hardware right first...

> **AutoStatic said:**
> ...
- Focusrite Saffire Pro 10 IO Firewire soundcard
...
For the Focusrite I use [FFADO]("http://ffado.org/") together with JACK.

What's your overall impression of the Saffire under Ubuntu Studio? Also is it self powered (I only have a 4pin Firewire socket)?

---

### Post by AutoStatic on 2009-11-05
Hello mango42, the Saffire is self-powered, afaik FFADO can not initialize the card when the power adapter is not attached.
I use the Saffire mainly in our rehearsal room and unfortunately we're not using Ubuntu there yet. When recording the band we haven't run into any problems so far. At home with Ubuntu I haven't had the need to stress the Saffire, but the recordings I did went really smooth. You need a good firewire card too, in the rehearsal room we use a Belkin card with a TI chipset and at home I use the card that came with the system (Agere), but I will swap that one with a Belkin too I think.

---

### Post by mango42 on 2009-11-06
Thanks for the info, AutoStatic - any relation to Eat Static? ;-)

---

### Post by AutoStatic on 2009-11-06
Nope :)

---

### Post by royleith on 2009-11-07
> **zzprop said:**
> ok so I got this yamaha multitrack sw1000xg midi audio sound card that will only work on windows and I use it with cakewalk pro audio9. (lotsa money invested in the two.)
I have ubuntu installed (and lovin it) next to windows in another partition  and there are no drivers to support the yamaha for linux.
now If I get a linux supported sound card and install it on the machine with the proper drivers and the yamaha with the windows drivers will it work if I want to do some audio midi work  can I go to windows and do my thing there with the yamaha card only and then when I want to use ubuntu just use the other card for audio playback for say Youtube and general audio stuff?.
thanks zz

I have an sw1000xg and a Sandblaster Live installed on the machine I am using to reply to your message. The Soundblaster (sorry for the cheap shot, it's not too bad) and its MIDI interface appear in both Windows and Ubuntu Studio, but no part of the Yamaha card appears in Studio. In installations with multiple Studio compatible sound cards one can select the card to use in jackctl settings. They are numbered 0, 1, 2 etc. As with Windows you can only use one card at a time, although all the MIDI interfaces should be available. I have been told that multiple Firewire devices from different manufacturers can be used at the same time. I am just about to give that a try. Let's see, that would be 24 ins and 8 outs. Oh, I haven't got that many mics and instruments.

Regards
Roy Leith

---

