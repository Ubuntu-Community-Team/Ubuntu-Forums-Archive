---
title: "No sound from Rosegarden"
date: 2009-12-04
forum: Ubuntu Studio
---

### Post by stigb on 2009-12-04
I disabled the "Realtime" checkbox in JACK Control because it caused an error when I tried to connect, and afterwards it caused no errors. I started Rosegarden and it connected to Jack. I tried to import a demo file and play it, but there was no sound.
Rosegarden came up with two information windows when I started it: "System timer resolution is too low" and "Helper programs not found".

So, jah?

---

### Post by jake_am on 2010-03-11
I have placed "***" around the important parts!

I have been working on this same problem for days! When I first saw the error message about connecting to jack I immediately tried to fix it. I got rid of the error message, loaded a file and got no sound. I got the real time kernel and that got rid of the timing device message but I still didn't get any sound. Eventually I became angry/frustrated/fed up.

***
I ignored all three error messages and loaded a file out of frustration. I hit play and it worked perfectly! 
***

So, I have found a way to get rid of the jack "problem"(but that was in its self a major problem considering it didn't work when I did!), and the timing resolution "problem" (even though it works just fine without fixing that). but still haven't found a way to get rid of the last "problem" but I don't even know if it will cause any problems.

***
In summery, don't connect to jack, just ignore the 2 "problems" and they will go away.
***

How ever, you can fix the timing one if you like and I beleve it would still work. To get rid of the timing problem, install the realtime kernel. I used [this guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation") and it worked. Just scroll down to the "[SIZE=1]Real Time Kernel & Xruns" heading and follow the instructions. 
[/SIZE]

---

### Post by kayosiii on 2010-03-12
Unfortunately as of Ubuntu 9.10 jack out of the box is a little broken.
For a serious setup you will want to modify the security settings on your machine to allow jack to run in realtime mode. But that being besides the point.

The thing about rosegarden is that it has no built in sound synthesis capabilities. It can use either plugins or external midi synths (both hardware and software to achieve this). The easiest way to get sound of Rosegarden is to hook some kind of midi synth up to the general midi output of rosegarden. (I use a program called patchage to do this). 
Probably to here the demo properly you will want qsynth and a general midi soundfont. both of these should be in the ubuntu repositories.


I understand that this situation is not ideal for beginners. But there you have it.

---

