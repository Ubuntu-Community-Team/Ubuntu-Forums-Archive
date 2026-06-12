---
title: "Windows Guy Tries Ubuntu 7:04: Part 2 - Two Weeks Later [Article]"
date: 2007-08-02
forum: The Cafe
---

### Post by pacsum on 2007-08-02
I know that people will start to scream at me or get annoyed because I posted this here but I hope that some ubuntu developer reads it. It's an unbiased article and from what I have saw it says nothing but the true.

Windows Guy Tries Ubuntu 7:04: Part 2 - Two Weeks Later 

[http://scitech.teambio.org/2007/07/29/windows-guy-tries-ubuntu-704-part-2-two-weeks-later/](http://scitech.teambio.org/2007/07/29/windows-guy-tries-ubuntu-704-part-2-two-weeks-later/)

---

### Post by aysiu on 2007-08-02
The Gutsy Gibbon Idea Pool isn't a place where developers hang out in the hopes forum users will post stories for them to read that have been previously posted on Digg.

I've moved this to the Cafe.

---

### Post by tigerpants on 2007-08-02
The fonts comment was interesting... personally I think font rendering in linux is better than windows or OSX. But I guess its personal preference.

---

### Post by forrestcupp on 2007-08-02
I may be wrong, but fonts seem to be a little better out of the box in Gutsy.  Fonts are one thing my wife complained about, but she thinks they look ok in Gutsy.

Here is an example from the article of why my signature is true:
> Every problem that I ran into, I found someone willing (if not able) to help. While some people were real idiots (”Windo$e Sux man!” or “M$ users are stupid” demonstrate a level of ignorance that that defies explanation) most people were very nice.

---

### Post by reacocard on 2007-08-02
> **tigerpants said:**
> The fonts comment was interesting... personally I think font rendering in linux is better than windows or OSX. But I guess its personal preference.

Really? For me, the default rendering does suck, but with a libfreetype with an improved subpixel hinting patch and a few tweaks, the fonts are now far better than anything I see on OSX or Windows.

It's actually a pretty good review, he sums up both the strengths and weaknesses of Ubuntu in a fair way. +1 to him.

---

### Post by macogw on 2007-08-02
I've never seen anything wrong with the fonts, so I always get confused when people say they suck in Ubuntu. Yeah, I installed the msttcorefonts so I could have "real" Times New Roman and Arial...is that what you all mean?

---

### Post by phrostbyte on 2007-08-02
> **macogw said:**
> I've never seen anything wrong with the fonts, so I always get confused when people say they suck in Ubuntu. Yeah, I installed the msttcorefonts so I could have "real" Times New Roman and Arial...is that what you all mean?

I agree. I think Windows XP (specifically) font rendering is disgustingly horrible compared to OS X, Vista, and Ubuntu.

I made a patch which installs a tweaked libfreetype and other libraries to add font hinting an anti-aliasing features not even seen in Mac OS X. [http://ubuntuforums.org/showthread.php?t=515947]("http://ubuntuforums.org/showthread.php?t=515947")

It also adds the Red Hat revolution fonts, can be used as a drop in replacement for msttcorefonts (I think they look even better.)

---

### Post by prizrak on 2007-08-02
> **reacocard said:**
> Really? For me, the default rendering does suck, but with a libfreetype with an improved subpixel hinting patch and a few tweaks, the fonts are now far better than anything I see on OSX or Windows.

It's actually a pretty good review, he sums up both the strengths and weaknesses of Ubuntu in a fair way. +1 to him.

This is weird alot of people bitch about fonts on Ubuntu. I personally don't see any problems. Seems like there are two camps one thinks that fonts suck others that they are OK. It would be pretty nice if AIGLX was used for font AA. XGL uses hardware font smoothing and it looks very good.

---

### Post by reacocard on 2007-08-02
> **prizrak said:**
> This is weird alot of people bitch about fonts on Ubuntu. I personally don't see any problems. Seems like there are two camps one thinks that fonts suck others that they are OK. It would be pretty nice if AIGLX was used for font AA. XGL uses hardware font smoothing and it looks very good.

I really think the reason its like that is because different people have different monitors. On most LCDs, linux font rendering isn't that great since the subpixel hinting doesn't work as well, but on CRTs and other monitors it looks very nice. Fortunately, improved subpixel font rendering is readily available for those of us who want it, so it is not a huge issue.

---

### Post by mrgnash on 2007-08-03
Anyone who 'screams' or gets 'annoyed' over this is a reactionary. It reads to me as a very honest and impartial appraisal of the system. I particularly liked your point about the package manager, because a lot of new users complain about how hard it is to install things in Ubuntu -- whereas I find it a darn sight easier, thanks to the package manager.

---

### Post by prizrak on 2007-08-03
> **reacocard said:**
> I really think the reason its like that is because different people have different monitors. On most LCDs, linux font rendering isn't that great since the subpixel hinting doesn't work as well, but on CRTs and other monitors it looks very nice. Fortunately, improved subpixel font rendering is readily available for those of us who want it, so it is not a huge issue.

Weird, I use LCD's exclusively and have no problems.

---

### Post by macogw on 2007-08-03
> **prizrak said:**
> Weird, I use LCD's exclusively and have no problems.

Yeah, me too.  I'm on my laptop all the time.  The only thing that annoys me is that it's sunny and I see my reflection more than I see the screen!

Ooooh maybe that's something?  I recall being asked if I had a Sony because "the screen is so clear" (no, Gateway).  Maybe the shiny screens it looks good and then the matte ones are when it looks bad?

When I use the CRT at my mom's house, though, it looks fine.  Can't say much for the 9 year old CRT at my dad's though.  I haven't left the TTY in weeks.  I caught a bad day to compile E17 from CVS....it's broken (I know Ubuntu has packages, this is a Debian system though).

---

### Post by reacocard on 2007-08-05
> **macogw said:**
> Yeah, me too.  I'm on my laptop all the time.  The only thing that annoys me is that it's sunny and I see my reflection more than I see the screen!

Ooooh maybe that's something?  I recall being asked if I had a Sony because "the screen is so clear" (no, Gateway).  Maybe the shiny screens it looks good and then the matte ones are when it looks bad?

When I use the CRT at my mom's house, though, it looks fine.  Can't say much for the 9 year old CRT at my dad's though.  I haven't left the TTY in weeks.  I caught a bad day to compile E17 from CVS....it's broken (I know Ubuntu has packages, this is a Debian system though).

Nope, I also have a glossy screen. Its not a huge deal though, the default rendering is OK, I just like my modified stuff a lot better. Before I knew there was an alternative, I didn't even notice that the fonts were bad at all, so I really think its mostly a matter of taste, although monitor type may have an impact.

---

### Post by Erik Trybom on 2007-08-05
The coolest part, I think, is that he was able to set up a fully working Apache server on Linux from the command line only two weeks after he installed it. 

To me this means: YES, you can make the switch if you want to. And while it will take some effort, anyone with some patience and willingness to learn can do it.

---

### Post by g2g591 on 2007-08-05
hmm I have an lcd and my renderings just as good on (k)ubuntu as on vista.

---

