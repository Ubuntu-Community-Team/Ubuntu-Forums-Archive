---
title: "Even apple can't implement openxml correctly"
date: 2007-08-16
forum: The Cafe
---

### Post by vexorian on 2007-08-16
Even apple - Microsoft's best friend and second most important supporter of naming OpenXML, the proprietary format an Open standard - cannot implement it correctly.

[http://www.sutor.com/newsite/blog-open/?p=1796](http://www.sutor.com/newsite/blog-open/?p=1796)

> Apple is allowing users to download a free trial version of iWork ‘08 that works for 30 days. Evidently its support for OOXML is read-only, and not complete at that. This means, to be explicit, that you can read some OOXML documents but not write them out again.

---

### Post by popch on 2007-08-16
> **vexorian said:**
> Even apple - Microsoft's best friend and second most important supporter of naming OpenXML, the proprietary format an Open standard - cannot implement it correctly.

[http://www.sutor.com/newsite/blog-open/?p=1796](http://www.sutor.com/newsite/blog-open/?p=1796)

Meaning that MS can implement it correctly and completely? And who is going to decide wether it is done correctly and completely?

---

### Post by starcraft.man on 2007-08-16
> **popch said:**
> Meaning that MS can implement it correctly and completely? 
Nope just implies that all those Apple fans overreacted to reports that iWorks supported OOXML.

> 
And who is going to decide whether it is done correctly and completely?
I believe it's fairly safe to say that with respect to office formats being able to read _and_ write are two prime abilities that need implementing in order to be "correctly and completely [implemented]". Other things can be added, but without read/write it is fairly useless.

Oh and this post based on the assumption that said fact iWorks not implementing OOXML right is correct. The link isn't working for me and I don't think I saw any other mention elsewhere.

---

### Post by vexorian on 2007-08-16
I think it was offline for some time, but it is back for me.

better link: [http://www.bioneural.net/2007/08/11/iwork-08-and-support-for-open-xml/](http://www.bioneural.net/2007/08/11/iwork-08-and-support-for-open-xml/)

---

### Post by Mathiasdm on 2007-08-16
Who says it's because Apple can't implement it correctly? I'm pretty sure *most* of the OpenXML spec is straightforward enough to implement (both reading and writing). The few 'do things like Word Version XX did it' parts shouldn't influence implementing read/write support for other parts of the spec (since it's XML).

How about this idea (just an idea): Apple isn't implementing write support for OpenXML, because they want to push their own format.

---

### Post by LaRoza on 2007-08-16
> **Mathiasdm said:**
> 
How about this idea (just an idea): Apple isn't implementing write support for OpenXML, because they want to push their own format.

Why not use Open Formats?

---

### Post by Mathiasdm on 2007-08-16
> **LaRoza said:**
> Why not use Open Formats?

They (Apple) have their reasons for using closed formats. For one, it makes it easier to tie the user to their own office suite.

Oh, and OpenXML (even though it does have its flaws) is at least a good step in the right direction. It might contain some bad parts, but it's certainly better than the old formats!

---

### Post by Quillz on 2007-08-16
I didn't know Apple has its own formats when it comes to iWork. Usually, you just save documents as .rtf, or .doc if you intend to share it with Word users.

---

### Post by RomeReactor on 2007-08-16
> **Mathiasdm said:**
> Who says it's because Apple can't implement it correctly? I'm pretty sure *most* of the OpenXML spec is straightforward enough to implement (both reading and writing).

Try reading the 6,000 page Office Open XML specification.

---

### Post by LaRoza on 2007-08-16
> **Mathiasdm said:**
> They (Apple) have their reasons for using closed formats. For one, it makes it easier to tie the user to their own office suite.

Oh, and OpenXML (even though it does have its flaws) is at least a good step in the right direction. It might contain some bad parts, but it's certainly better than the old formats!

I was referring to users using Open Formats. I never used a Mac long enough to get familiar, what is their Office Suit like?

OpenXML is better than the old formats, smaller too.

---

### Post by popch on 2007-08-16
> **LaRoza said:**
> I never used a Mac long enough to get familiar, what is their Office Suit like?

I, for one, don't know. I use Open Office on the Mac OS X.

---

### Post by vexorian on 2007-08-16
> **Mathiasdm said:**
> They (Apple) have their reasons for using closed formats. For one, it makes it easier to tie the user to their own office suite.

Oh, and OpenXML (even though it does have its flaws) is at least a good step in the right direction. It might contain some bad parts, but it's certainly better than the old formats!
it can't be much better  than the old formats considering it is just a dump of the old binary formats into xml...

---

### Post by Mathiasdm on 2007-08-16
> **RomeReactor said:**
> Try reading the 6,000 page Office Open XML specification.

I know it's a huge amount of pages ;) Perhaps 'straightforward' wasn't the word I was looking for.
I meant it was perfectly possible to implement reading + writing for most of the spec. Since Apple managed to implement reading, it's not exactly to hard to implement writing too.

---

### Post by vexorian on 2007-08-16
it didn't implement reading entirely well either.

---

### Post by Mathiasdm on 2007-08-16
Well, all I was saying was that there could be multiple reasons for that (not just the way OpenXML works, or the complexity of the spec). Just saying ;)

---

### Post by LaRoza on 2007-08-16
> **popch said:**
> I, for one, don't know. I use Open Office on the Mac OS X.

I use OpenOffice and Abiword on Windows and Linux, although I do have Office 2007, I don't use it.

---

### Post by Hendrixski on 2007-09-01
Apple isn't the only one.  Apparently NOT EVEN OFFICE 2007 implements it, at least not in the format that it was submitted to the ISO.

The problem is worse than that though, OOXML is like a "gateway drug" that sucks you into Microsofts stack of proprietary applications and services.  Their stack uses only OOXML to communicate, so only companies who can get a license from Microsoft can join the fun, meaning once you use MS Office you're locked into only using services from Microsoft because nobody else can communicate with you.
Read more about it on this thread: [http://ubuntuforums.org/showthread.php?t=540016](http://ubuntuforums.org/showthread.php?t=540016)

---

### Post by jomiolto on 2007-09-02
Not only is OOXML specification 6,000 pages long, but it is also not very well written, and as such I wouldn't be surprised if Apple is having trouble implementing it.

BSI (British Standards Institution) Group has a nice wiki of comments on the OOXML specification that lists literally hundreds of errors in the specification. You can find it here: [http://www.xmlopen.org/ooxml-wiki/index.php/DIS_29500_Comments]("http://www.xmlopen.org/ooxml-wiki/index.php/DIS_29500_Comments")

Some of those errors are just typos and other minor things, but there are a lot of bigger issues too, including stuff that is not really documented at all!

For example: (from [http://www.xmlopen.org/ooxml-wiki/index.php/2._WordprocessingML_Reference_Material#2.15.1.28_.5Bp1158.2C_13....5D]("http://www.xmlopen.org/ooxml-wiki/index.php/2._WordprocessingML_Reference_Material#2.15.1.28_.5Bp1158.2C_13....5D"))

> This algorithm description fails to specify the encoding of the input password. Presumably it is Unicode, but in what encoding? UTF-16BE? UTF-16LE? UTF-16 with a BOM (Byte Ordering Mark)? The described algorithms make use of byte-level manipulations which depend on the machine architecture (big endian versus little endian). So it is necessary that all byte ordering assumptions be made explicit.

Quite a "standard", eh?

---

### Post by Sluipvoet on 2007-09-02
I not going to defend Apple or MicroSoft, but aren't you guys too quick to make your judgements.
Neither kWord nor Abiword could immediatly implement OpenDocument correctly. At the start of it only OpenOffice(an its siblings Neo-/StarOffice) could implement OpenDocument
Nowadays kWord has improved(still haven't checked new versions of AbiWord), but I still wouldn't call it perfect.
And since it is a free trial version of iWork it think they deserve some time to improve their OOxml implementation.

---

