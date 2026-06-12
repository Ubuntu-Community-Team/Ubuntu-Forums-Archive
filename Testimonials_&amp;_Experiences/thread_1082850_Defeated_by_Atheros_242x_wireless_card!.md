---
title: "Defeated by Atheros 242x wireless card!"
date: 2009-02-28
forum: Testimonials &amp; Experiences
---

### Post by yeats on 2009-02-28
I'm a *committed* Ubuntu/Kubuntu user who will never willingly go back to any proprietary operating system, but I have made the decision to return to Windows Vista on my wife's computer.  I've done so only after reaching my personal limit time after time when trying to get the Atheros 242X wireless card to "just work."  My wife is a supporter of Free and Open Source Software herself, but she is also much more of a pragmatist than I am.  She has used Ubuntu as her primary OS (dual-booting with Vista) several times now, and for various reasons (usability, inability to configure it to her preferences), she has given up, much to my chagrin.  I don't blame her too much.  Besides, she's a student who needs a working, reliable computer.  Well now *I* am the one making the decision, because whatever I do to fix this problem will not work.  Or worse, it will *sometimes* work and *sometimes* not.  I'm sure someone here on the forum could talk me through a solution that would "stick," but I am honestly done with this issue!

I'll explain the following, before people make a lot of assumptions:

- I use Kubuntu on three computers that I have no plans to change.  I am completely satisfied with its performance and *truly enjoy* using them for both work and leisure.

- I understand what issues are involved with this - mainly that there is no Open Source driver from the manufacturer and that there are/may be legal problems with Ubuntu having the working modules installed by default

- I also understand that kernel upgrades require that you re-compile the drivers into the new kernel

I'll also say that if this were my own computer that I would continue struggling with it, but until Atheros cards are supported "out-of-the-box" for Ubuntu, there's not much of a chance we'll try again.

---

### Post by wolfen69 on 2009-02-28
it's actually pretty easy to get atheros cards working, but i'll just leave it alone and let you (or your wife) enjoy the pleasure of windows.

---

### Post by solwic on 2009-02-28
> **wolfen69 said:**
> it's actually pretty easy to get atheros cards working, but i'll just leave it alone and let you (or your wife) enjoy the pleasure of windows.

That's all you can do.  :)

@OP:  Good luck with Windows.

---

### Post by Tamlynmac on 2009-02-28
> chrissharp123
Or worse, it will *sometimes* work and *sometimes* not. I'm sure someone here on the forum could talk me through a solution that would "stick," but I am honestly done with this issue!

The choice is yours and there's no need to justify it. There in lies one of the true benefits of Ubuntu - no cost to have tried.
Of course there may be other options. But, you've made your decision and hopefully that decision will reduce your stress and frustration levels.

Hope this really was your choice, as this is not an assistance section of the forum.

Good Luck and Enjoy

---

### Post by yeats on 2009-02-28
> it's actually pretty easy to get atheros cards working, but i'll just leave it alone and let you (or your wife) enjoy the pleasure of windows.

Obviously this is one of those cases where it's easy once you know how to do it.  When the methods I followed worked, it *was* easy.  Obviously they didn't always work, hence my decision.


> The choice is yours and there's no need to justify it. There in lies one of the true benefits of Ubuntu - no cost to have tried.
Of course there may be other options. But, you've made your decision and hopefully that decision will reduce your stress and frustration levels.

Hope this really was your choice, as this is not an assistance section of the forum.

Good Luck and Enjoy 

Thanks for the support - it was my choice.  I'm just sharing my experience for the sake of conversation.

---

### Post by solwic on 2009-02-28
> **chrissharp123 said:**
> Obviously this is one of those cases where it's easy once you know how to do it.  When the methods I followed worked, it *was* easy.  Obviously they didn't always work, hence my decision.


Keep in mind, too, that you were using Kubuntu, not Ubuntu.  Using Kubuntu is akin to raising your arms to the sky and shouting to the Universe, "Please, O Universe, give me computer trouble!"

In any case, good luck.  Using what works for you is always the best decision.  :)

---

### Post by yeats on 2009-02-28
> Keep in mind, too, that you were using Kubuntu, not Ubuntu. Using Kubuntu is akin to raising your arms to the sky and shouting to the Universe, "Please, O Universe, give me computer trouble!"

Actually, the computer is question was running regular Ubuntu.

I have found that Kubuntu 8.04 is quite stable and reliable.  Kubuntu 8.10 is more like what you describe, though I'm now running it with KDE 4.2 and it is quite enjoyable so far.

---

### Post by 3rdalbum on 2009-03-01
Most Atheros cards these days do work. I imagine you didn't come this far and not try the 'ath5k' driver from the Intrepid Backports Modules package? It's far superior (in compatibility and speed) to the normal ath_pci driver that ships with Ubuntu.

---

### Post by binbash on 2009-03-01
Did you read those ?: 

[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html)
[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html)

