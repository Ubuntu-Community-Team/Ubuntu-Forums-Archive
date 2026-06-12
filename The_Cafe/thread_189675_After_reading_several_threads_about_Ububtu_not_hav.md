---
title: "After reading several threads about Ububtu not having mp3 support by default..."
date: 2006-06-05
forum: The Cafe
---

### Post by greggh on 2006-06-05
I was wondering, couldn't it have support for LAME encoded mp3s by default? I thought that LAME was a free and opensource encoder. At least that way people could immediately have support for some of their mp3's. Is there something that prevents this from being included out of the box?

---

### Post by az on 2006-06-05
Is there something that prevents this from being included out of the box?

Yes.  The patent on mp3 playback.  The mp3 format is licenced in such a way that you need to pay a royalty to the patent holder in order to use it in most circumstances.

While I don't think it breaks the law to use it for yourself, a linux distribution would have to pay for the priviledge of providing that functionality for you.  

There is no such issue with using open formats, such as ogg vorbis (compressed audio like mp3) or ogg theora (compressed video like mpeg).

Not every country recognises software patents.  

It's pretty dumb to patent software.  It's not like software development can be compared to things like techniques to manufacture material goods.  In such a case, a patent helps protect the inventor from losing ownership of "idea".  In software, most "ideas" are not all that original, but only  algorythms than just about anyone would have written when trying to solve the same problem.

Without patents, certain ideas would not be made public - so they serve the public by making it possible for these ideas to get out.  In the case of software (or free-libre software) the idea belongs to the public to begin with and to give the owner of the patent rights to it only *prevents* others from benefiting for it.

It's lose-lose - one person gets a monopoly and nobody else gets anything.

---

### Post by greggh on 2006-06-05
[QUOTE=azz]Is there something that prevents this from being included out of the box?

Yes.  The patent on mp3 playback.  The mp3 format is licenced in such a way that you need to pay a royalty to the patent holder in order to use it in most circumstances.[/QUOTE]

I'm still confused about that. If you're including LAME's encoder/decoder which does not use Fraunhaffer's compression algorithm (that's what the patent is for, right), how would it be violating their patent? Just because LAME audio file name ends in .mp3?

---

### Post by mostwanted on 2006-06-05
Decoding mp3 is where the problem lies AFAIK. There is basically only one way to read an mp3.

And LAME is not a decoder.

---

### Post by az on 2006-06-05
[QUOTE=greggh]I'm still confused about that. If you're including LAME's encoder/decoder which does not use Fraunhaffer's compression algorithm (that's what the patent is for, right), how would it be violating their patent? Just because LAME audio file name ends in .mp3?[/QUOTE]
Despite lame being completely original code, the patent still holds on the mp3 format.


[http://www.mp3licensing.com/help/index.html](http://www.mp3licensing.com/help/index.html)

---

