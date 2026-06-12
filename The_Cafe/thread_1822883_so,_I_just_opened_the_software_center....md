---
title: "so, I just opened the software center..."
date: 2011-08-11
forum: The Cafe
---

### Post by ninjaaron on 2011-08-11
... and beside the entry that says "provided by Ubuntu," there is a Fedora logo.

Anyone else seeing this? any thoughts?

edit:
Maybe this has to do with the update to faenza-icon-theme that I got today through the equinox PPA...

---

### Post by imortalninja161 on 2011-08-11
na i dont see it :/ btw POWER TO THE NINJAS !! lol

---

### Post by ninjaaron on 2011-08-11
> **imortalninja161 said:**
> POWER TO THE NINJAS !!

I dig. :cool:

---

### Post by zekopeko on 2011-08-11
> **ninjaaron said:**
> ... and beside the entry that says "provided by Ubuntu," there is a Fedora logo.

Anyone else seeing this? any thoughts?

What icon theme are you using? That particular Ubuntu logo was probably replaced in what ever icon theme you are using with the Fedora one.

---

### Post by ninjaaron on 2011-08-11
> **zekopeko said:**
> What icon theme are you using? That particular Ubuntu logo was probably replaced in what ever icon theme you are using with the Fedora one.

Faenza. I added that to the OP at about the same time you were posting this.

---

### Post by Dry Lips on 2011-08-11
LOL! I've got it as well!

---

### Post by zekopeko on 2011-08-11
> **Dry Lips said:**
> LOL! I've got it as well!

Somebody be trollin'!

---

### Post by Dry Lips on 2011-08-11
> **zekopeko said:**
> Somebody be trollin'!

Wot? The Faenza team you mean?

---

### Post by ninjaaron on 2011-08-11
werd.

---

### Post by danyc05 on 2011-08-11
I got it too... i just noticed it but I also just updated the package so maybe it was a mistake or something lol

---

### Post by Bandit on 2011-08-11
Looks like the Faenza Theme creater(s) have moved from Ubuntu to Fedora.. lol

---

### Post by el_koraco on 2011-08-11
maybe it's the mighty Upstream teaching Canonical a lesson for straying of The Path?

---

### Post by NightwishFan on 2011-08-11
Works fine here.

---

### Post by DangerOnTheRanger on 2011-08-11
I don't see the Fedora logo inside the USC on Lucid.

> **imortalninja161 said:**
> na i dont see it :/ btw POWER TO THE NINJAS !! lol
[QUOTE=ninjaaron;11140712]I dig. :cool:
[/QUOTE]

< Ditto.

---

### Post by Dry Lips on 2011-08-11
> **DangerOnTheRanger said:**
> I don't see the Fedora logo inside the USC on Lucid.
< Ditto.

Do you have the faenza icons installed, and have you added the PPA?
I also noticed that the icons were updated yesterday through the Update
manager.

---

### Post by ninjaaron on 2011-08-11
> **NightwishFan said:**
> Works fine here.Ack! except for the horrible typography that comes standard on all the communist distros!  My eyes are bleeding!!

> **el_koraco said:**
> maybe it's the mighty Upstream teaching Canonical a lesson for straying of The Path?

Straying from the path of boring into the path of awesome?

---

### Post by NightwishFan on 2011-08-11
[QUOTE=ninjaaron;11141365]Ack! except for the horrible typography that comes standard on all the communist distros!  My eyes are bleeding!!

What the bloody hell are you talking about?

---

### Post by ninjaaron on 2011-08-11
> **NightwishFan said:**
> 

What the bloody hell are you talking about?

The standard font rendering engine on Linux is FreeType2. It's not the best.  Ubuntu uses their own modified version of this engine which is better.  There is also another open source derivative called infinality-freetype2, which is better than Ubuntu's rendering for some things (depends on the font).  However, it contains some proprietary code (along with GLP code), so the more ideological distros don't have it in their repos, though you can always get it, of course.  Ubuntu's is all GLP, as far as I know, but nobody else uses it.  In addition, Fedora and Debian don't have hinting, sub-pixel smoothing, or antialiasing working by default (... they might have anti-aliasing... I don't recall...)

