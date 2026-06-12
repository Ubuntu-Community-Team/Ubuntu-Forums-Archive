---
title: "Roland UA-22 (Duo Capture EX) driver fix or tips :D"
date: 2013-06-07
forum: Ubuntu Studio
---

### Post by darkuillity on 2013-06-07
Hello,
I've been struggling for months to get my Audio Interface to work in linux,
In coinsidence i was compiling some kernel, an idea hit my head!
Then i was be able to use my Roland UA-22 :D :D :D
So i wanted to share my problem and my solution to help other users have same problem.

OK, ready?
[U]
What you need:[/U]
- Latest Ubuntu Version (For better results, I Personally used 13.04) .
- Three Batteries Size: AA .

_Instructions:_
1- Turn off & Disconnect the device from computer.
2- Insert fresh batteries into your Roland UA-22.
3- Use the setting described in the attached picture.
Make sure you've selected from back panel (TAB)
4- Connect your device via USB & Turn it ON.

and Trallalalala :D, your audio interface will shine red color from led instead of green (tablet mode).

to make sure it's working use this in Terminal:
```
$ cat /proc/asound/cards
```
You'll get something like this:
```
 2 [UA22           ]: USB-Audio - UA-22
                      Roland UA-22 at usb-0000:00:1a.0-1.2, full speed

```

You can use it for listening and recording, and have fun :D

---

### Post by Finn bjerke on 2013-12-26
It does not work in Ubuntu 13.04, tried your approach no succes Im afraid

---

### Post by jejeman on 2013-12-26
I don't see how it can work since the card is not listed (recognized).
Give
```
aplay -l
arecord -l
```

---

### Post by Finn bjerke on 2013-12-26
NOt mentioned here [http://wiki.linuxaudio.org/wiki/hardware_support](http://wiki.linuxaudio.org/wiki/hardware_support)

---

