---
title: "Copyright, piracy, codec n sourcecode... [how it works?]"
date: 2011-05-04
forum: The Cafe
---

### Post by inovarts on 2011-05-04
Hi guys,, 
Im just wondering about those copyright thing in software developing. And it led me to these question, hope somebody could help me here........ :p

1. When an opensource software developer, build a nice software **which is able to open** some format from proprietary software, do they need to pay some royalty to those proprietary software developer to get some license? (ie. gimp -> psd, libreoffice -> doc, blender -> 3ds, lwo)

2. (If the answer is "no need to pay") Whats the difference those format (doc, psd, cdr, n etc) with codecs (flv, mp3, avi, wmv, n etc)??  Coz, AFAIK, the original linux distributor doesnt include those codecs in their repository for those "license" reasons??

(it would be very satisfying if u can recommend me some links/article, in ur reply)

*hehe.....plz dont give me that "lol" words guys....wkwkwk. :popcorn: thanks!!!

---

### Post by lloyd_b on 2011-05-04
> **inovarts said:**
> Hi guys,, 
Im just wondering about those copyright thing in software developing. And it led me to these question, hope somebody could help me here........ :p

1. When an opensource software developer, build a nice software **which is able to open** some format from proprietary software, do they need to pay some royalty to those proprietary software developer to get some license? (ie. gimp -> psd, libreoffice -> doc, blender -> 3ds, lwo)

2. (If the answer is "no need to pay") Whats the difference those format (doc, psd, cdr, n etc) with codecs (flv, mp3, avi, wmv, n etc)??  Coz, AFAIK, the original linux distributor doesnt include those codecs in their repository for those "license" reasons??

(it would be very satisfying if u can recommend me some links/article, in ur reply)

*hehe.....plz dont give me that "lol" words guys....wkwkwk. :popcorn: thanks!!!

You're confusing copyright with patents.  File formats can't be copyrighted - the specification document can, and the *contents* of a particular file (such as the mp3 of a particular song) can be, but not the file format itself.  You can't copy the code of the format developer (that would be copyright infringement), but you are free to write your own code that reads that format.

The reason open source distributors shy away from audio/video codecs is that most such codecs are patented (in fact, most are covered by a substantial number of patents).  A patent does, in theory, make it illegal to distribute any implementation of the codec, even if you wrote that implementation yourself.

You're perfectly free to distribute a program that reads the mp3 file format.  But once you add in the code to actually turn it back into audio, you are implementing the codec, and you're potentially setting yourself up for a lawsuit for infringing on the patent.

(I won't get into whether or not patents that restrict software in this fashion *should* be allowed - that's a long and complex argument in its own right).

Lloyd B.

---

### Post by ve4cib on 2011-05-04
It also depends to a certain extent where you live.  Some countries/regions do not recognize software patents.  In such regions there isn't an issue with creating your own implementations of codecs.  Other regions rigorously enforce software patents.

---

### Post by doas777 on 2011-05-04
Lloyd has it right.
Copyright covers a manifestation of an idea (a written poem for instance), 
whereas patents cover the idea itself, independent of any kind of implementation. a patent on writing poems would prevent all people from writing so much as a limerick by any means, unless they have licensed the patent.

---

### Post by gsmanners on 2011-05-04
> **doas777 said:**
> Lloyd has it right.
Copyright covers a manifestation of an idea (a written poem for instance), 
whereas patents cover the idea itself, independent of any kind of implementation. a patent on writing poems would prevent all people from writing so much as a limerick by any means, unless they have licensed the patent.

You can't patent ideas (or rather, you shouldn't be able to). Once again, you can only patent implementations. But that patent allows you a limited monopoly on implementations of that same idea, not on the idea itself.

see [http://en.wikipedia.org/wiki/Patent](http://en.wikipedia.org/wiki/Patent)

---

### Post by Dustin2128 on 2011-05-04
EDIT: Realised I asked one of the questions asked by the OP.

---

### Post by doas777 on 2011-05-04
> **gsmanners said:**
> You can't patent ideas (or rather, you shouldn't be able to). Once again, you can only patent implementations. But that patent allows you a limited monopoly on implementations of that same idea, not on the idea itself.

see [http://en.wikipedia.org/wiki/Patent](http://en.wikipedia.org/wiki/Patent)
unfortunately, at least pre-bilsky, you can patent abstract ideas, known as 'business process' or 'Software' patents. there have been recent court cases that are beginning to change the landscape on soft patents, but the effect is still nascent.

a perfect example of patent encumbrance is the family of patents related to H.264 compression. these patents prevent ANY implementation/manifestation of the algorithms therein (algorithms are just ideas) even if you wrote your own, with no knowledge of the content of the patent in question.

---

### Post by user1397 on 2011-05-04
> **ve4cib said:**
> It also depends to a certain extent where you live.  Some countries/regions do not recognize software patents.  In such regions there isn't an issue with creating your own implementations of codecs.  Other regions rigorously enforce software patents.
is there a list somewhere of the countries which do not recognize software patents?  i tried googling it for a bit and couldn't find anything too concrete...

---

### Post by gsmanners on 2011-05-04
I think it's more notable which countries attempt to enforce [software patents]("http://en.wikipedia.org/wiki/Software_patent#Jurisdictions").

---

