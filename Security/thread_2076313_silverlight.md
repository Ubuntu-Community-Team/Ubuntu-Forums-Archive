---
title: "silverlight"
date: 2012-10-25
forum: Security
---

### Post by mike acker on 2012-10-25
a page i was reading  on geekwire asks for the MSFT plug-in *silverlight*

although I  think MSFT software is probably not maliscious *per se* still there is the question: what all doors and paths does that thing open -- and who uses them and for what ?

we know that many marketing people view electronic computing devices as their tools for market research, and arogate to themselves the privilege of running their market research tools on every computer they can connect to .

not all of us accept this concept ...

do we have any info on MSFT Silverlight ?

---

### Post by deadflowr on 2012-10-25
Silverlight is kind of like Flash.
It's Microsoft's in-house variant of sorts, so like flash, as a closed source plugin, it too probably has all kinds of holes.
Fortunately, or unfortunately, Silverlight does not run in Ubuntu or linux(It kind of does in wine, but as of now only older versions). to run silverlight in linux you need the open-source(open-source being used relatively loosely) variant Moonlight.

---

### Post by mike acker on 2012-10-26
> **deadflowr said:**
> Silverlight is kind of like Flash.
It's Microsoft's in-house variant of sorts, so like flash, as a closed source plugin, it too probably has all kinds of holes.
Fortunately, or unfortunately, Silverlight does not run in Ubuntu or linux(It kind of does in wine, but as of now only older versions). to run silverlight in linux you need the open-source(open-source being used relatively loosely) variant Moonlight.

yep, time for me to look into setting up AppArmor for my browser. i think someplace here we have a starter file for that. it had been my plan to simply do sensitive/critical browser tasks under my other user id but that may not be the best choice

---

### Post by CharlesA on 2012-10-26
I didn't think you could install Silverlight (or Moonlight, or whatever it's called) on a *nix box. Maybe that was just related to Netflix.

Personally, if a website said it required silverlight, I wouldn't even bother using that site. We've already got flash to deal with and HTML5 is around, but still not a drop-in replacement for flash.

---

### Post by Frogs Hair on 2012-10-26
Moonlight is available, but it is not being developed anymore and there have been no updates since April 2011. It only works certain websites though.     [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by directhex on 2012-10-29
Silverlight is a browser plugin from Microsoft , allowing web authors to write Flash-like content in C# and VB.NET. The design of it enforces strict sandboxing to keep your PC safe (much like every browser plugin promises, and often fails to deliver on). The biggest users of it are streaming video sites like LoveFilm or Netflix, who use Silverlight with Microsoft DRM.

Moonlight was an Open Source re-implementation of Silverlight for Linux, without the DRM parts, done by a team at Novell, with support (including some Open Source code) from Microsoft. However, that team no longer works at Novell, and there are no longer any developers working on Moonlight as of more than a year ago.

Silverlight is "safe" (at least as safe as Flash, but with a much better security record), but Moonlight is dead, and as such, you should avoid sites using Silverlight.

---

