---
title: "Why is Mplayer such a big legal deal?"
date: 2006-06-14
forum: The Cafe
---

### Post by scwizard on 2006-06-14
From wikipedia:
"Most video and audio codecs are supported natively through the libavcodec library of the FFmpeg project. For those codecs where no open source decoder has been implemented yet MPlayer relies on binary codecs. It can even use Windows DLLs directly with the help of a DLL loader forked from avifile (which itself forked its loader from the Wine project).

The combination of CSS decryption software, Windows codec use, implementation of codecs covered by software patents, and the GPL places a fully-functional MPlayer in the legal bind shared by most open source multimedia players. In the past MPlayer used to include OpenDivX, a GPL-incompatible decoder library. For these reasons MPlayer is not preferred by most linux distributions with a strong commitment to free software despite its functionality. For example, it is not supported by the Debian GNU/Linux distribution."

That gives me some info, but I desire more. OpenDivX according to this is not compatable with the GPL. How does this make Mplayer so incredibly evil? Doesn't some other non GPL compatable stuff come packaged with ubuntu?

One of the reason the huge amount of fuss puzzles me is because Mplayer comes by defuault with [eLive](http://www.elivecd.org/). But then again eLive is maintained by pretty much a single person.

I'm also wondering. If the people who distribute Mplayer are legally allowed to do so, then why aren't other people allowed to distribute Mplayer packaged with a bunch of other things?
Are they even allowed to legally distribute Mplayer? If I live in the US and download Mplayer is that just as bad as if I had downloaded a pirated copy of windows?

Is Mplayer in violation of the DMCA?
Is the DMCA also the reason why ubuntu can't ship with stuff like ndiswrapper?

Is there something about how Mplayer can only be used for personal use, and because Ubuntu is tied to a organization distributing it wouldn't be personal use?

And finally could a little thing explaining why ubuntu can't use a better media player be stickied or put in the FAQ.
(please don't anyone try to tell me that gstreamer is the best media player out there. It can't even play DVDs easily...)

---

### Post by bruce89 on 2006-06-14
Mplayer is in multiverse though, like ndiswrapper.

---

### Post by Engnome on 2006-06-14
DMCA is a huge thorn in the eye for anyone trying to develop OSS alternatives. It makes it illegal to break a content copy protection systems. For example the protection on dvd discs are easily broken but doing so is illegal. You cant reverse engineer it and make a compatible driver/program/codec. If youre in the US that is, here in Sweden no problem :D

---

### Post by scwizard on 2006-06-14
[QUOTE=Engnome]DMCA is a huge thorn in the eye for anyone trying to develop OSS alternatives. It makes it illegal to break a content copy protection systems. For example the protection on dvd discs are easily broken but doing so is illegal. You cant reverse engineer it and make a compatible driver/program/codec. If youre in the US that is, here in Sweden no problem :D[/QUOTE]
So the primary reason that Mplayer isn't included is because of the DMCA, right?

But Canonical is headquartered in europe though? If they were to include Mplayer what would that prevent them from doing? Would they still be allowed to ship to the US? Would it break some treaty?

---

### Post by mostwanted on 2006-06-14
Yeah, as a rule of thumb all those nasty anti-competitive rules for software are only valid for residents of the USA, so if you live somewhere else there are no legal issues.

Unfortunately, in the case of the binary codecs supplied by MS, they qualify is intellectual property in many countries; this isn't a software patent issue, but a piracy issue. Until there are freely available codecs for those formats (the Microsoft ones) it's just as illegal in Europe as it is in the US.

Circumventing DRM like CSS protection for DVDs is not legal in all countries either, but I know it is in Scandinavia so I haven't any worries myself.

---

### Post by Lunixfanboy on 2006-06-14
Mplayer using just the ffmpeg and only open codecs is freely distributable. The problem arises when the w32codecs package is part of the equation. Mplayer comes from Hungary, where things are a little less restrictive than here in the US of A. The w32codecs package includes MANY codecs which are not allowed by their owners to be redistributed at all. Quicktime, Microsoft WMA and WMV9, RealPlayer, etc., all have onerous restrictions on WHO gets the codecs and how (want WMA/WMV9, license them on RAND terms from Microsoft or buy WIndows).  THAT is the problem. Most folks get both mplayer AND w32codecs to bring Mozilla up to an Insecure Exploder capability to play embedded video, thus violating redistribution restrictions.

---

### Post by poofyhairguy on 2006-06-14
[QUOTE=scwizard]
But Canonical is headquartered in europe though? If they were to include Mplayer what would that prevent them from doing? Would they still be allowed to ship to the US? Would it break some treaty?[/QUOTE]

If Ubuntu did something to break U.S. law then Mark or any of the Ubuntu developers could be arrested as soon as they enter the U.S. at any point. That is unreasonable.

No one wants what this guy has gone through:

[http://en.wikipedia.org/wiki/Dmitri_Sklyarov](http://en.wikipedia.org/wiki/Dmitri_Sklyarov)

So therefore Ubuntu most please the lowest common denominator legally (which is my country in this case).

(For those who will be quick to reply that historically the patents regarding codecs and the DMCA violations of using the locked codecs have never been enforced- you are correct. Warren of Mepis fame puts all the bad codecs in his distro and lives in the U.S. outside of a jail cell. The problem is that if Mepis (or Ubuntu) got really popular than the first thing the enemy would attack is this position. If Microsoft thought Mepis was a threat then Warren would be in jail before the sun fell- I don't know how he gets good sleep.)

---

### Post by The Cosmic Hobo on 2006-06-15
[QUOTE=poofyhairguy]No one wants what this guy has gone through:[/QUOTE]
And then, of course, there's ["DVD Jon" Johansen]("http://http://en.wikipedia.org/wiki/DVD_Jon") and DeCSS...

---

### Post by Mr.Auer on 2006-06-15
Its like its always been here on Planet Earth: The bad guys with already huge piles of influence, money and the leading market position impose their own "standards" on others thru wide-spread pushing of their technologies...Then prevent others from interoperating thru lobbying the lawmakers, who also like to listen to the sound of "Ca-Ching" of dollars from the lobbyists in their pockets rather than the good of the common people who they are supposed to serve..Ah what a big lie!

Now dont get me started on fractional banking, the federal reserve aka The Biggest Swindle ever aka Imaginary Paper Money..And so on..Our world is ruled by mega-rich bankers who have consolidated power thru being able to control all currencies and global economic systems. Its sad, but thats how it is presently. All these lesser woes, like DMCA and codec licensing issues come from this ;)

---

### Post by The Cosmic Hobo on 2006-06-15
[QUOTE=Mr.Auer]Now dont get me started on fractional banking[/QUOTE]
Hmm... isn't that how Richard Pryor's character made his fortune in Superman III, by collecting all the unused fractions of cents off his colleagues' salaries? ;)

---

### Post by scwizard on 2006-06-15
[i]No one wants what this guy has gone through:

[http://en.wikipedia.org/wiki/Dmitri_Sklyarov](http://en.wikipedia.org/wiki/Dmitri_Sklyarov)[/i]

Hmm... Why not? It would be good free publicity for OSS, and he won the case in the end. The more cases that are won, the harder it becomes to enforce the DMCA :)

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=scwizard]
Hmm... Why not? [/QUOTE]

A: Jail in any form for any amount of time sucks. Mark and the devs deserve better.

B: Giving Ubuntu the image of a "rebel" is a bad idea when Mark is trying to push Ubuntu into the enterprise.

C: It costs a lot of money (to pay lawyers and such) to win court cases and that money would be better used for development. We are not MS (with deep pockets) and the Ubuntu desktop needs work on far more things before we can worry about maybe wasting resources to make closed media files play by default.

D: Dmitri Sklyarov went to jail trying to help those with handicaps. That is far more noble than going to jail so that CNN clips will play in the browser.

E: Adobe found themselves out resourced in the long run last time. If the next battle was fought over codecs the opposition would have FAR greater resources. If Apple and MS worked together to stop the default mplayer from playing closed codecs they could blow more money on it in a week then Ubuntu gets for development in ten years. It is a case that is a certain loss.

F: Codecs aren't that important. Heck, for desktop linux adoption in general home users (who are usually the ones demanding these codecs) are not that important. What is important is pleasing large organizations that might switch over (say schools or large corporations). They need a better Openoffice/Evolution/etc. far more then they need to play media files. Heck for some, the lack of codecs is an advantage of Ubuntu- no employee time lost to porn or whatever.

---

