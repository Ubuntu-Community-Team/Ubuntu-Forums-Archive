---
title: "M-Audio MobilePre &amp; Jack1 = bus error HELP!"
date: 2010-02-10
forum: Ubuntu Studio
---

### Post by zenon222 on 2010-02-10
Is it possible to use an M-Audio MobilePre with JACK1 or JACK2 ?

I have searched and have not found any success.  I am willing to be a JACK2 guinea pig if that's what it takes.


```
root@zenon-ubuntu:/home/zenon# jackd -s -R -P 70 -dalsa -dhw:0 -p1024 -r48000 -n2 -X seq
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
Bus error
root@zenon-ubuntu:/home/zenon# 

```I just noticed "32bit" in the output, this card is 16/48k could that be an issue?

MobilePre: [http://www.m-audio.com/products/en_us/MobilePreUSB.html](http://www.m-audio.com/products/en_us/MobilePreUSB.html)

---

### Post by AutoStatic on 2010-02-10
Hello zenon222,

From the manual:
> Class-compliancy on Windows XP & Mac OS X (10.2.6 & higher) systems
So it should work out of the box.
Could you post the outcome of **aplay -l** with the device attached?
And your nick, has it anything to do with the protagonist of [L'Œuvre au Noir]("http://en.wikipedia.org/wiki/L%27%C5%92uvre_au_noir")? Just curious :)

---

### Post by zenon222 on 2010-02-10
The card works beautifully and out of the box with typical ALSA + Gstreamer.  It is only JACKd that causes issues.  Which is why I'm wondering if upgrading to JACK2 may help.

```
zenon@zenon-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: MobilePre [MobilePre], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zenon@zenon-ubuntu:~$ 

```The handle has no specific relation to said book, it is a cyber pseudonym that came to me many years ago.  However, in Athens I was informed by an astute greek at the end of a chance encounter and long conversation that Zeno is the name of a respected greek philosopher who apparently has a similar personality to myself.
[http://en.wikipedia.org/wiki/Zeno_of_Elea](http://en.wikipedia.org/wiki/Zeno_of_Elea)

---

### Post by robeast on 2010-02-10
What are your JACK settings?

I'm guessing that "control device hw:0" is not the location of your hardware...just a guess.

---

### Post by AutoStatic on 2010-02-10
> **robeast said:**
> I'm guessing that "control device hw:0" is not the location of your hardware...just a guess.It's *hw:1*, or even better *hw:MobilePre*. Use the latter as the Interface name and it should work.

@zenon222, cool story! If you ever have the time you should read The Abyss, my Bachelor thesis was based on that book and Zénon (the French equivalent of Zeno) is just a marvellous personality.

---

