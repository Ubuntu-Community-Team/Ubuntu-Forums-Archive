---
title: "Audio Interface Set-up"
date: 2013-03-22
forum: Ubuntu Studio
---

### Post by Harmelodic on 2013-03-22
First off, I'm completely new to this so please have patience.

I wish to setup a home recording studio capable of recording vocals, guitars, piano and so on. What I would like to know is; What are some good ( i.e. best "bang for buck") audio interfaces that are compatible with what is running on my PC, and also what what kind of set-up would be most efficient? (i.e. mixer/soundcard or AI/soundcard etc. etc.)

Currently running/obtained:
[COLOR=#000000]
[LIST]
[*]Ubuntu Studio 12.04
[*]Ardour as a DAW
[*]Condenser Mic (Phantom Power needed) (XLR)
[*]Instruments (w/ leads etc.)
[/LIST]

Thanks,
Harmelodic
[/COLOR]

---

### Post by jejeman on 2013-03-22
There are no best soundcards. It all depends what you need (how many inputs) and how much you want to spend.
I use Edirol FA-66 capture device. It is supported, it has phantom power and enough inputs for my use.
I don't think you need a mixer or you should know if you need it. ;)

It is better if you list soundcards you think are for you, and we can comment on them. We don't know what cards are available for you to purchase.
Also you need a pair of monitors, but again, it all depends what you do.

---

### Post by tgalati4 on 2013-03-22
M-Audio Delta66 card with Omni breakout box.  24-bit, 96kHz recording, analog and digital, quiet preamps.

---

### Post by zequence on 2013-04-04
Check out this page for some nice info on devices [http://wiki.linuxmusicians.com/doku.php?id=hardware_matrix](http://wiki.linuxmusicians.com/doku.php?id=hardware_matrix)

---

### Post by Keiner298 on 2013-04-10
1st, You have to look if the card you have in focus, is supported by alsa, because the alsa drivers are the most used drivers for soundcards, including USB devices. And the alsa drivers are included in most of the distributions like e.g. Ubuntu Studio

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main).

I am going to buy the "Native Instruments komplete Audio 6"(USB device). The Focusride scarlett i4 works also.
good luck

---

### Post by jeff jordan on 2013-04-18
As all the others answered: It depends on what you're planning to do  with your system, especially how many independent channels you need and  if these channels needs to be balanced (symmetric) or unbalanced  (asymmetric). 
After figuring out what you need, look fore some audio  interfaces that fit the needs. Then check them against the  compatibility lists mentioned in the postings above.

I just  started with an M-Audio 1010LT, which provides 8 analog inputs and is  supported...  but has all its inputs unbalanced. That's fine if you have  a simple instrumental setup, but if you're messing around with  monitors, amps, (stand-alone) mixers, effects and PC, you're running  sooner or later into problems with severe ground loops, that provide a  decent humming or other interferences (provided by switching power  supplies, monitors, the PC itself and so on). So for our  monday-"jamming" we needed a device with at least 8 analog and balanced  inputs (which can be used simultaneously !!!), while 2 of them should  provide phantom power for the mics.

So after looking for an  adequate interface for use at our jamming attempts, we came across the  Edirol FA101, which we were able to buy through eB@y for a reasonable  price.

Now, last weekend, we just set up a little recording unit  with ubuntu studio in combination with the Edirol (brand by Roland)  firewire interface. 
It's just awesome, with 2 mics, 2 guitars  (stereo) 1 bass (stereo) we can now record everything simultaneously  (including hydrogen as drum machine) with ardour as single tracks, even  with additional effects like chorus or echo, in best quality (102db S/N)  without messing around with ground loops and other interferences.

---

