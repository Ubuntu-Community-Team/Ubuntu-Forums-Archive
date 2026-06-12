---
title: "Audacity NO SOUND Please Help"
date: 2008-05-08
forum: Ubuntu Studio
---

### Post by philidox on 2008-05-08
I cannot figure out why audacity keeps giving me this error message:
"Error while opening sound device. Please check the output device settings and the project sample rate."  Even when I do select other audio playback device.  I either get the same error message or it will visually play the audio file but I still gets NO SOUND!

Just yesterday it was working flawlessly after I updated to 8.04 but the fix was only short lived because Audacity is back to missing up.  I love this program but I cannot figure out its bugs.  I have not touch the settings/preferences since the last time I used it when it was working so I'm lost on what to do.  If its not audacity settings/preferences thats keeping it from working properly, what is?  I closed all my other audio applications to include firefox, so what else could it be.  Also if anyone else know of another program that will allow me to cut and edit audio file PLEASE let me know because I have just about had it with audacity.  Please provide 1 of 2 things.
1. A solution to fix audacity's bug.
2. A comparable alternative to audacity.(I just need a program that can cut and edit audio file)

---

### Post by warbread on 2008-05-08
Are you by chance using Jack?  I get this error when the sample rate settings in Audacity (found in the lower left hand corner) don't match the sample rate set by qjackctl.  If not, we'll have to go a different direction.

How many sound cards do you have?

---

### Post by philidox on 2008-05-08
> **warbread said:**
> Are you by chance using Jack?  I get this error when the sample rate settings in Audacity (found in the lower left hand corner) don't match the sample rate set by qjackctl.  If not, we'll have to go a different direction.

How many sound cards do you have?

that's a good question because I think I have 2, but i'll double check and what is this jack? I know it some kind of sound device manager but ill try anything to get my sound right

---

### Post by warbread on 2008-05-08
[Jack]("www.jackaudio.org") is a sort of software mixer-board.  With it you can route the output of any jack enabled program to the input(s) of any other jack enabled program.  This means you can have 3 audio programs (zynaddsub, hydrogen and qsynth, for instance) each routed to a different input in Ardour (a hard disk recorder), the same input, or one going to an input and the rest outputting directly to the speakers.  

It sounds fairly complicated, but you can do a lot with it.  

Post the output of ```
:-$ cat /proc/asound/cards 
```  That will tell you how many cards you have, and how to route to it in Audacity.

---

### Post by philidox on 2008-05-08
> **warbread said:**
> [Jack]("www.jackaudio.org") is a sort of software mixer-board.  With it you can route the output of any jack enabled program to the input(s) of any other jack enabled program.  This means you can have 3 audio programs (zynaddsub, hydrogen and qsynth, for instance) each routed to a different input in Ardour (a hard disk recorder), the same input, or one going to an input and the rest outputting directly to the speakers.  

It sounds fairly complicated, but you can do a lot with it.  

Post the output of ```
:-$ cat /proc/asound/cards 
```  That will tell you how many cards you have, and how to route to it in Audacity.

philidox@philidox-desktop:~$ cat /proc/asound/cards
 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfbefc000 irq 25

Thats my output tell me how to read it and what to do.  Thx a million by the way

---

### Post by philidox on 2008-05-08
> **warbread said:**
> Are you by chance using Jack?  I get this error when the sample rate settings in Audacity (found in the lower left hand corner) don't match the sample rate set by qjackctl.  If not, we'll have to go a different direction.

How many sound cards do you have?

Nope not using jack and I only have one sound card its the onbooard sound that came with my motherboard

---

### Post by monraaf on 2008-05-10
Try this:

```
pasuspender audacity
```

And after audacity has started:

```
killall jackd
```

It works for me.

---

### Post by tamiz vure on 2008-05-11
Hi,, i'm new to ubuntu... One problem no sound.. I have got Acer travelmate 2400 (yeah i know i need a new comp). If any of u guys got any links for the multimedia drivers ..pls let me know.

Thanks in advance.
Tamiz:)

---

### Post by Suwessi on 2008-05-11
You're not the only one having this problem, see: [**this Audacity forum thread**]("http://audacityteam.org/forum/viewtopic.php?f=18&t=4006") and others in the same forum. 

For me, it works the first time I run the program afterwards it pops up with the same error message. I thought that I solved it by downgrading to the stable version but after a while the problem persists.

I've searched the [**audacity bug-reporting archives**]("http://sourceforge.net/mailarchive/forum.php?forum_name=audacity-bugs") and have not found an exact match being reported, although I believe that [**some**]("http://limpet.net/audacity/bugzilla/show_bug.cgi?id=282") [**may**]("http://limpet.net/audacity/bugzilla/show_bug.cgi?id=283") [**be**]("http://sourceforge.net/mailarchive/forum.php?thread_name=200710300222.53607.siegerstein%40pochta.ru&forum_name=audacity-bugs") related.

Hopefully, it will get resolved soon.

~Suwessi

---

### Post by warbread on 2008-05-11
> **philidox said:**
> philidox@philidox-desktop:~$ cat /proc/asound/cards
 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfbefc000 irq 25

Thats my output tell me how to read it and what to do.  Thx a million by the way

Go into Edit -> Preferences and in that first screen, make sure you have either ALSA: default or ALSA: VT82xx selected.  

If that doesn't work, you could try Rezound or Ardour.  Ardour requires Jack, though.

---