I'm sort of a freak for typography (and detail in general), so I'm hyper-sensitive to this stuff.  I spent a couple days trying to get the fonts to look right in Fedora.  When I saw the default fonts in Debian, I just lol'ed and wiped the partition.

---

### Post by ninjaaron on 2011-08-11
Just got this email from the developer:

> Thanks, its a mistake since I am using Fedora now to test Gnome Shell. Ubuntu Logo will be back in the next hours.
*-Matthew James*

---

### Post by Dry Lips on 2011-08-11
**@ninjaaron: **I'm glad it'll be sorted out. Nice one!

---

### Post by Spice Weasel on 2011-08-11
> **ninjaaron said:**
> In addition, Fedora and Debian don't have hinting, sub-pixel smoothing, or antialiasing working by default (... they might have anti-aliasing... I don't recall...)

They do.

[IMG]http://i.imgur.com/KvDSS.png[/IMG]

---

### Post by NightwishFan on 2011-08-11
Mine certainly has it. The font cantarell is supposed to look like this. Also Debian is democracy thank you very much.

---

### Post by el_koraco on 2011-08-11
> **ninjaaron said:**
> 
I'm sort of a freak for typography (and detail in general), so I'm hyper-sensitive to this stuff.  I spent a couple days trying to get the fonts to look right in Fedora.  When I saw the default fonts in Debian, I just lol'ed and wiped the partition.


Actually, Squeeze has the same libfreetype as Ubuntu, what they don't have is the patched libcairo package. The freetype patent is expired, so Debian is including it, you just need to correct the settings via dpkg and .fonts.conf. The problem is mostly in vague documentation, and the fact that the libcairo devs don't like the patched version themselves. Plus, I've seen quite a lot of font-freaks on Debian preferring the original version. 

The infinality .fonts.conf is somewhat different than Ubuntu's, so you need to do some manual tweaking, although I'm not that familiar with infinality, having used Fedora for a relatively short time.

---

### Post by ninjaaron on 2011-08-11
> **Spice Weasel said:**
> They do.

[IMG]http://i.imgur.com/KvDSS.png[/IMG]

looks like it.

---

### Post by ninjaaron on 2011-08-11
> **NightwishFan said:**
> Also Debian is democracy thank you very much.
Yeah yeah.  I know (more or less) about Debian's organisational model and I have a lot of respect for it.  On the other hand, I have no ideological  opposition to private property, even intellectual property, especially if the rights-holder is giving it away for free with a few choice rights reserved.  I'm a "whatever works" kind of guy, and I've always thought the more extreme Stallman types were more than a little nuts.  I'm more of a disciple of Linus where that kind of thing is concerned.


> **el_koraco said:**
> Actually, Squeeze has the same libfreetype as Ubuntu, what they don't have is the patched libcairo package. The freetype patent is expired, so Debian is including it, you just need to correct the settings via dpkg and .fonts.conf. The problem is mostly in vague documentation, and the fact that the libcairo devs don't like the patched version themselves. Plus, I've seen quite a lot of font-freaks on Debian preferring the original version.

I know it has freetype, but it doesn't have the patched versions that many people prefer.  I realize that some people like the older versions, though I cannot for the life of me figure out why.


Anyway, it was kinda a joke.  Of course, I do hate the font, but if NightwishFan thinks it looks good, he's perfectly entitled to his opinion.

P.S. I think I know how you can get faenza systray and action buttons without the rest of the theme.  I posted it in the screenshots thread.

---

### Post by NightwishFan on 2011-08-11
I know it was a joke I was just giving you a hard time. And I don't 'think' it's good I know it is. :)

---

### Post by el_koraco on 2011-08-11
> **ninjaaron said:**
>  
I know it has freetype, but it doesn't have the patched versions that many people prefer.  I realize that some people like the older versions, though I cannot for the life of me figure out why.


libfreetype is patched as well, it's libcairo that isn't. I know this, because I've spent like five hours trying to fix libcairo on #!, only to find out that it took the other packages from Debian, and libcairo from Ubuntu :lolflag:

Gonna goo check out your advice.

---

