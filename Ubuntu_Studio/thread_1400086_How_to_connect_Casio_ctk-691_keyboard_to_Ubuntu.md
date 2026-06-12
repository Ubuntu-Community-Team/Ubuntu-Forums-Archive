---
title: "How to connect Casio ctk-691 keyboard to Ubuntu"
date: 2010-02-06
forum: Ubuntu Studio
---

### Post by jocampo on 2010-02-06
HI,

I just found Piano Booster, a kind of Linux tutorial for learning piano, and would like to use it with my Casio ctk-691 keyboard. What do I need or how to I plug my piano so I can use it as midi keyboard for any Linux Piano software?

Thanks in advance,

---

### Post by niffcreature on 2010-02-06
this is not related to any operating system or keyboard in particular. you should probably have done some simple googling or manual reading... just saying.
i cant tell if you already know about midi interfaces or not. well, thats the main thing you need. if you were thinking it wouldnt work with linux, you dont really have anything to worry about.
theyre around $40 at stores and $10 online btw

---

### Post by jocampo on 2010-02-06
> **niffcreature said:**
> this is not related to any operating system or keyboard in particular. you should probably have done some simple googling or manual reading... 

Don't  you think that if I have not checked before, I have not posted already?

I do not have the manual ... and it is related to Ubuntu, because I would like to use Piano Booster, which is a Linux program. 

Thanks for reply anyway, though it looks like you were not so motivated to help.

---

### Post by robeast on 2010-02-06
jocampo, the problem with your question is that, in order to answer it, I had to do my own search to find out about your keyboard and Piano Booster because you gave us no info about them...

Bitching aside, you will need a MIDI interface so you can plug your keyboard MIDI out into your computer. The Midisport interfaces are simple and very cheap. As far as making use of that with Piano Booster, it looks like it needs separate synth software to make sounds and it didn't say which audio drivers it uses. Hopefully it just recognizes the available MIDI instruments on your system.

---

### Post by jocampo on 2010-02-07
TO anyone interested in use your Midi Keyboard with Piano Booster, on Linux, here's how to do it...

1st, this is my Linux version:

Linux studio 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64 GNU/Linux


The piano I am using is a cheap CASIO CTK-691. There are two midi ports in the back, out and in. You need to buy a Midi to USB cable.

What to do

1.Plug Midi to USB cable on back of midi keyboard (out in "out" and in goes to "in" port) The USB connector goes to one of your PC USB port, of course (I suggest doing this with keyboard off)
2. Turn keyboard on and open Piano Booster
3. On Piano Booster go to Midi Setup and change Midi Input and Midi Output devices to the new USB interface that you will get because the cable you just plugged. On mine, is USB UNO interface: MIDISPORT Uno USB-TO-MIDI Interface, about 20 bucks new. But I guess any similar cable should work.

Enjoy! Piano Booster will recognize your midi keyboard immediately. I did not install or download any additional driver. You will have to get some midi songs before start practicing; there are some demos on Piano Booster website.

---

### Post by robeast on 2010-02-07
How's the software? Hearing about this is making me want to re-learn piano.

---

### Post by jocampo on 2010-02-07
> **robeast said:**
> How's the software? Hearing about this is making me want to re-learn piano.

I love it! It is really intuitive and easy to use. It let you play at your own pace and stop when you make a mistake. Take a quick look on this Youtube video:

[http://www.youtube.com/watch?v=UGbfm8Tv-20&feature=player_embedded]("http://www.youtube.com/watch?v=UGbfm8Tv-20&feature=player_embedded")

My wife plays piano a bit (she's a former opera singer) and she's impressed of what I've done so far with just 24hrs of practice. I'm not saying you will learn piano in weeks, but speeds up the learning curve a lot and it's fun ... besides, open source (free)

Kudos for the developer!

PS: not sure but I think it is on Edubuntu

---

