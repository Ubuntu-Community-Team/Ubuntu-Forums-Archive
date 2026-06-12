---
title: "Calling all EE Majors or people who like Circuitry"
date: 2005-08-18
forum: The Cafe
---

### Post by kvidell on 2005-08-18
[http://www.thinkgeek.com/gadgets/electronic/79be/](http://www.thinkgeek.com/gadgets/electronic/79be/)

I'm of the opinion that that thing is ridiculously expensive for what it is, especially since it's "No Battery Included" AND shipping is extra.
It looks like a $2 Radio Shack project, and that's what I'm going to do.
Problem is I don't know circuitry.. At all.

My stepdad and I are going to try to make one ourselves from old parts out in the garage, but it would be a lot easier if we had a schematic.
He's good with electronics but we'll be making it up as we go along...

My task to you is this:
Draw up the circuitry and needed bits to do what that thing does for less than $25 :-P
What do you get out of it? You'll know how to make a distastefully annoying device and will have provided a fellow Ubuntuite with a couple hours of entertainment while he makes a couple dozen of them to annoy his friends with.

Plus all the other ubuntuites that will now know how to make them..

We can take over the world with annoying small beeping devices!

Go! Go my little electrical heads! Design! :-D
- Kev

From the ThinkGeek website:
> A devious hide-and-seek game
The Mind Molester is an instrument of creative electronic harassment. It is an electronic device that can drive your victims a little crazy trying to figure out what it is and where it's located. Your friends/enemies will become obsessed, awaiting the next chirp trying to determine its location, completely disrupting their normal activities.

Just connect this device to a 9-volt battery and plant it in an appropriate location. It produces a one-second electronic chirp about once every 3 minutes. Due to the chirp's duration, frequency, and sound characteristics, it's a very difficult, time-consuming, frustrating and maddening task to locate the unit. And even if they find it, they'll have no idea what it is. The number of effective locations to plant the Mind Molester is limited only by your imagination. Of course, this device is for use on deserving subjects only.

Also has these features.

    * First beep cycle is about 5 minutes, then every 3 minutes
    * No identifying marks
    * Requires 9-volt battery (not included)
    * Chirp frequency: 2000Hz
    * Dimensions: 2" x 1"

---

### Post by xmastree on 2005-08-18
Yeah, I made one way back in the early 80s.

Actualy, what I made was a combination of two circuits featured in Elektor. One was an electronic cricket, the other was similar to that one.
The difference with mine was that it only operated in the dark. Turn on the light and it stopped. Turn it off again and it waited a while and started again.


One second pulse every three minutes eh?

Analog version:
You can use a largish capacitor, charge it, and wait for the voltage to decay. Once it's below a threshold, like <1V, trigger the bleep then charge it again.


Digital version:
Use an 8 bit counter and an 8 input and gate, inputs connected to the counter outputs. Feed 1Hz into the counter, trigger the buzzer from the output of the gate.
It'll bleep once every 256 seconds, when the counter reaches FF.

---

### Post by macgyver2 on 2005-08-18
Have you tried your local library?  Back when I was about 10 I found this really cool electronics book in the county library and I think it had one of those things in it.  It also had things like photocell trip alarms and motion sensors and lots of other gadgets and things.

---

### Post by BWF89 on 2005-08-18
How will someone go mad not knowing where you put it? It's not like it's exactly small and easy to conceal. And even if you didn't know where someone put it It wouldn't be hard to find just by looking behind and under everything.

---

### Post by kvidell on 2005-08-18
[QUOTE=BWF89]How will someone go mad not knowing where you put it? It's not like it's exactly small and easy to conceal. And even if you didn't know where someone put it It wouldn't be hard to find just by looking behind and under everything.[/QUOTE]
 You ever lose your pager under some papers?
I've done that before.
The tone I had mine set to beep at made it impossible to find it using audial depth perception.

That's what this does. They're _very_ difficult to find, and look at it, it's smaller than the battery it's attached to, and those batteries aren't exactly huge :-P

macgyver2: I'm gunna do that I think.
My stepdad gave me the name of some books I could look at if I wanted to try on my own since he's gunna be busy for awhile.

Thanks guys :-D
- Kev

---

