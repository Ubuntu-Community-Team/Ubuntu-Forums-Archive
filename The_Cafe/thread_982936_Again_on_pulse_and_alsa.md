---
title: "Again on pulse and alsa"
date: 2008-11-15
forum: The Cafe
---

### Post by zibi on 2008-11-15
Hi all!
I would like to address the question of the sound server.

After my upgrade to ibex I was having problems with skype which I didn't menaged to fix them until I decided to remove this damned pulse audio. 

I than goobunted around and I end up in the ubuntu brainstorm where the issue is considered.

Basically people say that to have pulse by default (even if messy to some extent now) will produce many benefit in future: it is a cross platform driver (or whatever it is) and cross-platform programmers will have less trouble in releasing linux verion of softwares involving sound menagement.

This is actually great. Still I want to underscore that:

1) I suppose to be a rater normal user: I'm not a programmer but if I have troubles I don't mind spending a couple of hours (maybe more) trying to look for a fix for my machine. I'm not scared of command line and I like to understand a little of how my beloved oS works.
Still it is quite messy not to have basic features like sound working out of the box. In particular, it's a shame to recommend people to switch to ubuntu, as the risk is that they end up saying <<Win was better>>.


2) The esound server rocks if compared with pulse. I mean that independetly of application NOT working, pulse have lower performance w.r.t. esound. I'm listening righ now to some mp3 on my 15 euro headpones, played with audacious. And the sound is rather clean. On the contrary with pulse I couldn't higer the volume too much otherwise hiss crack pop and whatever else.

So: First of all vote for this
[http://brainstorm.ubuntu.com/idea/129/](http://brainstorm.ubuntu.com/idea/129/)
a gui sound configurator 

Then. I pray the developers to bring pulse to a level comparable with esond and I hope that proprietary bastards will soon adjust their software to pulse. 

Anyway, maybe next time wait some more before introducing such a massive change in the default installation if it is so much problematic (expecially for end user that they may like the ubuntu philosophy but does not want to leave proprietary softwares).

Anyway I really would like to hear as much opinion as possible on such a matter as I really think it is crucial for thinking of the way in which ubuntu future is to be conceived as so many things come to intercat:
free VS proprietary software interaction
cross platform dev
end user needs

In the end, as always, the question is: which is the best way to make ubuntu (or just linux) the most used OS in the workd????

Bests
Luca

---

### Post by hanzomon4 on 2008-11-15
Let's just clear two thing up.. 

Pulse has nothing to do with suppling drivers
It does not replace ALSA, it replaces ESD

---

### Post by zibi on 2008-11-15
Thank you. Then it is the way in which pulse interact with alsa that is problematic, I guess...

I Edit accordingly.

---

### Post by eternalnewbee on 2008-11-15
> In the end, as always, the question is: which is the best way to make ubuntu (or just linux) the most used OS in the workd????
A revolution I'd say!!!
A comparison just visualized itself: Oil vs. Clean Energy.
EDIT: Not oil, but the ones controlling it.

---

### Post by bvm on 2008-11-15
when everything is working correctly (eg. buffer sizes) there will be NO objective difference in sound 'quality' when you compare pulse and esd. Neither will ever be the weakest link in the chain.Show me the abx tests to prove me wrong. 

Having said that, there is a greater possibility that things are owrking inoptimally as opposed to the windows' mantra of all or nothing (not necessarily a bad thing in audio terms)

---

### Post by hanzomon4 on 2008-11-15
If PA worked as stated it would rock, but Ubuntu fscked it up. No sound card with proper alsa drivers should stutter, shake and die under PA... so why do they?

---

