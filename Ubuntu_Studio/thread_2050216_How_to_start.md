---
title: "How to start?"
date: 2012-08-30
forum: Ubuntu Studio
---

### Post by Heathrow on 2012-08-30
Firstly and mostly I`m sorry for my English - it is not my native language.
 
I`m currently going to buy a new pc and would like to start using Ubuntu Studio instead of Windows. My question is - since I got alesis io2 usb audio interface and digidesign midi keyboard (also on usb) and once I`ll download any compatible DAW what should I download next to get everything working with minimum latency? Wime asio drivers? If so - which version? What after that? I`d never worked with any linux based environments and I`m just afraid as while browsing the forum I can see more and more newbie`s struggling to get everything in line. I`m not asking about the specification and what to set in options - I can read, however there is a lot of software responsible for other things and I got lost a little bit. Any answers would be highly appreciated. One more - I`m going to record midi and audio tracks and then mix them togheter so if you can advise about any good linux format plugin bundles - that would also be something.
 
Hope I`m not wasting your time.
 
Mark.

---

### Post by jejeman on 2012-08-30
First see if your hardware is supported.
Download now ubuntustudio it is live dvd, and see if hardware works. After that we can talk about software.

Boot the live dvd, plug in everything you got, and issu this commands
```
lsusb

``````
aplay -l
```
```
amidi -l
```copy outputs here, and we'll tell you if you are good to go.

---

### Post by sgx on 2012-08-31
> **Heathrow said:**
> Firstly and mostly I`m sorry for my English - it is not my native language.
 
I`m currently going to buy a new pc and would like to start using Ubuntu Studio instead of Windows. My question is - since I got alesis io2 usb audio interface and digidesign midi keyboard (also on usb) and once I`ll download any compatible DAW what should I download next to get everything working with minimum latency? Wime asio drivers? If so - which version? What after that? I`d never worked with any linux based environments and I`m just afraid as while browsing the forum I can see more and more newbie`s struggling to get everything in line. I`m not asking about the specification and what to set in options - I can read, however there is a lot of software responsible for other things and I got lost a little bit. Any answers would be highly appreciated. One more - I`m going to record midi and audio tracks and then mix them togheter so if you can advise about any good linux format plugin bundles - that would also be something.
 
Hope I`m not wasting your time.
 
Mark.Pretty sure your Alesis will work. Look at links 4 and 8 at this wiki:

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

to see jackd, and qjackctl setup. Takes 20 or 30 hours over the
next few months, and you'll have a solid grasp of the nice
possibilities. Youtube videos abound, search for ardour, hydrogen, zynaddsubfx, rakarrack, ubuntu studio, and the many sidebar links.

calf, invada. and mda plugins bundles, and guitarix, all will help
the sound. rakarrack is a fine multi-fx app.

qtractor and ardour are the main native linux daw, and reaper inside wine, with wineasio, is the best all inclusive setup.

It's output can be just another instrument, in the linux arsenal. 

In qjackctl, the Periods/Buffer setting should be 3, for usb devices
like the alesis

Cheers

---

