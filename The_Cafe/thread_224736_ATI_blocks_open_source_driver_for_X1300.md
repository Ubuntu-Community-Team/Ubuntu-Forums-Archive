---
title: "ATI blocks open source driver for X1300"
date: 2006-07-28
forum: The Cafe
---

### Post by ubuntu_demon on 2006-07-28
From [http://airlied.livejournal.com/31180.html](http://airlied.livejournal.com/31180.html) :

[quote=airlied]
Okay just an update for the world on something I told people at OLS, and in light of the AMD/ATI stuff...

I'm under NDA with ATI for information on a number of devices (r100, r200, r300) via a company I do work for, and using a utility that they gave me under that NDA I got a list of register names, numbers and bit names (no textual info) on the R5xx range of cards.

I wrote a driver for my X1300 card for 2D using that info and a VBE modesetting tool that trapped all the IO accesses. The code mod to the radeon driver is about 600 lines of actual code. I submitted this to ATI for release due to the NDAs I have with them. It is now > 4 months since I did this and I've heard nothing back from ATI apart from the initial interface.

This is just to say ATI's excuses of it being unable to review the 600 lines of code is not really believeable, and also I thought ATI would attend my talk at OLS to perhaps talk to me about it. So now the world knows, we have a probably open source driver available for the X1300 which does 2D modesetting (no big secrets in there) and ATI are blocking it. I'm not willing to do much more work on the driver until I can actually do something with it.
[/quote]

I added this to my blog :
[http://ubuntudemon.wordpress.com/2006/07/28/ati-blocks-open-source-driver-for-x1300/](http://ubuntudemon.wordpress.com/2006/07/28/ati-blocks-open-source-driver-for-x1300/)

---

### Post by mips on 2006-07-28
Moral of the story, stick with nVidia. Sad seeing ati are now in the AMD fold. Hopefully things change...

---

### Post by G Morgan on 2006-07-28
Companies will always look after themselves. The key is to support whatever corperate actions suit you and where there are corperate products that you don't agree with and there are free products that match your beliefs do so (as in change/support). This is called consumer choice and competition.

---

### Post by jimrz on 2006-07-28
> **G Morgan said:**
> Companies will always look after themselves. The key is to support whatever corperate actions suit you and where there are corperate products that you don't agree with and there are free products that match your beliefs do so (as in change/support). This is called consumer choice and competition.

EXACTLY.....vote with your wallet, 'tis the only thing they may listen to.

---

