---
title: "Ubuntu 9.10 Issues/etc"
date: 2009-11-16
forum: Testimonials &amp; Experiences
---

### Post by ashleydangerous on 2009-11-16
I've installed Ubuntu on two different computers -- both upgrades, and then a complete reinstall on another.  Neither of the machines work properly, to the point where I'm reverting back to 9.04 as I type this.  I've spent over five hours fixing problems, only to have others emerge and disappear more or less as they feel like it.  I feel like my computer's been taken over by malignant ghosts of some kind.

I'm so frustrated that I'm at the point of just moving to a different distribution, and was curious as to why this release is so bad.  Will the next one disable my mouse/keyboard/video/sound arbitrarily?  Will I get random lag and lockups that I didn't get with 9.04, or is the release cycle just more rushed or whatever now?

Seriously, it's like Ubuntu 9.10 is the Linux equivalent of Vista, or maybe Windows ME.  At least with ME, I could use my mouse and keyboard...

---

### Post by hwttdz on 2009-11-16
This is not a support request.

And viewing your profile I see you haven't asked a question in over a year.  It's quite possible, some might even say likely, that you encountered known bugs, and were unable to find the known solutions.  Anyways best of luck with 9.04. 

If you're unwilling to encounter any bugs it's probably best to sick with as minimalistic and stable a distribution as possible.  A good first step would be only using LTS releases and of course only using supported hardware.

---

### Post by Senesence on 2009-11-16
> **ashleydangerous said:**
> I've installed Ubuntu on two different computers -- both upgrades, and then a complete reinstall on another.  Neither of the machines work properly, to the point where I'm reverting back to 9.04 as I type this.  I've spent over five hours fixing problems, only to have others emerge and disappear more or less as they feel like it.  I feel like my computer's been taken over by malignant ghosts of some kind.

I'm so frustrated that I'm at the point of just moving to a different distribution, and was curious as to why this release is so bad.  Will the next one disable my mouse/keyboard/video/sound arbitrarily?  Will I get random lag and lockups that I didn't get with 9.04, or is the release cycle just more rushed or whatever now?

Seriously, it's like Ubuntu 9.10 is the Linux equivalent of Vista, or maybe Windows ME.  At least with ME, I could use my mouse and keyboard...

Yea, I sort of feel the same.

Things were fine after the upgrade, for a few days at least, but then I got some major filesystem corruption, and fsck couldn't fix it, so ultimately I had to reinstall.

However, even with the reinstall, I got a whole new set of problems, some of which I resolved, but installing the nvidia drivers breaks the X server now, so.........yea, I get the feeling that this release has some issues.

PS: Tell me what your problems are; maybe I, or someone else here, could help.

---

### Post by ashleydangerous on 2009-11-16
> **hwttdz said:**
> This is not a support request.

And viewing your profile I see you haven't asked a question in over a year.  It's quite possible, some might even say likely, that you encountered known bugs, and were unable to find the known solutions.  Anyways best of luck with 9.04. 

Viewing your profile, I see that you joined these forums back in 2006.  Is it safe to say that you used Linux for the first time back then?  Or maybe that's when you first started using the Internet?  No, I wouldn't make that sort of assumption, because I try not to jump to conclusions.

Actually, I dug through these and other forums, found a lot of similar problems, and it was just one big chain of "if this doesn't work, then try this!  Oh, that doesn't work, and broke something else?  Well, here's another huge list of things to try, which isn't going to fix the lag."  The straw that broke the camel's back was adding noacpi to my kernel startup options, and having that completely screw up my keyboard and mouse.  For whatever reason.  This sort of thing happened on two different machines, and if you look in the forums in general, you'll see that this release has been riddled with problems.

> **hwttdz said:**
> If you're unwilling to encounter any bugs it's probably best to sick with as minimalistic and stable a distribution as possible.  A good first step would be only using LTS releases and of course only using supported hardware.

I've been working with Linux since ~'97-'98, and this is seriously the worst upgrade/release I've ever dealt with.  Honestly, fighting with the occasional weird conflicts or problem is fine, but this release is just loaded with them.

I am still interested in my original question, because I've been satisfied with Ubuntu up to now.  Is this release just some strange anomaly, or will future releases be more stable/tested?

> **Senesence said:**
> 
PS: Tell me what your problems are; maybe I, or someone else here, could help.

Thanks -- I still have 9.10 on my other PC, so if it stays reasonably well-behaved with the occasional quirk I'll be sure to post bug reports/etc.  It's just the "everything fails at once, and one fix causes another bug" frustration with 9.10 on my current machine that's made me not even want to try anymore.

---

### Post by vcj88 on 2009-11-16
> **Senesence said:**
> Yea, I sort of feel the same.

Things were fine after the upgrade, for a few days at least, but then I got some major filesystem corruption, and fsck couldn't fix it, so ultimately I had to reinstall.

However, even with the reinstall, I got a whole new set of problems, some of which I resolved, but installing the nvidia drivers breaks the X server now, so.........yea, I get the feeling that this release has some issues.

PS: Tell me what your problems are; maybe I, or someone else here, could help.

Had the same where it had file corruption after afew days but fsck came through for me. Then grub completely stopped working and I couldn't boot so I switched back to 9.04 and now 9.04 won't recognize my wireless card even though it did the first time I installed it a while back and none of the fixes I've found work. Pretty sure I will be switching to Debian or Scientific by the end of the day.

---

### Post by arnab_das on 2009-11-16
its always better to go for a fresh installation than to upgrade.

---

### Post by Senesence on 2009-11-16
> **arnab_das said:**
> its always better to go for a fresh installation than to upgrade.

Unfortunately, this is true.

However, I must say, for a Linux distribution that produces new versions at such a quick pace, that's almost unforgivable, and something that should be resolved first.

If there is no way to do so, then Ubuntu should simply create a separate /home partition on initial install, and then every subsequent upgrade can be a fresh system install, with a script that just mounts your /home partition.

Although, I don't see how wiping the system files, while leaving the user data intact, is so much more difficult.

....In either case, this is a big problem.

---

