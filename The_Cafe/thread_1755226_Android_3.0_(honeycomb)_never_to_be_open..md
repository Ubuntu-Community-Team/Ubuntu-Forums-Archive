---
title: "Android 3.0 (honeycomb) never to be open."
date: 2011-05-10
forum: The Cafe
---

### Post by Dustin2128 on 2011-05-10
[http://linux.slashdot.org/story/11/05/11/0041250/Android-Honeycomb-Will-Not-Be-Open-Sourced](http://linux.slashdot.org/story/11/05/11/0041250/Android-Honeycomb-Will-Not-Be-Open-Sourced)
Just something I read a few minutes ago. Is this legal? There's quite a lot of GPL code that goes into android after all. I find it hard to believe that they refuse to release the source code "to protect their image". Who cares if it's buggy as hell- if it's open, you have Linus's law working for you.

---

### Post by FuturePilot on 2011-05-11
Slightly misleading title.

> During the Android Fireside Chat this afternoon, Google’s Dan Morill explained a bit more about the situation. As the bits and pieces that make up Android 3.1 get added into the next version, and the brand new bits that will come together and make this unifying UI get implemented, it will be appropriate to release Android Source.
[http://www.geek.com/articles/mobile/from-io-2011-confirmed-honeycomb-source-will-never-exist-on-its-own-20110510/]("http://www.geek.com/articles/mobile/from-io-2011-confirmed-honeycomb-source-will-never-exist-on-its-own-20110510/")

---

### Post by PhillyPhil on 2011-05-11
I think they're trying to keep 3.0 off phones (tablets only).  It stinks, but at least they've just announced IceCream Sandwich will be open source, as usual.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-05-11
They should definitely be sued to death. This is a severe GPL violation and undermines the basic principles of Free Software.

---

### Post by bfc on 2011-05-11
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> They should definitely be sued to death. This is a severe GPL violation and undermines the basic principles of Free Software.

Why? Google released all the LGPL and GPL portions of Honeycomb, and the code that wasn't released, I believe is licensed under the Apache License.

---

### Post by jamesjenner on 2011-05-11
This is old news. I saw people going on about this weeks if not months ago. As stated above Google is not doing anything wrong and is meeting all their obligations. Can't see anything wrong with what they're doing IMHO.

Cheers,

James.

---

### Post by cap10Ibraim on 2011-05-15
> 
The company revealed Thursday that it will delay publication of the Android 3.0 source code for the foreseeable future—possibly for months. It's not clear when (or if) the source code will be made available. The decision puts Android on a path towards a "draconian future" of its own, in which it is controlled by a single vendor—Google.

[http://arstechnica.com/open-source/news/2011/03/android-openness-withering-as-google-withhold-honeycomb-code.ars](http://arstechnica.com/open-source/news/2011/03/android-openness-withering-as-google-withhold-honeycomb-code.ars)

---

### Post by earthpigg on 2011-05-15
> By Ryan Paul | Published about a month ago

More has come to light since this premature article was written.

> The vast majority of Android smartphones are encumbered by lockdown mechanisms that block installation of third-party firmware.

Linus chose the GPLv2 over migrating to GPLv3. Not sure if that is the technical reason for this beign allowed, but Linus is certainly kinda sorta ok with this. So, take it up with him.

> Because Android operates its own Google-controlled fiefdom outside of the upstream stack, its growing popularity doesn't materially benefit upstream Linux.

Um, yes it does. It doesn't benefit Linux *as much* as it could, but kernel contributors are still welcome to merge patches and modules and whatnot as they wish. That option being available benefits Linux *to the extent that kernel contributors want it* to materially benefit Linux.

> Google further demonstrated its apathy towards the third-party Android developer community when the company's legal department sent cease and desist notices to a prominent modder in an effort to block the inclusion of Google's proprietary Android software in custom firmware images. 

Google isn't exactly the first company to differentiate its Linux distribution with proprietary addons that add value. Anyone seen the source code for Ubuntu One's server backend, or everything included in ubuntu-restricted-extras or Adobe Air provided by a "Canonical Partner"? This can also be done in trademark: Whatever happened to the distro called "Ubuntu Ultimate Edition"? Eh? yeah. None of these are *exactly* the same due to *slightly* different wording of promises by Canonical and Mark and Google, but the effect is on the same spectrum of shades of gray.

> The insular nature of the Android userspace makes interoperability between Android and conventional mobile and desktop Linux platforms difficult and impractical.

If Software Team X wants stuff from Software Team Y to run on X, that kind of falls to Software Team X. It isn't up to Linux Mint to ensure that their additions run on Ubuntu, for example. How's that 100% debian binary compatibility coming along, anyways?

> Rubin told BusinessWeek that Google has made the decision to keep the Honeycomb source code under wraps because it doesn't want hardware vendors to adapt it to run on other form factors where it might not function properly. Rubin says that Google cut corners during Honeycomb's development in an effort to rush it to market. He believes that widespread adoption at this stage in usage scenarios that Google didn't anticipate would lead to a very negative user experience.

That is fairly reasonable, actually. How would google look, if their brand name was put on Honeycomb as crammed into a cell phone's display?

Honeycomb was intended to be the pre-SP Vista. "Our shareholders want a product now, even if it ain't to great."



....

If someone wants to hate on google, there are plenty of avenues available without resorting to journalistic sensationalism.

---

### Post by Johnsie on 2011-05-15
No programmer/company wants to release a sub-par code into the wild. Let them make the improvements and then release it. Patience is a virtue. And yes, Google partners should get access to the code first... That will ensure that the first devices released are of high quality. First impressions mean everything in IT.

---

### Post by Simon17 on 2011-05-15
> **earthpigg said:**
> 
Linus chose the GPLv2 over migrating to GPLv3. Not sure if that is the technical reason for this beign allowed, but Linus is certainly kinda sorta ok with this. So, take it up with him.


For all practical purposes, it would be impossible to change the kernel to GPL3 because it would require consent from the hundreds of people who have released their code under version 2. Linus is only the maintainer. Ownership of the code by default belongs to the original authors. I heard an estimate fairly recently that only about 2% of code in the kernel today was written by Linus himself.

---

### Post by Dustin2128 on 2011-05-15
I understand that they don't want to release crappy code as open source, but it seems counter intuitive to me. Release source, then you'll have loads of programers working on it to improve it. Don't, and you'll have to fix it with your own resources.

---

