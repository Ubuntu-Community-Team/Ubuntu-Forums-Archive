---
title: "Old School sound producing!!! Yay!!"
date: 2006-10-08
forum: The Cafe
---

### Post by SirKillalot on 2006-10-08
Install the program 'beep' via apt and try this script:

Edit: this is also another piece I made (in this thread):
[http://www.ubuntuforums.org/showthread.php?p=1596084#post1596084](http://www.ubuntuforums.org/showthread.php?p=1596084#post1596084)

```
beep -f 650 -l 500
beep -f 480 -l 250 
beep -f 500 -l 250 
beep -f 570 -l 500
beep -f 500 -l 250
beep -f 480 -l 250 
beep -f 425 -l 500
beep -f 425 -l 250
beep -f 500 -l 250
beep -f 650 -l 500
beep -f 570 -l 250
beep -f 500 -l 250
beep -f 480 -l 500
beep -f 480 -l 250
beep -f 500 -l 250
beep -f 570 -l 500
beep -f 650 -l 500 
beep -f 500 -l 500
beep -f 425 -l 500
beep -f 425 -l 1250
beep -f 570 -l 500
beep -f 675 -l 250
beep -f 850 -l 500
beep -f 750 -l 250
beep -f 680 -l 250
beep -f 640 -l 750
beep -f 500 -l 250
beep -f 640 -l 500
beep -f 575 -l 250 
beep -f 510 -l 250
beep -f 480 -l 500
beep -f 480 -l 250 
beep -f 500 -l 250
beep -f 575 -l 500
beep -f 650 -l 500
beep -f 510 -l 500
beep -f 430 -l 500 
beep -f 430 -l 1000

```

if you rock, make your own!

---

### Post by %hMa@?b&lt;C on 2006-10-08
yippee! thanks for that. I am going to work on some beep stuff~

---

### Post by rowanparker on 2006-10-08
This is so cool.

---

### Post by IYY on 2006-10-08
Allow me to try...

for ((x=1; x <= 100; x++)); do beep -f `expr $x \* $x` -l50; done

And...

for ((x=1; x <= 1000; x++)); do beep -f `expr $x` -l1; done

PS. Kill it with Ctrl+C when it gets too annoying. My ears are unhappy. :(

---

### Post by rowanparker on 2006-10-08
Cool.

Like the first one, not the second.

---

### Post by SirKillalot on 2006-10-08
Wow! I like that! (especially the first one :)

---

### Post by Wallakoala on 2006-10-08
> **SirKillalot said:**
> Install the program 'beep' via apt and try this script:

```
beep -f 650 -l 500
beep -f 480 -l 250 
beep -f 500 -l 250 
beep -f 570 -l 500
beep -f 500 -l 250
beep -f 480 -l 250 
beep -f 425 -l 500
beep -f 425 -l 250
beep -f 500 -l 250
beep -f 650 -l 500
beep -f 570 -l 250
beep -f 500 -l 250
beep -f 480 -l 500
beep -f 480 -l 250
beep -f 500 -l 250
beep -f 570 -l 500
beep -f 650 -l 500 
beep -f 500 -l 500
beep -f 425 -l 500
beep -f 425 -l 1250
beep -f 570 -l 500
beep -f 675 -l 250
beep -f 850 -l 500
beep -f 750 -l 250
beep -f 680 -l 250
beep -f 640 -l 750
beep -f 500 -l 250
beep -f 640 -l 500
beep -f 575 -l 250 
beep -f 510 -l 250
beep -f 480 -l 500
beep -f 480 -l 250 
beep -f 500 -l 250
beep -f 575 -l 500
beep -f 650 -l 500
beep -f 510 -l 500
beep -f 430 -l 500 
beep -f 430 -l 1000

```

if you rock, make your own!

You are awesome! I love tetris!

---

### Post by picpak on 2006-10-08
> **IYY said:**
> PS. Kill it with Ctrl+C when it gets too annoying. My ears are unhappy. :(

Now you tell me. I had to restart!

---

### Post by pianoboy3333 on 2006-10-08
Alright, so I got a bit into this, and I made some sort of python "module" so you can easily reproduce notes. Ranges from C 0 to E flat 8. Make sure you have the program beep installed. wo0t for python!
So, a sample program would do it:

#/usr/bin/env python
# get the module at: [http://piano.juicemedia.tv/python/play/play.py](http://piano.juicemedia.tv/python/play/play.py)

# Although most don't like import *, it's better here

from play import *
# instead of import play then play.play(play.A4, 1000)

play(C4, 1000)

---

### Post by SirKillalot on 2006-10-09
Hey, this is great, this will make sound production a lot easier, although the old school style gets a bit lost :(
Greetings

---

### Post by Josh1 on 2006-10-09
Wow thats really cool. Anymore? :D

---

### Post by Toe on 2006-10-09
You can also take a little hearing test:

```

beep -f 25 -l 2000
beep -f 50 -l 2000
beep -f 250 -l 2000
beep -f 500 -l 2000
beep -f 1000 -l 2000
beep -f 2000 -l 2000
beep -f 3000 -l 2000
beep -f 4000 -l 2000
beep -f 5000 -l 2000
beep -f 6000 -l 2000
beep -f 7000 -l 2000
beep -f 8000 -l 2000
beep -f 9000 -l 2000
beep -f 10000 -l 2000
beep -f 11000 -l 2000
beep -f 12000 -l 2000
beep -f 13000 -l 2000
beep -f 14000 -l 2000
beep -f 15000 -l 2000
beep -f 16000 -l 2000
beep -f 17000 -l 2000
beep -f 18000 -l 2000
beep -f 19000 -l 2000
beep -f 20000 -l 2000

```

The last three sounds are too high for my ears.

---

### Post by SirKillalot on 2006-10-09
Guys, I would appreciate if you just submitted music (melodies)
I just created this one, a bit strange but I gonna fix that little "bugs"

> beep -f 400 -l 750
beep -f 400 -l 500
beep -f 400 -l 250
beep -f 400 -l 750
beep -f 300 -l 500
beep -f 470 -l 250 
beep -f 400 -l 750
beep -f 300 -l 500
beep -f 470 -l 250
beep -f 400 -l 1400
beep -f 600 -l 750
beep -f 600 -l 500
beep -f 600 -l 250
beep -f 600 -l 750
beep -f 620 -l 500
beep -f 470 -l 250
beep -f 400 -l 750
beep -f 300 -l 500
beep -f 470 -l 250
beep -f 400 -l 1400
beep -f 800 -l 750
beep -f 800 -l 500
beep -f 800 -l 250
beep -f 800 -l 750
beep -f 760 -l 500
beep -f 730 -l 250
beep -f 680 -l 175
beep -f 650 -l 175
beep -f 680 -l 750
beep -f 500 -l 400
beep -f 680 -l 750
beep -f 650 -l 500
beep -f 620 -l 250
beep -f 590 -l 175
beep -f 570 -l 175
beep -f 590 -l 750
beep -f 400 -l 250
beep -f 510 -l 750
beep -f 400 -l 500
beep -f 500 -l 250
beep -f 600 -l 750
beep -f 500 -l 500
beep -f 600 -l 250
beep -f 760 -l 750


---

### Post by rowanparker on 2006-10-09
> **Toe said:**
> You can also take a little hearing test:

```

beep -f 25 -l 2000
beep -f 50 -l 2000
beep -f 250 -l 2000
beep -f 500 -l 2000
beep -f 1000 -l 2000
beep -f 2000 -l 2000
beep -f 3000 -l 2000
beep -f 4000 -l 2000
beep -f 5000 -l 2000
beep -f 6000 -l 2000
beep -f 7000 -l 2000
beep -f 8000 -l 2000
beep -f 9000 -l 2000
beep -f 10000 -l 2000
beep -f 11000 -l 2000
beep -f 12000 -l 2000
beep -f 13000 -l 2000
beep -f 14000 -l 2000
beep -f 15000 -l 2000
beep -f 16000 -l 2000
beep -f 17000 -l 2000
beep -f 18000 -l 2000
beep -f 19000 -l 2000
beep -f 20000 -l 2000

```

The last three sounds are too high for my ears.
Is it worrying that I'm 14 but can't hear the last 6?

---

### Post by rowanparker on 2006-10-09
> **SirKillalot said:**
> beep -f 400 -l 750
beep -f 400 -l 500
beep -f 400 -l 250
beep -f 400 -l 750
beep -f 300 -l 500
beep -f 470 -l 250
beep -f 400 -l 750
beep -f 300 -l 500
beep -f 470 -l 250
beep -f 400 -l 1400
beep -f 600 -l 750
beep -f 600 -l 500
beep -f 600 -l 250
beep -f 600 -l 750
beep -f 620 -l 500
beep -f 470 -l 250
beep -f 400 -l 750
beep -f 300 -l 500
beep -f 470 -l 250
beep -f 400 -l 1400
beep -f 800 -l 750
beep -f 800 -l 500
beep -f 800 -l 250
beep -f 800 -l 750
beep -f 760 -l 500
beep -f 730 -l 250
beep -f 680 -l 175
beep -f 650 -l 175
beep -f 680 -l 750
beep -f 500 -l 400
beep -f 680 -l 750
beep -f 650 -l 500
beep -f 620 -l 250
beep -f 590 -l 175
beep -f 570 -l 175
beep -f 590 -l 750
beep -f 400 -l 250
beep -f 510 -l 750
beep -f 400 -l 500
beep -f 500 -l 250
beep -f 600 -l 750
beep -f 500 -l 500
beep -f 600 -l 250
beep -f 760 -l 750 
And this one rules!

---

### Post by GStubbs43 on 2006-10-09
I can't hear the last 5 :mrgreen:

Actually 4, because ```
beep -f 20000 -l 2000
``` doesn't do anything. It just shows an error message.

---

### Post by pianoboy3333 on 2006-10-09
Alright, for beep maddness download [http://piano.juicemedia.tv/python/play/play.py](http://piano.juicemedia.tv/python/play/play.py) and [http://piano.juicemedia.tv/python/play/mario](http://piano.juicemedia.tv/python/play/mario)

Then run mario with play.py

Copy and paste code:
```

wget http://piano.juicemedia.tv/python/play/getplay
bash getplay
cd playdir
python play.py mario

```

If for some reason you don't have python then download [http://piano.juicemedia.tv/python/play/play](http://piano.juicemedia.tv/python/play/play) instead.

---

### Post by IYY on 2006-10-09
> Is it worrying that I'm 14 but can't hear the last 6?

It also depends on your PC speaker. I believe some of them wrap around after a certain frequency and play something so low that you can't hear it.

---

### Post by maniacmusician on 2006-10-09
> **pianoboy3333 said:**
> Alright, for beep maddness download [http://piano.juicemedia.tv/python/play/play.py](http://piano.juicemedia.tv/python/play/play.py) and [http://piano.juicemedia.tv/python/play/mario](http://piano.juicemedia.tv/python/play/mario)

Then run mario with play.py

Copy and paste code:
```

wget http://piano.juicemedia.tv/python/play/getplay
bash getplay
cd playdir
python play.py mario

```

If for some reason you don't have python then download [http://piano.juicemedia.tv/python/play/play](http://piano.juicemedia.tv/python/play/play) instead.
thats pretty cool. I did hear a few irregularities, but pretty damn close.

---

### Post by rowanparker on 2006-10-10
> **IYY said:**
> It also depends on your PC speaker. I believe some of them wrap around after a certain frequency and play something so low that you can't hear it.
Oh, phew :D

---

### Post by SirKillalot on 2006-10-10
> **Josh1 said:**
> Wow thats really cool. Anymore? :D

yeah, is there anyone who can make his own piece?

---

### Post by pianoboy3333 on 2006-10-11
> **SirKillalot said:**
> yeah, is there anyone who can make his own piece?

I can, but I don't have the time ;).

Note: I have also continued working on play.py, check [http://piano.juicemedia.tv/python/play](http://piano.juicemedia.tv/python/play) for updates and new songs every now and then. Currently I'm working on the guitar solo for a song in Wallakoala's request.

---

### Post by SirKillalot on 2006-12-28
music!

---

### Post by mips on 2006-12-28
> **rowanparker said:**
> Is it worrying that I'm 14 but can't hear the last 6?

Maybe your pc speaker cannot handle high freq ranges.

---

### Post by rowanparker on 2006-12-28
> **mips said:**
> Maybe your pc speaker cannot handle high freq ranges.
I sure hope so.

---

### Post by mips on 2006-12-28
> **rowanparker said:**
> I sure hope so.

Try and output a alternating 15000-20000Hz sine wave on good speakers or headphones and see what happens.

---

### Post by rowanparker on 2006-12-28
But its a system beep, it doesn't come out of my PC speakers?

---

### Post by mips on 2006-12-28
> **rowanparker said:**
> But its a system beep, it doesn't come out of my PC speakers?

Just generate the frequencies elsewhere, I did not say you had to use beep.

---

### Post by rowanparker on 2006-12-28
> **mips said:**
> Just generate the frequencies elsewhere, I did not say you had to use beep.
Oh right, how can I generate these frequencies then?
And I use my HiFi as my PC speakers, that'll be alright won't it?

---

