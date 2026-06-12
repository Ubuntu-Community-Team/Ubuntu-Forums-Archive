---
title: "Linus announces linux 3.0"
date: 2011-05-29
forum: The Cafe
---

### Post by wolfen69 on 2011-05-29
[http://www.phoronix.com/scan.php?page=news_item&px=OTUwMg](http://www.phoronix.com/scan.php?page=news_item&px=OTUwMg)

---

### Post by wojox on 2011-05-30
I was just about to post this. Good thing I search first. [URL="http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=55922c9d1b84b89cb946c777fddccb3247e7df2c"]except there are various scripts that really know that there are
three numbers, so it calls itself "3.0.0-rc1".[/URL]

---

### Post by Aquix on 2011-05-30
The world have gone completely version number crazy!!

---

### Post by wojox on 2011-05-30
> **Aquix said:**
> The world have gone completely version number crazy!!

Could have been numbers and animals. :p

---

### Post by judge jankum on 2011-05-30
I got one of them there version numbers" dunno wut it is, but I got one!!!

---

### Post by JDShu on 2011-05-30
Well dropping the 2.6 prefix makes sense.... though I wonder if they should have just kept counting up 40,41,42,43.. etc,  seems as good a system as any other.

---

### Post by Artemis3 on 2011-05-30
Well, Linus has to obey "the voice in his head"... :)
He could have also gone with 2.8, or 2.7; but whatever. There is no rationale about version numbers anymore, it used to be middle number odd for development and pair for release. Funny thing is he abandoned the odd numbers altogether, but then whats the point? better to keep 2 numbers instead, which now appears to be the case.

Another option would be to go with dates, ubuntu style, but this is fine.

Other software should take a hint about very silly versioning schemes.

And yes, after 3.9 can come 3.10, and after 3.99 can come 3.100. It is infinite, when the developer thinks a major change comes, just change the first number. No need to use 0.1.0.3gamma-rc-whatever.

---

### Post by LowSky on 2011-05-30
its a funny time in software development. Everyone wants drastic change. I see the kernel number as a sorta joke to projects like Gnome and KDE.

---

### Post by 3rdalbum on 2011-05-30
> **LowSky said:**
> its a funny time in software development. Everyone wants drastic change. I see the kernel number as a sorta joke to projects like Gnome and KDE.

Before Wine released their 1.0 version, their versions were numbered 0.9.34 - as though they were so-very-slowly getting towards the 1.0 mark. I thought that was funny, and I'm glad Linus is making this a 3.0 version because round numbers are less funny than big decimal places.

---

### Post by 3Miro on 2011-05-30
Any big changes, the article doesn't really say anything about what would be includes (apart from cleaning old code). 2.4 to 2.6 was a huge change with the dynamic modules, what would 3.0 bring?

---

### Post by Barrucadu on 2011-05-30
Nothing, the point of it is that it's not a huge change, it's just a new version number because Linux wants one.

---

### Post by Zero2Nine on 2011-05-30
Blame Google! :P Chrom(e)(ium) that now has reached version 11.alotofdigitsafterit seems to have started this crazy version number battle. Firefox will adept this kind of numbering scheme now and even Linux... why?

---

### Post by Hwæt on 2011-05-30
> **Barrucadu said:**
> Nothing, the point of it is that it's not a huge change, it's just a new version number because Linux wants one.

Linux 2.6.40 is majorly different from Linux 2.0, or even just 2.4. It's been long overdue that the version gets ticked up.

---

### Post by Phrea on 2011-05-30
> we are very much *not* doing a KDE-4 or a Gnome-3 here. No breakage, no special scary new features, nothing at all like that.

:lolflag:

---

### Post by 3Miro on 2011-05-30
> **Hwæt said:**
> Linux 2.6.40 is majorly different from Linux 2.0, or even just 2.4. It's been long overdue that the version gets ticked up.

2.6.x was a big difference from 2.4.x

How would 3.0 be different from 2.6.x, doesn't seem like anything major is coming.

---

### Post by Hwæt on 2011-05-30
> **3Miro said:**
> 2.6.x was a big difference from 2.4.x

How would 3.0 be different from 2.6.x, doesn't seem like anything major is coming.

Well, compared to the original 2.6, 2.6.40 is already quite different. I mean, not as different as 2.4 to 2.6, but still enough to warrant that the version be changed. Who knows, maybe Linus has some surprise planned, too.

---

### Post by Phrea on 2011-05-30
Have you guys even read the article?

---

### Post by Zero2Nine on 2011-05-30
> **3Miro said:**
> 2.6.x was a big difference from 2.4.x

How would 3.0 be different from 2.6.x, doesn't seem like anything major is coming.

I think it would just raise expectations too much. Suddenly there is Linux 3.0 it'll look like something spectacular. People might expect much more hardware support and all power issues gone etc. I still cannot see the benefit of changing the version numbering system.

I imagine conversations:
"I hate that Linux stuff it's for nerds blablabla Windows is so much better" 
"Wait! now there is Linux 3.0" 
"What? I'll immediately switch, delete al my Windows partitions and throw my macbook out of the window"

---

