---
title: "how come ubuntu makes it look better?"
date: 2006-11-26
forum: The Cafe
---

### Post by kanpachi on 2006-11-26
hey guys
i was wondering
i just love ubuntu, and i use Dapper as my main and only OS
but i got to try out a few distros, and i always kept wondering
how come ubuntu's font smoothing is so amazing and easy on the eyes?
i tried installing Mandriva, Debian, Frugalware, Zenlinux, KateOs and the fonts never looked as good as ubuntu's
esp. the hebrew ones
so how come? is ubuntu using something out of the oridnary?

---

### Post by Klaidas on 2006-11-26
Hmmm...
Good developers?

---

### Post by IYY on 2006-11-27
It could either be a Gnome vs. KDE issue, or the fact that Ubuntu has newer software and fonts, and more robust packages than other distributions, especially when it comes to international language support.

---

### Post by ~LoKe on 2006-11-27
You adjusted to Ubuntu.  I mean, my first time here I thought the fonts were horrible.  Now I like them better than those of Windows.

---

### Post by vayu on 2006-11-27
> **kanpachi said:**
> 
how come ubuntu's font smoothing is so amazing and easy on the eyes?


There is a font drawing algorithm called BCI (Byte Code Interpreter).  It is patented by apple.  Through reverse engineering the Freetype Project has implemented a byte code interpreter. Due to legal issues in some countries it is disabled by some distros.  It is enabled in a few distros, Ubuntu being one of them.   

[http://alkalay.net/linux/docs/font-howto/Font.html]("http://alkalay.net/linux/docs/font-howto/Font.html")

---

### Post by shining on 2006-11-27
> **vayu said:**
> There is a font drawing algorithm called BCI (Byte Code Interpreter).  It is patented by apple.  Through reverse engineering the Freetype Project has implemented a byte code interpreter. Due to legal issues in some countries it is disabled by some distros.  It is enabled in a few distros, Ubuntu being one of them.   

[http://alkalay.net/linux/docs/font-howto/Font.html]("http://alkalay.net/linux/docs/font-howto/Font.html")

Right, but it's also in Debian (which I found surprising when I discovered it), and probably in some other distribs the OP listed.
So it's probably a configuration problem.
Note that font preferences are very different and subjective :

> 
ubuntu's font smoothing is so amazing and easy on the eyes


(Nearly) all kind of font smoothing look amazing and easy on the eyes for at least a few users. :)
You probably just need to configure freetype properly (using fontconfig settings). And in the worst case, recompiling freetype.

---

### Post by smdeep on 2006-11-27
> **shining said:**
> 


(Nearly) all kind of font smoothing look amazing and easy on the eyes for at least a few users. :)


I agree. I love my fonts in Kubuntu and SimplyMepis. To be honest I hate the look of fonts on the Mac Mini, (we have one in my work place). I have tried all tricks to make them look nice but still they do not match my Kubuntu desktop. If there is one thing I like about Windoze it is the font rendering. I rate it above all comp oses. I am 42 and have to wear reading glasses so I do not like the fuzzy look of fonts. I have disable anti-aliasing for fonts from size 8-12.

---

