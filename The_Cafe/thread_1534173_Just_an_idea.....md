---
title: "Just an idea...."
date: 2010-07-19
forum: The Cafe
---

### Post by steele64e on 2010-07-19
Well, after brainstorming what i should try creating with python(just starting) I thought of a very interesting idea. That is, if it's possible for me and my limited (but ever expanding) knowledge of programming to create. Anyways, my idea is to create a little script(preferably in python) that converts a message say.... "Foo" into low/high(anything outside human hearing) frequency tones(similar to morose code) which then could be played out of the speakers. The second part of the script will be the receiver(located on a separate machine) which will(if possible) capture these tones, cut out all the background noise and convert them back into the original message.

So, is this possible? To me it seems that having a precise enough microphone and cutting out the background noises are the only real difficulties other than actually creating it.

All advice is welcome.

--Mike

---

### Post by matthew.ball on 2010-07-19
Don't know much about this, I believe my uncle was involved with some team which was designing the audio systems in conference rooms (particularly with respect to minimum signal degradation), and I only know that he mentioned DSP (wiki both digital signal processing, and digital signal processor). I'm guessing you'd be interested in a noise-reduction DSP algorithm, at the very least if only for receiving transmissions. No idea how to go about such a thing though, sorry, hope something here is useful.

---

### Post by Paqman on 2010-07-19
> **steele64e said:**
> 
So, is this possible?

Sure, remember dialup? Back in the old days you'd stuff the whole receiver of your telephone into your modem. The modem and the phone would yell at each other and you'd get your (appalling slow) data connection. Shifting it up into higher frequencies than voice would require specialised hardware, but the concept is the same.

---

### Post by Junkieman on 2010-07-19
I don't see any practical application for this, but find it very intriguing :)

The frequency range for humans is between 20 Hz and 20,000 Hz. 

Frequencies under below 100Hz are usually handled by professional live sound [sub woofers]("http://en.wikipedia.org/wiki/Subwoofer"). Not everybody has one.

The good news is that some [tweeters can handle]("http://en.wikipedia.org/wiki/Tweeter") frequencies 20,000+ Hz, well close and over the human hearing range. So you'd have to go for this higher frequency range. 

I'm not too clear about standard desktop PC speakers though, or the ranges that standard microphones can pick up. I'd work with mid level ranges if the hardware can't handle.

If you want to secure the signal, try a basic rot13-style encryption on the message. another clever way could be to construct a character/tone translation map from a seed, the seed being played/received pre/post message so that both sender and receiver can translate against the same map. Asymmetric encryption with a private/public key pair would just be overkill ;)

---

### Post by Excedio on 2010-07-19
If you cannot hear the signal, how do you know if it's being projected? ;-)

Seems like a troubleshooting nightmare...

---

### Post by Directive 4 on 2010-07-19
try a laser

---

### Post by LowSky on 2010-07-19
I would feel bad for any dogs you might have.

Talking over lazer would be cooler! Yes I spell lazer with a Z it makes it look cooler:!:

---

### Post by Penguin Guy on 2010-07-19
OMG! This idea is amazing! We can call it 'wireless'.

---

### Post by LowSky on 2010-07-19
> **Penguin Guy said:**
> OMG! This idea is amazing! We can call it 'wireless'.

2+2=4

I just put that together. Thanks Penguin Guy!

I will give steele64e his credit, he's trying to recreate something we take full advantage of without a thought on how it works.

---

### Post by Directive 4 on 2010-07-19
[FONT=Verdana, Arial, Helvetica, sans-serif] Electromagnetic  waves are different from sound       waves because they do not need molecules to travel.[/FONT]

---

### Post by Junkieman on 2010-07-22
> **Penguin Guy said:**
> OMG! This idea is amazing! We can call it 'wireless'.
Mod +1 Funny :D

---

### Post by limestone on 2010-07-22
> **Paqman said:**
>  "The modem and the phone would yell at each other" 

HAHAHA.. hilarious ^^

---

