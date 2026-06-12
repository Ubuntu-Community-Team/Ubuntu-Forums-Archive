---
title: "Practice Metronome?"
date: 2010-09-30
forum: Ubuntu Studio
---

### Post by MikesGuitar on 2010-09-30
This may not be the right thread for this but I figured someone here would know. Any decent metronome apps besides those in the software center? None of those worked, Thanks

---

### Post by 23dornot23d on 2010-09-30
Just done a quick search ..... [**metronome linux 2010 sourceforge**]("http://www.google.com/search?client=ubuntu&channel=fs&q=metronome+linux&ie=utf-8&oe=utf-8") ..... if no others use one ....

**Open Source** is always good to search on too ..... best I can do ..... as not used one for ages.

Just seen this ..... [online Metronome]("http://www.metronomeonline.com/")

---

### Post by AutoStatic on 2010-10-01
gtklick doesn't cut it for you?

---

### Post by Pablo_F on 2010-10-01
+1 for gtklick.

However, note that it is a jack application, so you need the jack server running before launching it. Instructions:



1) Install gtklick, qjackctl and jackd

From a terminal:

sudo apt-get install gtklick qjackctl jackd

2) I hope jackd configuration window will pop up. Choose YES, you want to give the user rtprio and memlock privileges. If you don't see such a window or you have selected NO by accident, do in the terminal:

sudo dpkg-reconfigure -p high jackd

3) Add you login or user name to the audio group:

sudo usermod -a -G audio your_user_name

4) reboot the computer.

At this point you should be able to run the jack audio server in realtime mode. Let's go on:

5) Sound and Video Menu: Launch Jack Control

6) Press Start button,. This will (hopefully) start the jack server.

If there is an error, post the contents of the message window and the terminal output of:

aplay -l

so we can help.

7) Launch gtklick. Preferences, select: "Automatically connect to soundcard output".

8 ) Start the metronome.

Done. 

Gtklick is very nice, I love it. Meter and patterns are very flexible. Take a look at the view menu too.

You might like hydrogen too (not just a metronome).

Cheers! Pablo

---

### Post by cchhrriiss121212 on 2010-10-01
Or if you don't want to use jack, gtick should work fine.

---

### Post by Steve H on 2011-02-05
> **Pablo_F said:**
> +1 for gtklick.

However, note that it is a jack application, so you need the jack server running before launching it. Instructions:



1) Install gtklick, qjackctl and jackd

From a terminal:

sudo apt-get install gtklick qjackctl jackd

2) I hope jackd configuration window will pop up. Choose YES, you want to give the user rtprio and memlock privileges. If you don't see such a window or you have selected NO by accident, do in the terminal:

sudo dpkg-reconfigure -p high jackd

3) Add you login or user name to the audio group:

sudo usermod -a -G audio your_user_name

4) reboot the computer.

At this point you should be able to run the jack audio server in realtime mode. Let's go on:

5) Sound and Video Menu: Launch Jack Control

6) Press Start button,. This will (hopefully) start the jack server.

If there is an error, post the contents of the message window and the terminal output of:

aplay -l

so we can help.

7) Launch gtklick. Preferences, select: "Automatically connect to soundcard output".

8 ) Start the metronome.

Done. 

Gtklick is very nice, I love it. Meter and patterns are very flexible. Take a look at the view menu too.

You might like hydrogen too (not just a metronome).

Cheers! Pablo

Pablo, thanks. You just saved me a headache.

---

### Post by BobvanderPoel on 2011-02-05
If you **really** want a metronome you've been given good advise about.

However, my experience is that metronomes are hard to play with and in many cases teach bad habits (like letting you cheat by permitting too many ticks for a note!). Not to stroke my own software too much, but you might want to look at my free program MMA as an alternate.

  [http://mellowood.ca/mma/index.html](http://mellowood.ca/mma/index.html)

Hope this helps.

---

