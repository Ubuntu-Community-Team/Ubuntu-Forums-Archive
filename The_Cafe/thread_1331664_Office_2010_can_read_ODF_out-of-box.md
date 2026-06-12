---
title: "Office 2010 can read ODF out-of-box"
date: 2009-11-19
forum: The Cafe
---

### Post by piousp on 2009-11-19
A friend just downloaded the MS Office 2010 demo. I remember i read somewhere that Microsoft was going to make a update to Office 2007 so it could read/write in ODF format.

SO, we tried to save as an ODF document and it can (at least now[It does give a weird warning that could scare normal users tho :p])
And our second test, was to give a natural ODF from oo.org (an ODT) and the result was nice: It opened it like it was a native format!

What do you think??

---

### Post by Tristam Green on 2009-11-19
This just in:  MS Office 2007 can open and ODT files also.

---

### Post by piousp on 2009-11-19
> **Tristam Green said:**
> This just in:  MS Office 2007 can open and ODT files also.

:o i thought it couldn't, at least by default

---

### Post by blueshiftoverwatch on 2009-11-19
This is pretty cool news, why would MS do something like this though?

---

### Post by Tibuda on 2009-11-19
> **blueshiftoverwatch said:**
> This is pretty cool news, why would MS do something like this though?

anti-trust decision

---

### Post by earthpigg on 2009-11-19
any word on OO.o and perfect rendering of .docx?

---

### Post by froggyswamp on 2009-11-19
People forget Microsoft is a vivid embrace-extend-extinguish player.

In Office 2007 it only supports odf partially (with whatever excuses), and if you save the file with office 2007 you will likely lose some settings - read my first sentence or google for details.

---

### Post by siimo on 2009-11-19
> **froggyswamp said:**
> People forget Microsoft is a vivid embrace-extend-extinguish player.

In Office 2007 it only supports odf partially (with whatever excuses), and if you save the file with office 2007 you will likely lose some settings - read my first sentence or google for details.

