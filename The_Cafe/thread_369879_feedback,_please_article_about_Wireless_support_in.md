---
title: "feedback, please: article about Wireless support in Linux"
date: 2007-02-25
forum: The Cafe
---

### Post by gradedcheese on 2007-02-25
Hi there.  I wrote an [article about 802.11 wireless support in Linux]("http://andrey.thedotcommune.com/wireless.html") and I would appreciate it if a few people read it and give me some feedback.

A little background: this article is aimed at regular users who are frustrated about wireless support in Linux but have a desire to know why the situation is the way that it is and how it will improve.  I've helped quiet a few people sort out their wireless problems in the forums and I occasionally see comments about how "Linux wireless sucks" or "Linux sucks" from confused users.  Therefore, I want to explain to them a little about why we're in the situation that we're in, along with things like FCC regulatory domain that they may not have thought about.

You can also look at this as an exciting story of firmware, media access control implementations, regulations, and chipsets :)

Thanks for your time and any comments.

---

### Post by Tomosaur on 2007-02-25
Good article! Informative and helpful :)

---

### Post by koenn on 2007-02-25
> You can also look at this as an exciting story of firmware, media access control implementations, regulations, and chipsets
very interesting - excellent "executive summary" on why wireless can be problematic.

I do have some doubts on whether it will get its message across to your average "Wireless doesn't work. Linux sucks" user but they should at least get the general idea that there is more involved than meets the eye.

Oh, and i still don't understand what that FCC regulatory domain is about.

---

### Post by gradedcheese on 2007-02-25
Thanks!

> 
Oh, and i still don't understand what that FCC regulatory domain is about.


Yeah, I probably need to go into a little more detail on that.  The FCC regulates the radio spectrum in the USA (and similar organizations exist elsewhere), making rules about what devices can operate at what power and what frequencies under what licenses.  The frequencies used in 802.11 are in the Part 15 'junk band' and there are a lot of strict rules about them.  Incidentally, this also has to do with why channels 6 and 11 on your b/g router work better than the other channels (the outer channels have to have a strict 'cutoff' to stay within the allowed range).

The 802.11 devices are legal to operate as long as they're staying within the rules, otherwise the operator needs a license.  The rules include what frequencies (channels) are allowed, where active probing is allowed, the maximum power allowed on each channel, and (in the 802.11a case) some crazy stuff about military radar compatibility.  See paragraphs three and four in the [wikipedia article]("http://en.wikipedia.org/wiki/802.11") for a bit more detail.

However the radio chips in a WiFi card go after the MAC layer.  You can generally just tell the radio "hey, do this like this" and it will do it, as it doesn't have much logic of its own.  It's up to the MAC (which might be software) and firmware to ensure that it's operating the radio correctly.  This is where there's a risk that, having modified some driver code, the programmer unintentionally tells the otherwise 'dumb' card to do something illegal.  As far as I know, this has never happened in reality.  But you can see how this may be used as an excuse to not bother allowing open source drivers :(  (even though it can be overcome with a little work)

---

