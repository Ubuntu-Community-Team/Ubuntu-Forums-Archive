---
title: "odd EE times article about the unsuitability of Linux"
date: 2010-05-01
forum: The Cafe
---

### Post by sdowney717 on 2010-05-01
when used in mission critical defense applications.
An interesting read, but is it legitimate concern?

[http://www.ghs.com/news/eet4817_final2.pdf](http://www.ghs.com/news/eet4817_final2.pdf)

found that older article when browsing this site which is anti linux in nature it seems
[http://www.ghs.com/linux/threat.html](http://www.ghs.com/linux/threat.html)

---

### Post by Lensman on 2010-05-01
Looks like the finest article that MS can buy. :)

---

### Post by PhilGil on 2010-05-01
Not MS, in this case, but the CEO of an company that custom designs embedded systems software in competition with Linux-based embedded systems developers.  If you read the original article ([http://www.ghs.com/linux/threat.html](http://www.ghs.com/linux/threat.html)), it's full of absurd anti-Linux FUD about "script kiddies" and how easy it is to break into Linux systems.

Security is critically important to defense systems, but I don't see a legitimate reason why a "hardened" Linux would be any less secure than proprietary software.  The whole article reads like self-serving hogwash, to me.

---

### Post by Danny Dubya on 2010-05-01
> **Lensman said:**
> Looks like the finest article that MS can buy. :)
Ugh, no. If you actually looked at the article, then you must have read selectively, because it was saying that tightly controlled and secure custom operating systems that aren't intended for mass consumption by civilians were preferable for national defense. In other words, it was also arguing that Windows wasn't suitable for defense systems either -- Linux just happened to be singled out because many people place it on a pedestal for being free and open-source, and have illusions about its security as being on the level of near-invincibility.

---

### Post by red_Marvin on 2010-05-01
tl;dr for me, but iirc green hills develop their own secure os (eg stuff suitable to run mission critical loops on nuke armed stealth bombers), of course they will say that anything else is less secure be it linux or windows.

---

### Post by standingwave on 2010-05-01
Reminds me of this from about a year ago:

[French planes grounded by Windows worm]("http://news.cnet.com/8301-17852_3-10159186-71.html")

---

### Post by 3rdalbum on 2010-05-01
This comes down to the old "Security through obscurity" debate. A custom-written operating system is only as secure as the code that the vendor writes, and the vendor could deny the existence of attacks against the code.

---

### Post by gletob on 2010-05-01
I heard fire was secure, I wish I could Install it in these FUD makers houses.

---

### Post by euler_fan on 2010-05-02
There is both a straw-man here and a serious confusion of facts in the articles mentioned and neither deserves serious attention from the community as more than objects of intelligent ridicule.

The straw-man is that our options are:

1) a very insecure general purpose OS whose creators have no inherent interest in an inherently secure (and, note, reliable) OS independant of any use a government might wish to make of it and 
2) a number of special purpose OS's which are inherently secure because they're written by US citizens with security clearances. 

The is completely bogus. Certainly NASDAQ has an much interest in a secure, reliable OS as the US DOD does. So do we, the Linux community. And giving programmers security clearances doesn't make their software more secure or more reliable. Better programmers do that. So do rigorous review, bounties for bugs, good programing practices, and treating programming like the engineering discipline it actually is for production software.

The serious confusion of facts is that every piece of software needs to face the internet and be run on a general purpose OS. This is completely wrong. I would argue that nuclear reactors control software shouldn't see the internet at all and certainly if it must should do so on an as limited and tightly controlled basis as possible. Likewise, we don't need the full flexibility of a complete Linux install in many applications. Do we really need a full linux install to monitor and optimize fuel injection for an engine? No. How about flow monitors? No. Ballistics computers? No. Elevator controls? No. Electronic thermometers? No. In fact, in many of these cases we probably gain far more overhead in terms of hardware requirements than we save in development costs by being able to use a nice, shiny API.

---

