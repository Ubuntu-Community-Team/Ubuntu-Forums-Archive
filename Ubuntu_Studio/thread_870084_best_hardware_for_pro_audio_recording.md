---
title: "best hardware for pro audio recording?"
date: 2008-07-25
forum: Ubuntu Studio
---

### Post by bmce on 2008-07-25
I am going to build a new machine specifically for recording and producing professional audio. I am somewhat new to Linux (and to building computers), but I would like to dual boot XP and Ubuntu and gradually switch over to Ubuntu for my recording projects. 

I want to make sure all of the hardware I buy is Linux compatible. Does anyone have recommendations for what to buy, or what not to buy? 
 
Or, what's your dream setup for a Linux audio machine?

---

### Post by thorgal on 2008-07-25
that's my setup, it works really nice!

[http://linuxmusicians.com/viewtopic.php?t=101](http://linuxmusicians.com/viewtopic.php?t=101)

I run debian sid and my own realtime kernel (compiled myself)

---

### Post by hansdown on 2008-07-25
Sweet system thogal. Very nice.

---

### Post by russo.mic on 2008-07-26
So,  The RME Fireface offers great sound quailty, great mic pres, and linux support.  

For the more price concenious, I must say the presonus firepod does quite well.  8 Channels, and you can daisy chain up to 2 more for 24 channels.  Believe it or not, sync is upheld between the 3 very reliably under freebob, and horribly under windows and osx. 3 of them in a rack with ardour is my mobile rig.

Russo

---

### Post by Good Speed on 2008-10-13
Hello, i have a RME fireface 800, for me it'is a great and professonnel sound card with very low latency (5ms with a fiwire 400)

---

### Post by robeast on 2008-10-13
> **russo.mic said:**
> 
For the more price concenious, I must say the presonus firepod does quite well.  8 Channels, and you can daisy chain up to 2 more for 24 channels.  Believe it or not, sync is upheld between the 3 very reliably under freebob, and horribly under windows and osx. 3 of them in a rack with ardour is my mobile rig.
Russo

I also back the firepod. I'd never heard of anyone tripling up on them with Linux before, was it easy to accomplish?

---

### Post by Mike'sHardLinux on 2008-10-16
> **Good Speed said:**
> Hello, i have a RME fireface 800, for me it'is a great and professonnel sound card with very low latency (5ms with a fiwire 400)

Since when has the Fireface been supported under Linux????? I don't believe it!!?? And I sold mine a while back because there was no chance of RME ever making any Linux drivers!!!!! Is it really true???

What about this? [http://freebob.sourceforge.net/index.php/List_of_Supported_Devices]("http://freebob.sourceforge.net/index.php/List_of_Supported_Devices")

---

### Post by robeast on 2008-10-17
> **Mike'sHardLinux said:**
> Since when has the Fireface been supported under Linux????? I don't believe it!!?? And I sold mine a while back because there was no chance of RME ever making any Linux drivers!!!!! Is it really true???

What about this? [http://freebob.sourceforge.net/index.php/List_of_Supported_Devices]("http://freebob.sourceforge.net/index.php/List_of_Supported_Devices")

Both the ffado and freebob websites explicitly say that the Fireface is unsupported. Is Good Speed moonlighting with another operating system? If not, how did you get it to work?

---

### Post by rayj on 2008-10-19
The M-Audio Delta 1010 is my card, and I'm surprised by the quality of the converters. They are exceptionally good at revealing how crappy my cheap mixer preamps are.

---

### Post by Tlon on 2008-10-30
According to RME's own website, there are both OSS and ALSA Linux drivers for the Fireface 800... they just aren't made, maintained, or supported by RME themselves.  In any case, I may be getting one of these from a friend this weekend, so I will report back on whether or not I was able to get it working...

---

### Post by Tlon on 2008-10-30
I spoke too soon... there are drivers for all EXCEPT their firewire devices :(

Could something like CrossOver make this work?

---

### Post by Mike'sHardLinux on 2008-10-30
Something like Crossover or WINE won't work. Those don't work at the driver level as far as I know. They are meant to run applications.

I am pretty sure the possibility of ever running the Fireface in Linux is zero. I would never have sold my Fireface otherwise. That is one of the best pieces of audio gear I have EVER owned!

---

### Post by eshattow on 2009-08-17
A to-be-unnamed coder alluded how RME as a company relates to the products it sells.

RME (the company and brand) is a sales and marketing team that's been added on to sort of loose network of product engineers. A new product is the engineer's "baby", theirs alone to bring into completion. Marketing and sales have no idea what is going on and the engineer is somewhat autonomous and separate from support requests. The engineer does not reveal the product until it is completed or very near completion. This is counter to everything you'd expect from a company. All those petitions or complaints asking for Linux platform support end up in a sales / marketing bin for "things the engineer may ask us about" and NOT as a todo list for the engineer.

Whoever was behind the design of the Fireface thought of Linux as a hobbyist or do-it-yourself platform, and it was not interesting to make driver support for that. Driver and platform support is subject to the whim of whoever happened to make the product, so Linux was not interesting and it never got anywhere with the engineer who knew enough to provide needed specifications. Furthermore it was never known to ask sales / marketing about whether anyone wanted it or not.

Over a conversation in-person about RME products being used on Linux platforms to analyze signals at nuclear facilities, a bet that the unnamed coder knew a surprising lot more about the engineer's "baby" than expected, and no doubt a beer or two, ... independently written drivers and the Linux platform had caught the engineer's interest.

So the challenge: figure out the rest and the unnamed coder gets full specs and sample hardware to write independent drivers.

Disclaimer: I forgot who had what to do with it, and I may be misquoting or completely fabricating this backstory. The point of it is that people voicing support for Linux as a platform do generally misunderstand how RME the company is set up, and that a face-to-face interaction was necessary to start this process.

Many months later the FFADO project benefits from the attention of interested parties within RME, and [driver support for the Fireface is being actively developed]("http://www.ffado.org/?q=node/1061").

---

