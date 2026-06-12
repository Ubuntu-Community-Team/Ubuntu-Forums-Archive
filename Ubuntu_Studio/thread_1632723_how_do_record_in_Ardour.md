---
title: "how do record in Ardour?"
date: 2010-11-28
forum: Ubuntu Studio
---

### Post by eMeRJot on 2010-11-28
Hi! I've got a problem. I want record something in Ardour by microphone. I start record and... It's silence! What must I choose and where to record by microphone?

P.S Sorry for my English. I'm from Poland... and you know ;)

---

### Post by ajgreeny on 2010-11-28
Does your mic work?
Can you hear output from your speakers when you talk into your mic?
Have you checked the record level in pulseaudio volume control?
Have you checked with *alsamixer* in terminal to see if the capture levels are too low?

It is very difficult to know what is wrong if you don't say what you have already tried.

---

### Post by eMeRJot on 2010-11-28
There you can see how looks my alsamixer:

[http://img528.imageshack.us/i/zrzutekranur.png/](http://img528.imageshack.us/i/zrzutekranur.png/)

I tried to choose something there:

[http://img3.imageshack.us/i/zrzutekranu10.png/](http://img3.imageshack.us/i/zrzutekranu10.png/)
[http://img823.imageshack.us/i/zrzutekranu2bt.png/](http://img823.imageshack.us/i/zrzutekranu2bt.png/)

But still it's nothing. 

I can say more... In record I can hear background sounds for example when I clicking something. It's something like "What U Hear" in Windows. I don't know how to chose it to recording by microphone.

---

### Post by cchhrriiss121212 on 2010-11-28
Hi
Ardour uses jackd (not pulse audio). Jack is designed to allow you to connect ports wherever you like, so you need to tell it which ports you want recorded.

So first you will need to open up the connections window in jack control and look for your mic capture port. You may need to test the all captures to see which one is your mic if you have more than one. You can do that by connecting your system capture straight to your system playback and listening. Then you need to connect it to the track you want to record to in Ardour, by default it will autoconnect capture1 to track1. 

Patchage is a good program for changing connections, you should have it installed already. The blue boxes show your audio ins/outs and the green boxes will show MIDI ins/outs.

Once the mic is connected to the track, you must arm the track by clicking the red record button next to the track name. You should now see a meter that will indicate your capture level. Once a track is armed you press the big record button on the main task panel and it should start.

---

### Post by Pablo_F on 2010-11-29
The problem with that kind of cards is that they have an internal mixer and lots of options and what-not and you have to figure out some sane settings in alsamixer. Maybe, if you paste the output of "amixer" command (between code tags please) someone can give you a good idea.

It is much easier with a pro card like m-audio PCI's...

Cheers, Pablo

---

