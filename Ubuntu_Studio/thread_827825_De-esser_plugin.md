---
title: "De-esser plugin"
date: 2008-06-13
forum: Ubuntu Studio
---

### Post by roaldz on 2008-06-13
Hello,

I was wondering if any of you guys are having the same problems as I have. I´m mixing some band with ardour and jamin, and I really need a de-esser for the lead vocals. I can only find 1 de-esser, found in the TAP plugins pack. This de-esser doesn´t work. I can´t understand why, all other plugins just work.
I´m running 2.6.24-19-generic x64 on an Intel C2D 2.0, 2 gig RAM.

Please help me with the TAP de-esser, or point me to an alternative!

Thank you

---

### Post by roaldz on 2008-06-13
bump

---

### Post by roaldz on 2008-06-13
bump´d

---

### Post by roaldz on 2008-06-14
cmon, help me:) I´ve helped you too!

---

### Post by roaldz on 2008-06-14
up

---

### Post by roaldz on 2008-06-15
up

---

### Post by thorgal on 2008-06-15
don't know about a good de-essing plugin but :

1- can you re-record the vocals with a filter of some sort ?

2- if not, can you analyze the vocal frequencies and spot which frequency range poses problem ? I would guess the essing effect is occupying a very narrow bandwitdh (I don't really know, I never faced this problem). Could you try to spot it and work with some EQ or use a very frequency restricted compression ?

---

### Post by roaldz on 2008-06-15
> **thorgal said:**
> don't know about a good de-essing plugin but :

1- can you re-record the vocals with a filter of some sort ?

2- if not, can you analyze the vocal frequencies and spot which frequency range poses problem ? I would guess the essing effect is occupying a very narrow bandwitdh (I don't really know, I never faced this problem). Could you try to spot it and work with some EQ or use a very frequency restricted compression ?

No, I can´t re-record the vocals, because it´s a live gig.
De-essing is in fact a compressor with a bandfilter, but I can´t find a way to cleverly chain these together to make a de-esser.. I´ve tried to use the SC2/3 compressor on a seperate buss in ardour, and feed it with only 5/6KHz, but that gave me internal feedback..

Don´t you find it weird that there´s only 1 LADSPA de-esser plugin available? The TAP-de-esser is mostly made for ardour, so I´m a bit confused..

Thank you for your reply.

Roald

---

### Post by thorgal on 2008-06-15
what do you mean by "internal feedback" ??
... do you need to reroute through a bus ? why don't you use these plugins in the track post fader directly (i.e. internal insert) ? ardour is non destructive so unless you freeze the track explicitely, you still keep the original audio.

---

### Post by warbread on 2008-06-15
Have you tried just dropping the volume by 6-7 dB on the ess?  It's not pretty, but I've read that works.

---

### Post by roaldz on 2008-06-15
> **warbread said:**
> Have you tried just dropping the volume by 6-7 dB on the ess?  It's not pretty, but I've read that works.

You mean by using an equalizer on the ´ess´ freq? That would take out 5.5K-6.5K, thats where a part of the definition of his voice is.

I just want to compress the 5.5K-6.5K freq´s above some threshold, any tips?

---

### Post by thorgal on 2008-06-15
you could use jamin as an insert but for a realtime effect, it is not best, it introduces some latency and is very CPU hungry. But you could isolate the track in ardour, process it through jamin used as an insert, export the result in a file, reimport in ardour with the rest of the session.
Jamin is quite cool, it has three freq domains, each has its own compressor and you can graphically set the region boundaries in the freq spectrum. So you can define a very narrow region using the mid-freq band, leave the low and high freq bands uncompressed, and apply the mid band compressor according to taste.

---

### Post by Stochastic on 2008-06-16
What troubles are you having with the TAP de-esser?  Is it not loading into Ardour, or is the effect not drastic enough / what you've desired?  Here's the official documentation: [http://tap-plugins.sourceforge.net/ladspa/deesser.html](http://tap-plugins.sourceforge.net/ladspa/deesser.html)

---

### Post by roaldz on 2008-06-16
> **Stochastic said:**
> What troubles are you having with the TAP de-esser?  Is it not loading into Ardour, or is the effect not drastic enough / what you've desired?  Here's the official documentation: [http://tap-plugins.sourceforge.net/ladspa/deesser.html](http://tap-plugins.sourceforge.net/ladspa/deesser.html)

I´ve read the docs, didn´t help. I can load it in ardour, but it doesn´t work. If I put the threshold on -50dB the attenuation meter wont bite.. It just doesn´t work.. 

@thorgal:
Thank you for the jamin bandcompressor tip, didn´t think of that. I´ve used jamin before, a lot. Gonna try it:)

---

### Post by Stochastic on 2008-06-17
> **roaldz said:**
> I´ve read the docs, didn´t help. I can load it in ardour, but it doesn´t work. If I put the threshold on -50dB the attenuation meter wont bite.. It just doesn´t work.. 

Really? I tested it on my system and it works.  Do you have the bypass enabled (I know stupid question, but you never know)?  What output do you get from ```
apt-cache policy tap-plugins
```

---

