---
title: "The name of 64bit version of ubuntu"
date: 2018-10-21
forum: The Cafe
---

### Post by fund_raiser on 2018-10-21
hi all

I just wonder why the name of the latest Ubuntu version is: ubuntu-18.04.1-desktop-**amd64**.iso 

Why *amd*? AMD is just a company name, the same as intel. Wouldn't it be better to name the download link: ubuntu-18.04.1-desktop-**64bit**.iso

I just wonder why does Canocical favour amd here? 

thx

---

### Post by QIII on 2018-10-21
That is a historical convention based on the fact that AMD was the first to bring 64 bit hardware and instruction sets to the consumer market.

The term stuck.  It does not mean Canonical favors AMD over Intel.  Ubuntu runs on either.

---

### Post by hackerb9 on 2018-10-22
QIII is correct, mostly.  Intel actually did come out with a 64-bit chip first: Itanium.  Its ABI (application binary interface) was called **ia64**. It was completely different from the ABI used in the 32-bit **i386** instruction set architecture. Itanium was going to be incredibly fast thanks to VLIW, it was shiny, it was new, it was "the future"... It was a disaster. Meanwhile, AMD had gone the easier (and in retrospect, smarter) route: they simply extended the old 32-bit i386 architecture with 64-bit features. Their ABI got named **amd64**. 

After abandoning ship from the chip that became known as "The Itanic", Intel needed a 64-bit chip and they needed one fast. So, they simply copied AMD and made Intel's new line of chips compatible with the amd64 ABI.

That was years ago and the ABI has grown since then, but fundamentally the binary interface which 64-bit Ubuntu is compiled to is still amd64. It leads to some confusion when people see it since amd64 code runs on Intel chips just fine, but developers see no reason to change the name. Perhaps they see it as a lesson in hubris and a reminder to not get bogged down in making a perfect "[Second System]("https://en.wikipedia.org/wiki/Second-system_effect")".

This name is not limited to Ubuntu developers, by the way. Microsoft Windows users are sometimes confused why Microsoft is pushing them patches named "AMD64" when they are running Intel processors. Microsoft's marketing department is separate from their developers, though, so the name has been changed on the surface to "X86-64". But, if you look closely at things like the system filenames you'll see amd64 popping up. 

So, that's the history. I'd also add that nothing forces Ubuntu to use the technical name of the ABI in their filenames, particularly when people are supposed to choose one to download. They could replace "amd64" with something less confusing. Unfortunately, your suggestion of "64bit" isn't specific enough as Ubuntu can run on several different 64-bit chips. Do you think "X86_64" would be better? If so, maybe file a bug with Ubuntu and let them know.

---

### Post by mastablasta on 2018-10-22
you forgot to add that the lawsuit from AMD was settled too late to have an effect on the market, so intel took over (or rather kept) the huge market share from AMD. i remember than around 2000 AMD was the CPU to have but then they started lagging behind intel. that was expected since their fundings were much lower.

then came ARM and "*destroyed*" intel on mobile market.

---

### Post by QIII on 2018-10-22
>  Intel actually did come out with a 64-bit chip first: Itanium.

Note that I deliberately said "consumer market".  The Itanium line was not intended for the consumer market.

Cray actually beat both Intel and AMD to the 64 bit arena -- in the 70s.

---

### Post by hackerb9 on 2018-10-25
I didn't think you were mistaken, Quill. I figured you knew what you were talking about but had shortened the facts so as to give a helpful answer instead of a long, rambling history like I did. (Often it's better to be concise than precise). I figured my post would be complementary to yours: I gave the long-winded and extraneous background while you actually answered the question. :)

---