AND I AGREE WITH YOU, ar242x is a big headache

---

### Post by yeats on 2009-03-01
> Most Atheros cards these days do work. I imagine you didn't come this far and not try the 'ath5k' driver from the Intrepid Backports Modules package? It's far superior (in compatibility and speed) to the normal ath_pci driver that ships with Ubuntu.

Yep - that was the way I got it working.  It would then stop working and continue to not work until I went all the way around the block again trying several different methods.  This was *maddening* to me.  And to top it off, it would work for weeks or months - just long enough for me to have forgotten what I'd done previously :-).

> Did you read those ?:

[http://www.ubuntu-inside.me/2009/02/...orking_25.html](http://www.ubuntu-inside.me/2009/02/...orking_25.html)
[http://www.ubuntu-inside.me/2009/02/...orking_27.html](http://www.ubuntu-inside.me/2009/02/...orking_27.html)

I don't know if I read those particular ones, but the first link points to the way I did it last.  I don't think I ever dealt with ndiswrapper in my explorations, so I don't think I came across the second link.  Thanks for the suggestions - I'll keep them in mind if my wife goes crazy with Vista and wants to return to the fold :-).

> AND I AGREE WITH YOU, ar242x is a big headache 

Thanks so much for acknowledging this.  Seems that most people responding on this post find it to be no problem - I obviously did.  It's actually a load off not having to worry about it anymore.  Two of my other (K)ubuntu installations are desktops and the laptop I use is an Ubuntu-friendly Dell.  I've never had such issues with any of them.  If my wife's computer were my only station I would have learned enough about the issue to master it - for now I'll stick to Linux topics I'm *actually interested in*.

I'll also mention that while I sincerely appreciate the suggestions people have offered, I truly did mean to report this as a shared experience.  I wasn't passive-aggressively fishing for help, as I've seen others do.  (To be clear) :-)

---

### Post by stchman on 2009-03-02
> **chrissharp123 said:**
> I'm a *committed* Ubuntu/Kubuntu user who will never willingly go back to any proprietary operating system, but I have made the decision to return to Windows Vista on my wife's computer.  I've done so only after reaching my personal limit time after time when trying to get the Atheros 242X wireless card to "just work."  My wife is a supporter of Free and Open Source Software herself, but she is also much more of a pragmatist than I am.  She has used Ubuntu as her primary OS (dual-booting with Vista) several times now, and for various reasons (usability, inability to configure it to her preferences), she has given up, much to my chagrin.  I don't blame her too much.  Besides, she's a student who needs a working, reliable computer.  Well now *I* am the one making the decision, because whatever I do to fix this problem will not work.  Or worse, it will *sometimes* work and *sometimes* not.  I'm sure someone here on the forum could talk me through a solution that would "stick," but I am honestly done with this issue!

I'll explain the following, before people make a lot of assumptions:

- I use Kubuntu on three computers that I have no plans to change.  I am completely satisfied with its performance and *truly enjoy* using them for both work and leisure.

- I understand what issues are involved with this - mainly that there is no Open Source driver from the manufacturer and that there are/may be legal problems with Ubuntu having the working modules installed by default

- I also understand that kernel upgrades require that you re-compile the drivers into the new kernel

I'll also say that if this were my own computer that I would continue struggling with it, but until Atheros cards are supported "out-of-the-box" for Ubuntu, there's not much of a chance we'll try again.

I have the same wireless card on my Aspire One and it was very easy to get it working.

I have a tutorial on getting the wireless working on an AA1.  The same thing should work on other PCs with the same wireless card.

[http://www.stchman.com/aspire_one_intrepid.html](http://www.stchman.com/aspire_one_intrepid.html)

---

### Post by liamnixon on 2009-03-02
I have that same card, so I feel your pain.  Trying to get it to work in Ubuntu was my introduction to Linux.

That being said, it works out of the box in other distros.  I'm on Slackware right now and all I had to do was install wicd and it worked.  It also worked in Fedora and Mandriva.

---

### Post by wolfen69 on 2009-03-02
> **liamnixon said:**
> It also worked in Fedora and Mandriva.
mandriva has pretty good hardware detection. unfortunately, some people are like, "it's ubuntu, or back to windows". without giving another distro a chance. god help them.

---

### Post by Crafty Kisses on 2009-03-03
> **jrock612 said:**
> Keep in mind, too, that you were using Kubuntu, not Ubuntu.  Using Kubuntu is akin to raising your arms to the sky and shouting to the Universe, "Please, O Universe, give me computer trouble!"

In any case, good luck.  Using what works for you is always the best decision.  :)

I think Kubuntu is great, if you're basing that statement off using KDE 4 with Kubuntu, then I totally agree. If you're using KDE 4.1, then I'm not sure what the problem is, KDE 4.1 for me anyway was great and painless. Took a little bit of configuring, but after that Kubuntu ran great and I didn't have any issues.

---

