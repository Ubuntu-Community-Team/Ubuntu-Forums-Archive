---
title: "Macros"
date: 2009-09-03
forum: The Cafe
---

### Post by Leovinus on 2009-09-03
Hi there.  I've been trying to convince people of just how good ubuntu is, I get all sorts of arguments from them about why they have to use windows, the only one I can't counter is the issue of visual basic in ms office software.  To this end I was wondering if anybody knows if there is any way of writing macros in python and getting them to run in ms office, or if VB macros can be converted easily to python or be made to run in open office?

---

### Post by marchwarden on 2009-09-03
Can I ask, why not port them over to OpenOffice.org BASIC?

---

### Post by megamania on 2009-09-03
> **marchwarden said:**
> Can I ask, why not port them over to OpenOffice.org BASIC?
Can I ask how to do that?

I have a program entirely written in visual basic for Excel, and I'd love to have it working under Calc...

---

### Post by niteshifter on 2009-09-03
> **megamania said:**
> Can I ask how to do that?

I have a program entirely written in visual basic for Excel, and I'd love to have it working under Calc...

See [this]("http://documentation.openoffice.org/HOW_TO/various_topics/VbaStarBasicXref.pdf") (openoffice.org/../VbaStarBasicXref.pdf)

As to using Python for macros:

See [here]("http://udk.openoffice.org/python/scriptingframework/index.html") and [here]("http://wiki.services.openoffice.org/wiki/Extensions_development_python").

Macros in either MSO or OOo can be divided into two 'levels': Simple click and keystroke recorders and 'for-real' programming. The built in help of OOo covers the former, for the latter openoffice.org (and oooforum.org) are very helpful resources. Getting to know UNO is essential for 'advanced' macro work - you'll find everything you'll ever want to know in the openoffice.org domain :) 

That's not to knock this forum, just sayin' go where ya can get it from the horse's mouth ...

---

### Post by megamania on 2009-09-03
> **niteshifter said:**
> 
That's not to knock this forum, just sayin' go where ya can get it from the horse's mouth ...
Thanks. 

On various occasions I had taken a look at the ooo website, and as far as I know there's no quick way to get complex visual basic applications to work.
A major rewriting is needed, and that's why I asked HOW to port the applications as a quick solution to the problems raised by the original poster.

---

### Post by koenn on 2009-09-03
> **megamania said:**
> Thanks. 

On various occasions I had taken a look at the ooo website, and as far as I know there's no quick way to get complex visual basic applications to work.
A major rewriting is needed, and that's why I asked HOW to port the applications as a quick solution to the problems raised by the original poster.
thye answer is in your question : you have to rewrite them.

You'll probably be able to follow roughly the same logic as in your VBA "program", but as to the specific statements, in windows VBA you'll be using calls to objects and methods that are specific to the Windows environment and/or to MS Office Applications, you can't expect that OOo knows how to handle those or automatically replace them. You'll have to do that yourself.

---

