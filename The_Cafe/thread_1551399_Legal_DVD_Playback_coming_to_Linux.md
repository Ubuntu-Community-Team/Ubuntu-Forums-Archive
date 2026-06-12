---
title: "Legal DVD Playback coming to Linux?"
date: 2010-08-12
forum: The Cafe
---

### Post by ronnielsen1 on 2010-08-12
[http://www.linuxjournal.com/content/legal-dvd-playback-coming-linux](http://www.linuxjournal.com/content/legal-dvd-playback-coming-linux)

> In a country where the legal system is based on precedents, a judge's  recent decision just may make the use of Linux a whole lot easier.
 From nearly the beginnings of entertainment DVDs, Linux users in  certain countries either had to break the law to watch their legally  obtained media on their computer, boot a Windows system, or not use  them.  Many chose to break the law and install decryption software.   Perhaps those days are over.
 Appeal Judge Garcia [found]("http://www.courthousenews.com/2010/07/23/29099.htm")  that General Electric did not break the Digital Millennium Copyright  Act by merely unlocking MGE UPS Systems' protection software in order to  repair faulty power supplies.  The judge wrote that the DMCA protects  against infringement, not viewing or using.  While these aren't DVDs  with copyrighted movies or music, it still sets a precedent for legal  fair use of DMCA protected products.  


---

### Post by gnomeuser on 2010-08-12
Even if this means we can ship libdvdcss the codecs required to decode a DVD are still covered by patents which means we can't ship them.

For legal DVD playback under Linux:

[http://www.fluendo.com/shop/product/fluendo-dvd-player/](http://www.fluendo.com/shop/product/fluendo-dvd-player/)

It works really well and solves the issue with patents.

---

### Post by Lucradia on 2010-08-12
> **gnomeuser said:**
> Even if this means we can ship libdvdcss the codecs required to decode a DVD are still covered by patents which means we can't ship them.

For legal DVD playback under Linux:

[http://www.fluendo.com/shop/product/fluendo-dvd-player/](http://www.fluendo.com/shop/product/fluendo-dvd-player/)

It works really well and solves the issue with patents.

^^ Yep, sorry, but it won't be that easy, OP.

---

### Post by TheNerdAL on 2010-08-12
Wait DVD playback is illegal? Why?!

---

### Post by forrestcupp on 2010-08-12
> **gnomeuser said:**
> Even if this means we can ship libdvdcss the codecs required to decode a DVD are still covered by patents which means we can't ship them.

But if it's declared legal to view DVDs, why wouldn't it be possible for someone to reverse engineer the codecs and offer a free alternative?  They did that with LAME, why couldn't it be done with DVD codecs?

---

### Post by LowSky on 2010-08-12
> **TheNerdAL said:**
> Wait DVD playback is illegal? Why?!

The same reason it cost money to use Microsoft Windows.

---

### Post by TheNerdAL on 2010-08-12
> **LowSky said:**
> The same reason it cost money to use Microsoft Windows.

But what if we paid for the DVD? D:

---

### Post by ronnielsen1 on 2010-08-12
> Wait DVD playback is illegal? Why?! 	

> In short, DVD playing under Linux is in a "grey area" where the MPAA  is not even trying anymore; they have moved on to HD formats instead  where they put the encryption in hardware.
  > Playing you DVDs doesn't ripoff anything. Using unlicensed software which copies a licensed, proprietary codec does.
  You misunderstand the whole issue.  Ths is not a case of someone's  hard work getting ripped off; not that reverse engineering is wrong  anyway, but that's not even the point.  The DVD-CCA came up with the  non-codec CSS so that they could charge DVD player manufacturers a  license fee; it's a shakedown, nothing more.  The only plausible  argument for "ripping off" has to do with copies of the DVD itself, and  that's not what we're talking about.  We're talking about watching DVDs  you paid for, in the industry-standard MPEG-2 format, which have been  scrambled by the DVD-CCA just so you have to pay extra for a key to  descramble them.  Imagine if you couldn't make a spare key to your own  house because of the Spare Key Authority who got legislation passed so  they controlled all spares.


[http://www.oreillynet.com/linux/blog/2006/07/a_fully_licensed_dmca_complian.html](http://www.oreillynet.com/linux/blog/2006/07/a_fully_licensed_dmca_complian.html)

I'd be curious on how many copies are in the US

---

### Post by forrestcupp on 2010-08-12
> **TheNerdAL said:**
> But what if we paid for the DVD? D:

You also have to pay for the means to decrypt the DVD into viewable format.

---

### Post by endotherm on 2010-08-12
ok, the issue is patents. a licensing agency (DVDLA) holds the patents for CSS decoding, so in order to write a ecoder/decoder, you must license the rights to implement the patent from them. this means that anyone who what to write a dvd css coder will have to pay for the right to do so. that is why the fluendo option is legal. Our hero DVD John did not pay for such a license, so the library he wrote cannot ever be legal in the us, no matter whether the DMCA is struck down or if css circumvention becomes completely legal.

just like so many aspects of the DMCA, we have the right to take a particular action, but we are forbidden from performing one of the critical steps that would facilitate that action. schools are allowed to take clips from copyrighted material for educational purposes without notice or permission, but they are still prevented from using dvddecryptor or any other tool to make it possible for them to exercise that right, or rather, they were until the latest library of congress review.

---

### Post by endotherm on 2010-08-12
> **forrestcupp said:**
> You also have to pay for the means to decrypt the DVD into viewable format.
well, **you** don't, but whoever wrote the css encoder/decoder has to license the patents from the dvdla. copyright infringement generally deals with the customer, whereas patent infringement deals with manufacturer.

---

### Post by forrestcupp on 2010-08-12
> **endotherm said:**
> well, **you** don't, but whoever wrote the css encoder/decoder has to license the patents from the dvdla. copyright infringement generally deals with the customer, whereas patent infringement deals with manufacturer.

Well, as they say, poop rolls down hill.  No one is going to pay the license fee and not unload it on the end user.

---

