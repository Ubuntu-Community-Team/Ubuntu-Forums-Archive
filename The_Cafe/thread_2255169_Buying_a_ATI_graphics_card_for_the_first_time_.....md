---
title: "Buying a ATI graphics card for the first time .... Need to clear some doubts"
date: 2014-12-02
forum: The Cafe
---

### Post by linuxyogi on 2014-12-02
Hi,

I am planning to buy [this graphics card]("http://www.flipkart.com/asus-amd-ati-hd-5450-2-gb-ddr3-graphics-card/p/itmdq25qcqnygvbh?pid=GRCDQ25QCQNYGVBH&otracker=from-search&srno=t_39&query=ati+graphic+card&ref=0f13bcbc-e70e-4776-9c74-804f01db9c40"). This is the first time I a buying a ATI graphics card,
Nvidia's True Videos HD is called vdpau under Linux right ? So what is ATI's accelerated video 
output driver called ?

Also, am bit confused if [this card]("http://www.flipkart.com/asus-amd-ati-hd-5450-2-gb-ddr3-graphics-card/p/itmdq25qcqnygvbh?pid=GRCDQ25QCQNYGVBH&otracker=from-search&srno=t_39&query=ati+graphic+card&ref=0f13bcbc-e70e-4776-9c74-804f01db9c40") is capable of HD decoding. Someone please confirm that for me.

---

### Post by QIII on 2014-12-02
NVIDIA does use VDPAU with some of its own extensions.  AMD uses the more generalized VA-API with AMD's XvBA back end.

NVIDIA's solution has a richer feature set for Linux.

As for that card's encoding?  I don't know.  But in terms of the ATI cards still offering Linux support, that is an entry level economy model.  So I wouldn't expect too much out of it -- particularly since it's passively cooled.  Very capable card for the vast majority of users.  For really demanding stuff, not so much.

---

### Post by linuxyogi on 2014-12-02
Actually I read [this]("http://www.openbsdindia.org/amd64.html") 

> [COLOR=#000000][FONT=Times New Roman]X Window System support is available for most graphics cards, using the X.Org server. As with other free operating systems it is highly recommended that Nvidia cards are avoided since this vendor continues to show tremendous resistance towards releasing information that would allow X.Org to support their hardware properly.[/FONT][/COLOR]

and decided to buy ATI this time. I thought this rule applies to all open source projects. So which brand do you recommend, Nvidia or ATI ? Other that HD decoding I want play some games with moderate details.

---

### Post by pqwoerituytrueiwoq on 2014-12-02
which games?
are we talking 3ed person view rpg type games, or fps games like xonotic

---

### Post by papibe on 2014-12-02
Hi linuxyogi.

For video decoding, and desktop effects anything relatively new would work just fine. Even Intel integrated graphics.

For gaming in Linux, specially Steam games, and as today, Nvidia cards, using their proprietary driver, have better game support and performance.

Regards.

P.S.: Note that AMD cards would only shine if you use the AMD proprietary driver too.

---

### Post by QIII on 2014-12-02
@linuxyogi --  That sounds like some true-believer bloviating to me.

A lot of folks hate NVIDIA because they don't release much to the open source community.  A "sin" if ever there was one in the minds of some.  That's no reason for YOU to not use their products unless you have a neckbeard's religious view of open source.

Use what works.  Fact is, NVIDIA works better for a lot of gaming applications on Linux.  ATI better on Windows.

I'm an ATI user and have been for years.  But facts is facts.  Don't base your decisions about what YOU want to do on someone else's vision of misplaced zealotry.

---

### Post by linuxyogi on 2014-12-03
> **pqwoerituytrueiwoq said:**
> which games?
are we talking 3ed person view rpg type games, or fps games like xonotic

Mostly games like the NFS series (Car racing).

> **papibe said:**
> Hi linuxyogi.

For video decoding, and desktop effects anything relatively new would work just fine. Even Intel integrated graphics.

For gaming in Linux, specially Steam games, and as today, Nvidia cards, using their proprietary driver, have better game support and performance.

Regards.

P.S.: Note that AMD cards would only shine if you use the AMD proprietary driver too.

> **QIII said:**
> @linuxyogi --  That sounds like some true-believer bloviating to me.

A lot of folks hate NVIDIA because they don't release much to the open source community.  A "sin" if ever there was one in the minds of some.  That's no reason for YOU to not use their products unless you have a neckbeard's religious view of open source.

Use what works.  Fact is, NVIDIA works better for a lot of gaming applications on Linux.  ATI better on Windows.

I'm an ATI user and have been for years.  But facts is facts.  Don't base your decisions about what YOU want to do on someone else's vision of misplaced zealotry.

In that case I will go for Nvidia. My budget is not that great. So I guess I will settle with [this one]("http://www.flipkart.com/gainward-nvidia-2gb-ddr3-gt610-2-gb-graphics-card/p/itmddrzzcygk7hzf?pid=GRCDDRZZCYGK7HZF&otracker=from-search&srno=t_3&query=nvidia+graphics&ref=599aa1d6-16a3-4ade-a904-6b7ebf97ff6c").

---

### Post by papibe on 2014-12-03
A 610 sounds OK.

I have a similar card but older generation (310M) on my laptop and so far these games have played very well: Amnesia, Limbo, Rochard, Tiny & Big.

Although I have to say they all are not high intensive graphics games.

Regards.

Note that in general the second digit reflect how powerful the card is. For instance 520 > 610, 550 >> 420. etc

---

### Post by pqwoerituytrueiwoq on 2014-12-03
> **linuxyogi said:**
> In that case I will go for Nvidia. My budget is not that great. So I guess I will settle with [this one]("http://www.flipkart.com/gainward-nvidia-2gb-ddr3-gt610-2-gb-graphics-card/p/itmddrzzcygk7hzf?pid=GRCDDRZZCYGK7HZF&otracker=from-search&srno=t_3&query=nvidia+graphics&ref=599aa1d6-16a3-4ade-a904-6b7ebf97ff6c").
The GeForce GT 610 card is a rebranded GeForce GT 520.
The GeForce GT 620 card is a rebranded GeForce GT 530.
be sure to compare the price
if you can find a cheap **OEM** GTX 460 those are good cards, i think that is a bit out of your budget though

---

