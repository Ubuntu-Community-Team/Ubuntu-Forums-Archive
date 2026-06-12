---
title: "Will there be a 6.06.2 release?"
date: 2006-11-30
forum: The Cafe
---

### Post by ahaslam on 2006-11-30
Hi,

The title says it all really. I was just wondering if there were any plans for this.

Tony.

---

### Post by greggh on 2006-11-30
I would say its almost a certainty given that 6.06 is a LTS (long term support release) and will be officially supported for 3 years on the desktop and 5 years on the server. It's only been out 5 months and we already have 6.06.1. Over the next few years I think we'll see 6.06.2 ,.3, .4 ...

---

### Post by PriceChild on 2006-11-30
I think that the main reason 6.06.1 was released was because of several flaws in the installer...

Who knows though :)

---

### Post by qalimas on 2006-11-30
I think you're right.  There was a bug in the installer (for me, it always added a blank proxy to apt, and would never work until I went in and blanked apt.conf).  This is gone in 6.06.1.

---

### Post by Oki on 2006-11-30
Do you know it there will be another LTS version after Dapper Drake? I like the idea of an stable OS (Edgy was to buggy for me).

---

### Post by daynah on 2006-11-30
Yes, there's going to be another LTS, but I don't believe it's Fiesty.

I'm apparently behind. What was the bug in the installer?

---

### Post by zachtib on 2006-11-30
> **PriceChild said:**
> I think that the main reason 6.06.1 was released was because of several flaws in the installer...

Who knows though :)

Even still, it would be nice for Canonical to release another point release of Dapper once or twice a year so that if someone does a fresh install, they won't have several months or even a few years worth of updates to install.

---

### Post by PriceChild on 2006-11-30
There was some MAJOR partitioning problems... not that there still isn't... as i found out at a LUG install day...

There will be another LTS when it is most suited.

---

### Post by kuja on 2006-11-30
> **daynah said:**
> Yes, there's going to be another LTS, but I don't believe it's Fiesty.

I'm apparently behind. What was the bug in the installer?
The next LTS will be Feisty+2

And apparently there was, but that's the past now isn't it? Said bug has been long since squashed.

---

### Post by Brunellus on 2006-11-30
> **kuja said:**
> The next LTS will be Feisty+2

And apparently there was, but that's the past now isn't it? Said bug has been long since squashed.
along with some others.  the 6.06.0 release's default i386 kernel did not play well with PCMCIA buses on some hardware, leaving me with no networking on one install.  Breezy's kernel did, as did a subsequent Dapper, so I ended up installing Breezy and dist-upgrading to dapper instantly.  

No big deal for me, as it was a secondary system, but these are the sorts of things that point releases for LTS distros are supposed to fix.  They fixed them, the point release is out there.  I am satisfied.

---

### Post by chaosgeisterchen on 2006-11-30
> **kuja said:**
> The next LTS will be Feisty+2


I thought it was this way round:

One rather experimental release.
One release, developing the innovations towards stability.
One long time support release
One rather...

---

### Post by madmetal on 2006-11-30
since dapper is supported for 3 years desktop and 5 server i think the next LTS release will be just before support ends..

---

### Post by greggh on 2006-11-30
I remember reading somewhere that LTS releases will be every 4 releases. Which would indeed make Feisty+2 the next LTS.

---

### Post by justin whitaker on 2006-11-30
I'd like to see:

LTS1
Bleed
Triage (bug fix)
LTS Update (features update from Bleed)

---

### Post by Oki on 2006-11-30
Good to hear that they will realise another LTS version after Drapper Drake:-D I guess I will try Feisty as I did with Edgy. After being a software junky I have settled with applications that works, FF1.5 is good, no need for 2.0. 

Do you know if Feisty will be as &#8220;Edgy&#8221; as &#8230; Edgy?

---

### Post by PriceChild on 2006-11-30
Let me clear this up.

[B]THERE IS NO SCHEDULE FOR LTS RELEASES.

[/B]When development on integral parts of the system, such as gnome reach a plateau after huge advancements (such as compositing or KDE4 etc.) that they are considered "stable", then there will be choices made over whether to make that release LTS.

These things aren't predictable, It could be feisty +1, feisty +2, or even feisty +3.... who knows.

Pricey

---

### Post by PriceChild on 2006-11-30
> **Oki said:**
> Do you know if Feisty will be as “Edgy” as … Edgy?My personal experience makes me think that Edgy is more stable than Dapper.

However I know that this isn't true for everybody, there have been MANY regressions.

I'm guessing that feisty will be more stable across the board though... Edgy was "edgy".

---

