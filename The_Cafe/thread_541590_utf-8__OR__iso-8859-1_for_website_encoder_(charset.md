---
title: "utf-8  OR  iso-8859-1 for website encoder (charset) ?"
date: 2007-09-03
forum: The Cafe
---

### Post by user1397 on 2007-09-03
Why should one be used over the other?

Are there advantages or disadvantages to any of them? (Compatibility, readability, accessibility, anything?)

I currently use the iso-8859-1 standard, I live in north america, and I don't necessarily work  on a single OS at any time; I use windows, linux, and macs (sometimes).

---

### Post by Fbot1 on 2007-09-03
UTF-8 is preferred more.

---

### Post by Spr0k3t on 2007-09-03
utf-8 is best.

---

### Post by user1397 on 2007-09-03
hmm, ubuntuforums.org uses iso-8859-1...interesting

---

### Post by nowshining on 2007-09-03
I delete sending of either in my firefox configs of my portable firefox..optimized for protection hardcore.. ;)

---

### Post by Rhapsody on 2007-09-03
UTF-8 is what all/most modern operating systems natively work in, if I recall correctly. It has the advantage of allowing characters from just about every language in the world to be used in the same document or string, since they're all a part of unicode. I'd recommend using it as much as possible.

---

### Post by popch on 2007-09-03
> **Rhapsody said:**
> UTF-8 is what all/most modern operating systems natively work in, if I recall correctly. It has the advantage of allowing characters from just about every language in the world to be used in the same document or string, since they're all a part of unicode. I'd recommend using it as much as possible.

Not quite.

UTF-8 is a small subset of unicode. It has the nice property that each character uses exactly 8 bits. For a US American site, that will be quite enough since they do not usually contain text in any other language.

iso-8859-1 on the other hand supports a greater number of 'foreign' (to the USA)  languages. I am not sure if that includes languages using altogether different glyphs, though.

---

### Post by user1397 on 2007-09-03
Ah ok.

So to change it to unicode, I would just need to replace this: [html]<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />[/html] with this: [html]<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />[/html] ?

---

### Post by popch on 2007-09-03
> **ubuntuman001 said:**
> Ah ok.

So to change it to unicode, I would just need to replace this: [html]<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />[/html] with this: [html]<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />[/html] ?

This will only work if the document contains only characters wich are correctly encoded in the utf-8 character set. Otherwise, you would have to 'translate' the characters.

I presume that the character sets are listed on [unicode's site]("http://www.unicode.org/").

Oh, to be nitpicking: both utf-8 and iso-8859-1 ***are ***unicode.

---

### Post by user1397 on 2007-09-03
> **popch said:**
> This will only work if the document contains only characters wich are correctly encoded in the utf-8 character set. Otherwise, you would have to 'translate' the characters.

I presume that the character sets are listed on [unicode's site]("http://www.unicode.org/").

Oh, to be nitpicking: both utf-8 and iso-8859-1 ***are ***unicode.ah, alright, thanks.

---

### Post by Rhapsody on 2007-09-03
> **popch said:**
> Not quite.

UTF-8 is a small subset of unicode. It has the nice property that each character uses exactly 8 bits. For a US American site, that will be quite enough since they do not usually contain text in any other language.

iso-8859-1 on the other hand supports a greater number of 'foreign' (to the USA)  languages. I am not sure if that includes languages using altogether different glyphs, though.
Nope. [UTF-8](http://en.wikipedia.org/wiki/UTF-8) can represent any character in the Unicode standard, which includes all of ISO-8859-1 and a hell of a lot more besides. The only real disadvantage is that UTF-8 requires three bytes to represent a lot of the Basic Multilingual Plane characters (UTF-8 uses anywhere from one byte to four bytes for each character), meaning [UTF-16](http://en.wikipedia.org/wiki/UTF-16/UCS-2) may be more space-efficient in certain cases where a lot of non-Latin characters are used. There is also [UTF-32](http://en.wikipedia.org/wiki/UTF-32/UCS-4), but this has no real advantages over the other two and is rarely used.

But it most be noted that all Unicode Transformation Formats (UTF-8, UTF-16, UTF-32, and others) can represent all Unicode characters, it's just a matter of how efficient they are with space and how easy they are to use in the contexts of programming.

Incidentally, I was also wrong in stated that all/most modern operating systems use UTF-8 natively. Most actually seem to use UTF-16.

---

### Post by popch on 2007-09-03
> **Rhapsody said:**
> Nope. [UTF-8](http://en.wikipedia.org/wiki/UTF-8) can represent any character in the Unicode standard, which includes all of ISO-8859-1 and a hell of a lot more besides. 

I sit corrected, and thanks for correcting my mistake.

---

### Post by southernman on 2007-09-03
I think you can do this also. Someone correct me please if it's wrong.

> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"; charset=iso-8859-1 />


---

### Post by user1397 on 2007-09-03
> **southernman said:**
> I think you can do this also. Someone correct me please if it's wrong.I don't think that would work, but maybe if there are quotation marks around the iso one too?

but o well, as has been said in this thread, utf basically contains all the characters of iso-8859, so it would be pointless to have both charsets.

Thanks for all the replies by the way, I think I'm switching to utf-8 now.

---

