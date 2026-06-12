---
title: "A little shot of DRM"
date: 2006-06-14
forum: The Cafe
---

### Post by nalmeth on 2006-06-14
I've officially had a bad personal experience with DRM

I was browsing torrents, and found a little video, just a clipping of a movie, and it was described as "With DRM". I downloaded the small video (about 3 megs or so), just to see how Ubuntu would handle it, what kind of error I would get, or whatever else *could* happen.

Well as fast as I double-clicked the little guy, my entire X went black, and hardlocked the system. No way around it, no restarting X, only hard-reboot.

It was a little disheartening. How could a small video cause such a hard crash? What kind of DRM is really in this file? Is this an intended effect? Or is this just a side-effect of it's programming?

Should I be searching for any unfamiliar traces in my /home? Where should I report this kind of incident? 

Anyone up for a guess as to what happened?

---

### Post by Kernel Sanders on 2006-06-14
[QUOTE=nalmeth]I've officially had a bad personal experience with DRM

I was browsing torrents, and found a little video, just a clipping of a movie, and it was described as "With DRM". I downloaded the small video (about 3 megs or so), just to see how Ubuntu would handle it, what kind of error I would get, or whatever else *could* happen.

Well as fast as I double-clicked the little guy, my entire X went black, and hardlocked the system. No way around it, no restarting X, only hard-reboot.

It was a little disheartening. How could a small video cause such a hard crash? What kind of DRM is really in this file? Is this an intended effect? Or is this just a side-effect of it's DRM programming?

Should I be searching for any unfamiliar traces in my /home? Where should I report this kind of incident? **Anyone up for a guess as to what happened?**[/QUOTE]

You got owned? :razz:

---

### Post by professor_chaos on 2006-06-14
I did a google on "With DRM" and video. Came upon a blogging site that seemed like a promising article, and then firefox crashed instantly. Firefox never crashes on me.

Coincidence or Conspiricy???

---

### Post by NeghVar on 2006-06-14
The DRM is written to work with Windows most likely so it was probably just an unexpected consequence of being in an unusual environment. Its odd that it would cause so many problems though.the whole firefox crashing thing, I have firefox crash at random sitesa then when I go back it is fine, its EXTREMELY rare now but it does happen maybe once every 2 months or so.

---

### Post by nalmeth on 2006-06-14
>  You got owned? :razz: hehe yes
I'm right pissed off about it too

Professor Chaos, search up a Team America clip, about 2.5 megs "With DRM"

If you want to get owned too.

---

### Post by nalmeth on 2006-06-14
> The DRM is written to work with Windows most likely so it was probably just an unexpected consequence of being in an unusual environment. Its odd that it would cause so many problems though.the whole firefox crashing thing, I have firefox crash at random sitesa then when I go back it is fine, its EXTREMELY rare now but it does happen maybe once every 2 months or so.
Whether it was an unexpected consequence is questionable I think. That is a hard acting side-effect, and it seems to me it takes a sort of intent to hard-freeze the X server like that.
As far as I'm concerned this is malware that successfully attacked my system. 
I still get the odd video that claims to be 'unsupported', and I assume that has some DRM measures that simply don't allow decoding. This was different though, it caused my system to crash.

---

### Post by imagine on 2006-06-14
The actual question is: Why would anyone want to download files with Direct Restriction Management?

---

### Post by nalmeth on 2006-06-14
[QUOTE=imagine]The actual question is: Why would anyone want to download files with Direct Restriction Management?[/QUOTE]
[quote=nalmeth]I downloaded the small video (about 3 megs or so), just to see how Ubuntu would handle it, what kind of error I would get, or whatever else *could* happen.[/quote] It's something the world has to face and conquer at some point, I wanted to see a random example of how my system would react to "DIGITAL _*RESTRICTIONS*_ MANAGEMENT"
Not a great impression.
[QUOTE=nalmeth] [COLOR=Red]As far as I'm concerned this is malware that successfully attacked my system.[/COLOR] [/QUOTE]

---

### Post by Dr. C on 2006-06-14
I would suggest reporting a bug. The fact that this brought down an X-server would indicate a vunerability in Ubuntu that this DRM exploited. 

[http://www.ubuntu.com/support/bugs]("http://www.ubuntu.com/support/bugs")

---

### Post by jason.b.c on 2006-06-15
> search up a Team America clip,

That movie was **hilarious**..!!   :D

---

### Post by prizrak on 2006-06-15
Alot of .wmv's kill my firefox if they embedded in a site. Once in a while they destroy GDM as well (not actually X but it's not easy to tell, which one is dead IMO it's GDM not X itself).
One way around that is hitting ctrl+alt+f1 that takes you to a virtual text console so you can reboot at the very least.

---

### Post by nalmeth on 2006-06-15
>  One way around that is hitting ctrl+alt+f1 that takes you to a virtual text console so you can reboot at the very least.
Tried, I was totally paralyzed.

---

### Post by prizrak on 2006-06-15
[QUOTE=nalmeth]Tried, I was totally paralyzed.[/QUOTE]
That is one serious piece of malware

---

### Post by nalmeth on 2006-06-15
Yeah it sucks
I know its one incident, but it's sort of a wake up call, thats one serious outcome just from trying to play a 
DRM'ed video. 

@ FineE: 
A bug report is a good idea, I will do so.

If anyone wants the link PM me and I'll email it to you (no torrent posting on forums), because I'm *sure* a lot of people want to try ;)

BTW when playing a few games on that PC, in the terminal I get this libGL error message, something like

Too slow, switching to indirect rendering .... .... ... drmLIB ...

I will post the full output when I get home tonight. I'm sure it's nothing related, but then again..
[quote=Professor Chaos]Coincidence or Conspiricy???[/quote]

---

### Post by wmcbrine on 2006-06-16
[QUOTE=nalmeth]BTW when playing a few games on that PC, in the terminal I get this libGL error message, something like

Too slow, switching to indirect rendering .... .... ... drmLIB ...[/QUOTE]That's a completely different "DRM" -- in this case it stands for "Direct Rendering Manager".

---

