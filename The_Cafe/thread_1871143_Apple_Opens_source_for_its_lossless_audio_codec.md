---
title: "Apple Opens source for its lossless audio codec"
date: 2011-10-28
forum: The Cafe
---

### Post by Lucradia on 2011-10-28
[http://arstechnica.com/apple/news/2011/10/after-seven-years-apple-open-sources-its-apple-lossless-audio-codec.ars](http://arstechnica.com/apple/news/2011/10/after-seven-years-apple-open-sources-its-apple-lossless-audio-codec.ars)

Bang!

---

### Post by Paqman on 2011-10-28
Which I guess means it can now be supported more widely. Although TBH this is the first time I've ever heard of it, so there can't be too many people out there gagging for ALAC support.

---

### Post by dpny on 2011-10-28
> **Paqman said:**
> Which I guess means it can now be supported more widely. Although TBH this is the first time I've ever heard of it, so there can't be too many people out there gagging for ALAC support.

I think lossless is mainly an audiophile thing.

---

### Post by tr333 on 2011-10-29
ALAC is supported natively on the iPod/iPhone unlike FLAC, which is useful to some people.  It's also used in [AirPlay](http://www.apple.com/itunes/airplay/).

---

### Post by 3rdalbum on 2011-10-29
Just as long as it's more community-based open-source than Apple's previous efforts. In the past, open-source for Apple was "Here's a bundle of source code for the current release version" and "If you find a bug, e-mail us and we might fix it in two years when the next release comes out".

For ALAC, Apple should allow access to the bug tracker and read access to their CVS at least.

---

### Post by Paqman on 2011-10-29
> **tr333 said:**
> ALAC is supported natively on the iPod/iPhone unlike FLAC, which is useful to some people.  It's also used in [AirPlay](http://www.apple.com/itunes/airplay/).

I've never understood the desire for lossless on a portable device. Background noise will mean you can't hear the difference anyway.

---

### Post by moldaviax on 2011-10-29
presume this move is to encourage uptake? presumably beyond apple devices?

M.

---

### Post by Lucradia on 2011-10-29
> **moldaviax said:**
> presume this move is to encourage uptake? presumably beyond apple devices?

M.

Android / Linux wouldn't use ALAC when it's been using FAAD / FLAC / OGG for years.

---

### Post by Legendary_Bibo on 2011-10-29
> **Lucradia said:**
> Android / Linux wouldn't use ALAC when it's been using FAAD / FLAC / OGG for years.

The point is now it can legally.

---

### Post by krapp on 2011-10-29
Eh who cares. FLAC is already around. This hardly makes Apple open-source friendly.

---

### Post by speedwell68 on 2011-10-29
> **krapp said:**
> Eh who cares. FLAC is already around. This hardly makes Apple open-source friendly.

It doesn't make then unfriendly either.  I can't see any negatives in this move from Apple.

---

### Post by krapp on 2011-10-29
Making ALAC in the first place instead of opting for FLAC was unfriendly. If they had anything to gain financially from ALAC they would've kept it shut down.

---

### Post by dpny on 2011-10-30
> **krapp said:**
> If they had anything to gain financially from ALAC they would've kept it shut down.

Apple's a hardware company. They make almost no money from software.

---

### Post by Nixarter on 2011-10-30
A wolf in sheep's clothing...

It isn't a bad thing completely, though.  But the intentions are all about market share.  Since greed is the underlying reason... it is bad :p

But I've been waiting for steps like these for a long time, to be honest.  I've always said... whoever comes out with a REAL online audio service, I will use it.  Does this mean Apple has (or will soon have) lossless audio in addition to compressed audio?  On a CD, tracks cost about $1 apiece.  On Apple, they do too... BUT that's the same price, for a lower quality song.  If I'm going to pay full price, I want full quality.  That being said, I would gladly pay the full price of CD audio for the same quality digital audio file online, whether it is from Apple or whoever.

Anyone know more?

Also, open-source doesn't mean free.  They could still force licensing if they so chose.  It might be for higher brand recognition as well, if it is freely licensed.  Or, it could be because samsung just outsold their new iphones :p  Or... they could just be trying to balance out some of the gestapo-esque practices they have.  Another big possibility is that they are genuinely trying to bring in audiophiles, and we don't put up with the crap that other people do :p  But who knows.

---

### Post by Bachstelze on 2011-10-30
> **Legendary_Bibo said:**
> The point is now it can legally.

Implying it couldn't before. That might be true but then it would mean that ALAC is patented (because the source code of libavcodec is entirely written by the ffmpeg project, and thus does not conflict with Apple copyright-wise). And if ALAC is patented, I see nothing here that indicates that the patent has been "lifted", meaning that any other implementation of the codec still infriges it, regardless of whether Apple's codec is open source or not.

*EDIT:* ALAC is the only lossless audio codec that is supported in .mp4 files (at least as defined by the standard), so if you want a compatible .mp4 file with a lossless soundtrack, ALAC is your only choice. Also I am not sure how good the libavcodec implementation of ALAC encoding is, but if it's like FAAC for AAC, it basically sucks, so if someone wants to encode on Linux a lossless soundtrack for a .mp4 file, this is definitely good news.

---

### Post by Warpnow on 2011-10-30
I despise apple but still am glad this is open sourced.

More open source code is good. Even if it has no practical application for users (though I would bet this does have one) the mere open source nature of the code gives aspiring programmers code to analyze and promotes further development.

---

### Post by tr333 on 2011-10-30
> **Bachstelze said:**
> Implying it couldn't before. That might be true but then it would mean that ALAC is patented (because the source code of libavcodec is entirely written by the ffmpeg project, and thus does not conflict with Apple copyright-wise). And if ALAC is patented, I see nothing here that indicates that the patent has been "lifted", meaning that any other implementation of the codec still infriges it, regardless of whether Apple's codec is open source or not.

ALAC is now licensed under [Apache License 2.0](http://en.wikipedia.org/wiki/Apple_Lossless) which is GPLv3 compatible.  I don't think there will be any patent problems with it, but IANAL.
Quoting from [http://www.apache.org/licenses/:](http://www.apache.org/licenses/:)
> The goals of this license revision have been...
...to require a patent license on contributions that necessarily infringe the contributor's own patents

---

### Post by FakeOutdoorsman on 2011-10-30
I wrote a mini-guide showing how to [compile, install, and use alacconvert](http://ubuntuforums.org/showpost.php?p=11404469&postcount=1900).

Although I don't see myself using this format, the few media players I tried could not handle the caf outputs, the compilation requires a patch, and the alac bug tracker isn't/wasn't usable.

---

### Post by qyot27 on 2011-10-30
> **Bachstelze said:**
> *EDIT:* ALAC is the only lossless audio codec that is supported in .mp4 files (at least as defined by the standard), so if you want a compatible .mp4 file with a lossless soundtrack, ALAC is your only choice. Also I am not sure how good the libavcodec implementation of ALAC encoding is, but if it's like FAAC for AAC, it basically sucks, so if someone wants to encode on Linux a lossless soundtrack for a .mp4 file, this is definitely good news.
Actually, the MPEG-4 standard defines both ALS and SLS as approved lossless formats, and both were published in 2006.  ALAC is a *de facto* standard (and first appeared in 2004), and if I understand [this chart](http://www.mp4ra.org/codecs.html) correctly, ALAC has to be put into a private stream rather than a registered one, lending some credence to the idea that MPEG hasn't officially updated the standard to include it*.  *De facto* because, well, good luck finding any sizable amount of ALS or SLS streams, even through FFmpeg has an ALS decoder.

*the relevance of this is fairly moot, though; the MP4 container was based on Quicktime's native MOV container, so in theory Apple could shove anything MOV can use into MP4 and it would be at least somewhat kosher.

Being that ALAC is lossless, as long as an implementation is correct, then it won't perceptually suck the way that codecs for lossy formats can.  It would mainly be down to compression ratio and/or speed balance, since data integrity and sound quality would be non-issues.




In any case, it's never bad to have another option.  There's several other non-FLAC lossless codecs that do get use (most notably TTA, but TAK, WavPack, APE, and others have representation too), and unless Apple plans on making ALAC-encoded tracks available through iTunes, that 'limited use' thing will probably end up applying to it as well.

I will note that I have seen at least one or two artists (or choice of distribution site) offering ALAC versions of their stuff online, but I also want to say they offered FLAC alongside it - FLAC for pretty much everyone, and ALAC for those with iDevices I guess.

---

### Post by krapp on 2011-10-30
> **dpny said:**
> Apple's a hardware company. They make almost no money from software.

Closed source software keeps their users tied to their hardware. That's the Apple mantra, as it has always has been.

---

### Post by dpny on 2011-10-31
> **krapp said:**
> Closed source software keeps their users tied to their hardware. That's the Apple mantra, as it has always has been.

Tied?

People choose to use the software and hardware because they like it. There are no victims on this scenario.

---

### Post by gsmanners on 2011-10-31
> **dpny said:**
> People choose to use the software and hardware because they like it.

Which is precisely why [Steve Jobs stabbed the clone market in the back]("http://en.wikipedia.org/wiki/Macintosh_clone#Jobs_ends_the_official_program"). :P

---

### Post by krapp on 2011-10-31
> **dpny said:**
> Tied?

People choose to use the software and hardware because they like it. There are no victims on this scenario.

Uh you're the only one talking about victimhood here. I quite enjoy the role of Linux fundamentalist, but I wasn't playing that here. Apple's software is top notch. Their hardware is overpriced. Limit use of software to hardware: overpriced hardware is guaranteed to sell. Otherwise you're left with a very paradoxical portrait of consumers.

---

### Post by dpny on 2011-10-31
> **krapp said:**
> Otherwise you're left with a very paradoxical portrait of consumers.

Not paradoxical at all: the value is in the integration of hardware and software.

---

### Post by krapp on 2011-10-31
Well value is an interesting and long discussion, but let's just remark that Apple by some sleight of hand (never mind what it is here, though I'd be happy to elaborate elsewhere) has managed to convince people that bargains, that old favorite of America, are no longer desired.

---

### Post by dpny on 2011-10-31
> **krapp said:**
> Well value is an interesting and long discussion, but let's just remark that Apple by some sleight of hand (never mind what it is here, though I'd be happy to elaborate elsewhere) has managed to convince people that bargains, that old favorite of America, are no longer desired.

No sleight of hand: stuff which just works is a value. Money is not a deciding factor for everyone.

---

### Post by Legendary_Bibo on 2011-10-31
> **krapp said:**
> Well value is an interesting and long discussion, but let's just remark that Apple by some sleight of hand (never mind what it is here, though I'd be happy to elaborate elsewhere) has managed to convince people that bargains, that old favorite of America, are no longer desired.

Someone wants an Apple product, therefore they value it, yeah Apple computers might be a bit overpriced, so what? It's someone else's decision, and their choice to buy and love Apple products. Everyone develops a brand loyalty for everything. I mean do you always get bread from a certain company, do you like certain restaurants that you repeatedly go to? Brand loyalty is everywhere, it's what people like, and it's their choice. Some people value different things than you, some people care to look at the source code of everything running through their CPUs, and some people just want to boot up their computer and look at funny pictures of cats or whatever. Isn't shoving the concept of "software freedom" down other people throats just as evil as the doings of corporations it claims to be fighting?

---

### Post by krapp on 2011-10-31
Oh boy. This little exchange went from my suggesting the absence of a necessity to keep ALAC closed, to my citing an obvious example (in fact one that gsmanners also used), to accusations that I'm somehow calling Apple's users victims, and now I'm told I'm shoving something down someone's throat.

---

### Post by Thewhistlingwind on 2011-10-31
> **krapp said:**
> Oh boy. This little exchange went from my suggesting the absence of a necessity to keep ALAC closed, to my citing an obvious example (in fact one that gsmanners also used), to accusations that I'm somehow calling Apple's users victims, and now I'm told I'm shoving something down someone's throat.

I have to agree. All you said was that this was a moot subject. (Which I agree with somewhat, however ALAC is important to a degree for Linux to support apple devices.) 

You said that, and are now being batted with concepts like free choice and different requirements. Which your initial post had nothing to do with.

---

### Post by Legendary_Bibo on 2011-10-31
> **krapp said:**
> Oh boy. This little exchange went from my suggesting the absence of a necessity to keep ALAC closed, to my citing an obvious example (in fact one that gsmanners also used), to accusations that I'm somehow calling Apple's users victims, and now I'm told I'm shoving something down someone's throat.

I never said you were shoving your values down people's throats.

---

### Post by Thewhistlingwind on 2011-10-31
> **Legendary_Bibo said:**
> I never said you were shoving your values down people's throats.

> **Legendary_Bibo said:**
>  Isn't shoving the concept of "software  freedom" down other people throats just as evil as the doings of  corporations it claims to be fighting?

I think that first statement may need emphasis in some parts.

---

### Post by Legendary_Bibo on 2011-10-31
> **Thewhistlingwind said:**
> I think that first statement may need emphasis in some parts.

It wasn't directed at anyone.

---

### Post by krapp on 2011-10-31
Thanks whistling, much appreciated!

Now I will echo someone else's post (I'm too lazy to quote them but they know who they are) and say the more open the better! So all in all, we are, speaking absolutely, happy when the enemies of open source open their source.

---

### Post by Legendary_Bibo on 2011-10-31
> **krapp said:**
> Thanks whistling, much appreciated!

Now I will echo someone else's post (I'm too lazy to quote them but they know who they are) and say the more open the better! So all in all, we are, speaking absolutely, happy when the enemies of open source open their source.

Absolutely.

---

### Post by Thewhistlingwind on 2011-10-31
> **krapp said:**
> 
Now I will echo someone else's post (I'm too lazy to quote them but they know who they are) and say the more open the better! So all in all, we are, speaking absolutely, happy when the enemies of open source open their source.

I audibly cheered when I read the headline. So I'm not exactly unimpressed. I'm very happy that this has happened for multiple reasons. However, I still think that iOS should support FLAC OOTB. 

There IS a mit-style licensed implementation of FLAC, right?

EDIT: According to wikipedia, the main libraries are BSD.

---