FUD.  The ODF project is open source. [http://odf-converter.sourceforge.net](http://odf-converter.sourceforge.net)

---

### Post by Tomone on 2009-11-21
> **earthpigg said:**
> any word on OO.o and perfect rendering of .docx?

Last I've seen, .doc isn't rendered the same in both MS Office and OO.o, so I'd guess that .docx wouldn't be either.
Does anyone know how close odf looks between MS and OO.o?

---

### Post by doorknob60 on 2009-11-21
> **Tristam Green said:**
> This just in:  MS Office 2007 can open and ODT files also.

Yeah, it can (at least with SP2), but not perfectly. For example, I opened an ODF spreadsheet and all the formulas were gone and just replaced with the last used numbers *facepalm* But again, people don't like to update their system, so even if they have Office 2007, there's a good chance they don't have SP2. And don't leave out the many people that still use Office 2003. Hopefully ODF eventually becomes a more widely accepted format though, and this is a step in the right direction.

---

### Post by MalleRIM on 2010-04-26
> **siimo said:**
> FUD.  The ODF project is open source. [http://odf-converter.sourceforge.net](http://odf-converter.sourceforge.net)
No FUD. That link is the ODF converter plugin. MS-Office's native support for ODF is a different thing.

---

### Post by gnomeuser on 2010-04-26
> **blueshiftoverwatch said:**
> This is pretty cool news, why would MS do something like this though?

Profit is driven by customer demand. Many organizations and governments are now standardizing on either OOXML, OpenDoc or both. To serve these customers and continue to sell them Microsoft Office licenses (and by extension Windows licenses) they need to support both formats.

While support may not be perfect for either format right now, be sure to see this polished with updates and service packs as issues are detected. 

Nothing nefarious at all, just plain old profit and providing the best possible experience they are capable of.

---

### Post by MalleRIM on 2010-04-26
Does anyone know anything on the quality of the implementation? I can't imagine, Microsoft is providing a fully functional, standards compliant implementation of ODF.

---

### Post by BrokenKingpin on 2010-04-26
I think this is great. I use OpenOffice for the most part, but a lot of the people I know use MS Office, so it is nice I can send them documents and they can open them without much hassle.

---

### Post by madjr on 2010-04-26
i would love for an ODT/ODF document to pop-up a message and a link to download an ODT compatible reader.

i could send my odt's to anyone and they would be prompt to download a reader (or 1 click DL). that would be cool viral marketing for OOo and/or abiword :)

problem solved, no need to wait on MS to implement crappy odf support, that they can sabotage whenever

would also solve the problem with lots of users still using Office 2003

---

### Post by Khakilang on 2010-04-26
I se a lot of my friend and customer are using OpenOffice. Maybe MS thought they have loss some market share and try to make up for it. Nevertheless its a good thing.

---

### Post by skymera on 2010-04-26
I read somewhere that Oracle was going to start charging other software vendors $90 to use the ODF format.

Is this true?

---

### Post by Danny Dubya on 2010-04-26
> **skymera said:**
> I read somewhere that Oracle was going to start charging other software vendors $90 to use the ODF format.

Is this true?
Barely. What they're charging $90 for is Sun's ODF plugin that worked with Office 2003, since MS never backported ODF import/export filters to it. And the plugin is only available in packs of 100 licenses or something... so I'm guessing it really costs $9,000.

---

### Post by legolas_w on 2010-04-26
Hi,

does MS office 2010 works in Ubuntu? either in 9.10 or 10.04?

Thanks.

---

### Post by clanky on 2010-04-26
> **legolas_w said:**
> Hi,

does MS office 2010 works in Ubuntu? either in 9.10 or 10.04?

Thanks.

Hi Legolas, it is possible to run office in Wine, but it is far from perfect, although now that MS Office supports open document format and O_Oo can read .docx format you can use O_Oo to read and edit anything produced in MS Office and MS office on a windows PC so there is really no need to run MS Office in Linux.

---

### Post by gnomeuser on 2010-04-26
> **MalleRIM said:**
> Does anyone know anything on the quality of the implementation? I can't imagine, Microsoft is providing a fully functional, standards compliant implementation of ODF.

Your mistake is assuming that fully functional and standards compliant aren't in conflict when it comes to OpenDoc.. which is just happens to be. If you implement according to the spec you you will find several wonderfully undefined areas which require you to read the OpenOffice.org source code (which very likely due to license and legal concerns isn't an option for Microsoft) to figure out which is the right way to do things.

OpenDoc is basely a horribly written standard, it really is. This is why some documents will not interoperate correctly currently. Microsoft implemented OpenDoc to the letter and it still fails which deserves as a suitable testament to the horridness of OpenDoc as a standard.

A similar implementation of OOXML would have fared far better simply due to the extensive effort that went into writing that specification.

I would like to take this time to thank all the activists for taking their time to mix their politics into a decision which should have been based solely in technological superiority. I realize your intentions are good, but as the proverb warned us all.. that path let to where we are now.. hell.

---

### Post by legolas_w on 2010-04-27
> **clanky said:**
> Hi Legolas, it is possible to run office in Wine, but it is far from perfect, although now that MS Office supports open document format and O_Oo can read .docx format you can use O_Oo to read and edit anything produced in MS Office and MS office on a windows PC so there is really no need to run MS Office in Linux.

The main reason behind using MS office is its very powerful grammar and spelling checker which easily beat OO.org spelling and grammar checker.

Thanks.

---

### Post by MCVenom on 2010-04-27
> **legolas_w said:**
> The main reason behind using MS office is its very powerful grammar and spelling checker which easily beat OO.org spelling and grammar checker.

Thanks.
Then run it on a Mac or Windows VM :P

...Or you could take supplementary grammar lessons so the checks are unneeded :lolflag:

---

