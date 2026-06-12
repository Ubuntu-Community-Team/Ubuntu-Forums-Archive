---
title: "Biiiiig Jack Problem"
date: 2011-12-01
forum: Ubuntu Studio
---

### Post by UbunLeo on 2011-12-01
Hello mates,
I am a new Ubuntu Studio User and because of this i have some problems setting up my Software. I am a musician so i wanted to turn up my netbook into a studio platform. I installed Ubuntu Studio 11.10 and then i tried to make some noise, but i failed. I have an M Audio USB Midi Controller which i cant use with ubuntu, but i can see it when i plug it in. But i think that my big problem comes from Jack where i recieve too much errors an i dont know why. I post a screenshot to show you my situation.
Sorry for any language mistakes, i am a lower user of english! :)

[IMG]http://a7.sphotos.ak.fbcdn.net/hphotos-ak-ash4/374137_281882965181057_215707121798642_696814_382704921_n.jpg[/IMG]

---

### Post by beefheartvliet on 2011-12-01
You are getting a lot of X-Runs. Try setting up Jack from this guide. 

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

Hope this Helps. I'm not an expert, but will try and help if I can.

---

### Post by UbunLeo on 2011-12-01
Thanks.. But It didn't work... Same as usual!

[IMG]http://a6.sphotos.ak.fbcdn.net/hphotos-ak-snc7/374778_281967275172626_215707121798642_697081_1413405677_n.jpg[/IMG]

---

### Post by Sylos on 2011-12-05
Hello.

You mentioned in you OP that you are setting up a netbook for this. Can you provide details of your specs. Maybe the HW is struggling with things (in my understanding netbooks usually have pretty limited specs). Maybe increasing the latency in jack settings might slow down the Xrun fever.

Cheers

---

### Post by sgx on 2011-12-06
> **UbunLeo said:**
> Thanks.. But It didn't work... Same as usual!


in qjackctl, Periods/Buffer should be 3  for usb devices.

Install a2jmidid and after starting qjackctl, use the command

a2jmidid -j default

It will place a midi connector in the middle tab of the connections panel in qjackctl. In the alsa tab, if there are midi-thru ports, connect them to the midi interface, both in and out.  in-X-out

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)  has a2jmidid

Bodhi linux is ubuntu based, but less than 400 meg .iso, and may be better to use on a netbook

---