### Post by Hwæt on 2011-05-30
> **Phrea said:**
> Have you guys even read the article?

Yes

[quote=Linus]
So what are the big changes?

NOTHING. Absolutely nothing. Sure, we have the usual two thirds driver changes, and a lot of random fixes, but the point is that 3.0 is *just* about renumbering, we are very much *not* doing a KDE-4 or a Gnome-3 here.
[/quote]

---

### Post by jerenept on 2011-05-30
> **3rdalbum said:**
> Before Wine released their 1.0 version, their versions were numbered 0.9.34 - as though they were so-very-slowly getting towards the 1.0 mark. I thought that was funny, and I'm glad Linus is making this a 3.0 version because round numbers are less funny than big decimal places.

VLC did the same thing.

---

### Post by Hwæt on 2011-05-30
> **jerenept said:**
> VLC did the same thing.

Gotta love the asymptotic behavior of some open source projects, especially WINE. :lol:

---

### Post by gnomeuser on 2011-05-30
Linus lies, there is something huge in 3.0. They finally fixed that annoying kswapd taking 100% CPU and making the machine unusable for up to double digit minutes issue.

I, for one, welcome my incremented kernel version overlord.

I already submitted the SRU request to have the fix applied to Natty (and likely below as the fix is fairly simple, ~8 lines)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/789982](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/789982)

---

### Post by Lucradia on 2011-05-31
I'm surprised no one blatantly bashed Linux 3.0.0 yet that it doesn't have multi-GPU Support:

> The Linux 3.0 kernel will also lack a number of features including the Reiser4 file-system, the VIA KMS/DRM driver, an accelerated Poulsbo / PowerVR DRM driver, multi-GPU rendering, and various other long sought after items. The major Linux kernel power regressions have yet to be resolved as well, but that's still on my TODO list to finish bisecting those two nasty bugs.

---

### Post by Dustin2128 on 2011-05-31
I believe I will start calling this idiotic versioning number e-peen jockeying the "chrome syndrome".

---

### Post by Lucradia on 2011-05-31
> **Dustin2128 said:**
> I believe I will start calling this idiotic versioning number e-peen jockeying the "chrome syndrome".

+1 to that. Chrome made a mess.

---

### Post by Artemis3 on 2011-05-31
> **Lucradia said:**
> I'm surprised no one blatantly bashed Linux 3.0.0 yet that it doesn't have multi-GPU Support:

[http://www.phoronix.com/scan.php?page=news_item&px=ODA1OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODA1OQ)

I find that feature particularly unappealing. I don't believe in bundling 2 different gpus in a netbook and constantly switching one to the other. Better make a single gpu consume less when its not taxed. It doesn't feel right at all.

If you thought this had anything to do with sli or crossfire, you were very wrong.

---

### Post by Lucradia on 2011-05-31
> **Artemis3 said:**
> If you thought this had anything to do with sli or crossfire, you were very wrong.

Then why does the article make it seem that way >_>

---

### Post by Bandit on 2011-05-31
Going to 3.0.0 without any changes drives me crazy. Although if its had all those extra ham radio drivers & etc.. removed into a cleaner package to build on, then that is something in my book worth going to 3.0 on.

---

### Post by trizrK on 2011-05-31
'Bout time! jk

---

### Post by gnomeuser on 2011-05-31
> **Dustin2128 said:**
> I believe I will start calling this idiotic versioning number e-peen jockeying the "chrome syndrome".

And yet with the ever increasing 2.6.x releases you had companies claiming to ship 2.6 kernels, but being 7 years behind.

Aside that we are now very far from the 2.6 kernel released many years ago. 

I would though have adopted a 201X.[1-4] scheme to reflect a state in time easily and it would reflect the defacto standard that we do 4 kernels a year - every 3 months. It's been pretty regular for a while now. I think such a scheme would fit nicely with a foundational component.

---

### Post by ssam on 2011-05-31
with distributed version control systems it is easy to merge new features whenever they are ready. there is no benefit from saving up all the new stuff for a few years and releasing it all at once (unless you need to persuade users to pay money again).

most opensource projects have transitioned to this workflow (it would be nice if some others, eg gimp, would do the same). at this point all you need is numbers that increment. its a bonus if they are easy to write, so reaching huge numbers, or having too many decimal places is a pain (eg TeX).

date based numbers are nice, but i guess the enterprise distros would be unhappy.

---

### Post by Dustin2128 on 2011-05-31
> **gnomeuser said:**
> And yet with the ever increasing 2.6.x releases you had companies claiming to ship 2.6 kernels, but being 7 years behind.

Aside that we are now very far from the 2.6 kernel released many years ago. 

I would though have adopted a 201X.[1-4] scheme to reflect a state in time easily and it would reflect the defacto standard that we do 4 kernels a year - every 3 months. It's been pretty regular for a while now. I think such a scheme would fit nicely with a foundational component.
I agree with that, but a version skip to 3.0 was unnecessary. 2.8 would have sufficed.

---

### Post by RiceMonster on 2011-05-31
> **Dustin2128 said:**
> I agree with that, but a version skip to 3.0 was unnecessary. 2.8 would have sufficed.

Does it really matter, though?

---

