---
title: "Does Firefox run slow in Linux?"
date: 2009-05-09
forum: The Cafe
---

### Post by dspari1 on 2009-05-09
Firefox in virtual box /w XP is running circles around Firefox in Linux. What gives?

---

### Post by monsterstack on 2009-05-09
I think it has something to do with Linux Firefox's use of libraries. A possibly speedier alternative you might want to try is [Swiftfox]("http://getswiftfox.com/") [getswiftfox.com].

---

### Post by Viranh on 2009-05-09
Not that I've seen. Windows starts firefox so sloooowly. It seems to prefetch a lot of things. I do not notice a speed difference once they're started. Is there some way to truly measure this? I've also noticed that Windows and linux seem to handle my wireless connections differently, affecting download speeds and firefox's speed.

---

### Post by RedSingularity on 2009-05-09
No problem here.

---

### Post by Sealbhach on 2009-05-09
I use Firefox 3.6a1. I think the 3.0 version is a lot slower. The new 3.5 version will be zippier.

.

---

### Post by dspari1 on 2009-05-09
> **Sealbhach said:**
> I use Firefox 3.6a1. I think the 3.0 version is a lot slower. The new 3.5 version will be zippier.

.

yeah, I'm using 3.0.10

I may try to change to a beta version if it improves speed.

---

### Post by Einsamkeit on 2009-05-09
I get better performances with FF from Ubuntu than XP, no slowing down, hanging up or anything.
Altho some sites may or may not make the whole thing cranky, especially with graphic-intensive ads, with flash and everything.. Hell, those even make desktop computer grind its teeth.

EDIT: Forgot to add, using 3.0.10 on both machines.

---

### Post by Ewingo401 on 2009-05-09
I wouldn't say the Linux version of Firefox is slow.  But I have noticed that the Windows version of Firefox running through WINE is noticably faster, at least on my system.  I'm hoping Firefox 3.5 speeds up the Linux version a bit.

---

### Post by thisllub on 2009-05-10
Addons make a difference too.
Opera and Midori are both faster.

---

### Post by RiceMonster on 2009-05-10
I've never noticed any difference. I don't know what people are talking about saying it's faster on Windows.

---

### Post by x33a on 2009-05-10
firefox starts slow both on windows and ubuntu, and i don't see much difference in memory usage on either platforms.

---

### Post by medicalystoned on 2009-05-10
my last remaining windows machine has 1 gig of ram, the kubuntu machine i am on right now has 256k, and it runs circles around windows. I have all kinds of add-ons and use speed dial on my firefox with linux, and basic ff with windows, linux smokes windows, hands down.............. peace

---

### Post by dspari1 on 2009-05-10
> **RiceMonster said:**
> I've never noticed any difference. I don't know what people are talking about saying it's faster on Windows.

I notice people saying that even Firefox with wine seems to run faster. I think there is a problem with the 3.0.10 release. I'm not sure. Hopefully, the next major release of Firefox will be as fast as its Windows counterpart.

---

### Post by stwschool on 2009-05-10
Swiftfox is your friend. I've just installed it, it's fast. Don't worry, it picks up your old history, add-ons, bookmarks, etc and you can have both on your machine at once so you won't lose anything. Deb packages are available.

---

### Post by monsterstack on 2009-05-10
> **stwschool said:**
> Swiftfox is your friend. I've just installed it, it's fast. Don't worry, it picks up your old history, add-ons, bookmarks, etc and you can have both on your machine at once so you won't lose anything. Deb packages are available.

He's right, you know.

---

### Post by sports fan Matt on 2009-05-10
I wonder if swiftfox is installed, it would break if Firefox was uninstalled

---

### Post by dspari1 on 2009-05-10
> **monsterstack said:**
> He's right, you know.

I'm going to install it.

---

### Post by itreius on 2009-05-10
The actual browser doesn't feel that different, but tests (Sunspider, and other benchmarks) suggest that the Linux version really is slower than the Windows and Mac OS counterparts.

---

### Post by HavocXphere on 2009-05-10
> **dspari1 said:**
> Firefox in virtual box /w XP is running circles around Firefox in Linux. What gives?
I've read about that...but I don't see it. And I'm pretty sure that the original report on this focused on Javascript performance.

IMO the *nix FF starts faster than win FF.

One thing I can say though is that FF starts *way* faster on Gnome than on KDE. As in very noticeably faster.

Slight de-rail: I wonder whether ext4 makes a difference in this...

---

### Post by stwschool on 2009-05-10
> **monsterstack said:**
> He's right, you know.
I do that a lot ;)

---

### Post by dLeon on 2009-05-10
FF Linux & FF Windows work perfectly for me. Speed from clean start equally same, both never crash. Copied FF Windows to my Ubuntu (or the other way around) account also doesn't make any big threats. I also happen to use FF extensions I downloaded myself, not from Ubuntu repos.
If its problematic, I think the main problem is from Firefox build itself, not because we're using Windows or Linux.

---

### Post by stwschool on 2009-05-10
> **sox fan Matt said:**
> I wonder if swiftfox is installed, it would break if Firefox was uninstalled
Probably not given how package management works on Ubuntu. Don't forget, most packages will list their dependencies so that nothing breaks, so if you uninstall firefox, it'll take firefox off, but if apps are dependent upon parts of it, they'll be left behind (that's my understanding anyway).

Also, opening up the package and looking at installed files, it looks like it puts content in the /usr/lib/swiftfox/ folder rather than /usr/lib/firefox/ or anything similar, so the two can co-exist quite happily. The only caveat is that launching firefox now seems to launch swiftfox, which I didn't expect, and may indicate some links between them.

---

### Post by jespdj on 2009-05-10
> **ricemonster said:**
> i've never noticed any difference. I don't know what people are talking about saying it's faster on windows.

+1 ! It runs fine on Ubuntu, just like on Windows. I don't notice any difference. Maybe benchmarks show that it's slower, but it's not something that's really noticeable.

What exactly is slower according to the people who say so? Displaying pages? Loading pages?

---

### Post by Jay_Bee on 2009-05-10
For me JavaScript performance is noticeably slower than in FF on windows.
Good example would be [www.chromeexperiments.com]("http://www.chromeexperiments.com") which is laggy on linux but not on windows.

---

### Post by dLeon on 2009-05-10
> **Jay_Bee said:**
> For me JavaScript performance is noticeably slower than in FF on windows.
Good example would be [www.chromeexperiments.com]("http://www.chromeexperiments.com") which is laggy on linux but not on windows.

No... I test the site you mention; gone through everywhere there (not all), the site just find. It load in speeding bullet on my system.
Are you sure not just because your connection?

BTW, Is that page somekind of Chrome test site?

---

### Post by Bölvaður on 2009-05-10
it must be a new update that did it. Firefox began to be slow for me like 3 days ago.

---

### Post by dLeon on 2009-05-10
> **Bölvaður said:**
> it must be a new update that did it.

Complete version please...

Mine is Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.10) Gecko/2009042523 Ubuntu/9.04 (jaunty) Firefox/3.0.10

---

### Post by LightB on 2009-05-10
> **medicalystoned said:**
> the kubuntu machine i am on right now has 256k

Wow, that's amazing!

---

### Post by LightB on 2009-05-10
> **Jay_Bee said:**
> For me JavaScript performance is noticeably slower than in FF on windows.
Good example would be [www.chromeexperiments.com]("http://www.chromeexperiments.com") which is laggy on linux but not on windows.

If you're talking about the flash pages, that's flash, no need to blame firefox. It's adobe's fault. Yes, flash is slow on linux.

---

### Post by Skripka on 2009-05-10
> **medicalystoned said:**
> my last remaining windows machine has 1 gig of ram, the kubuntu machine i am on right now has 256k

You must mean megabytes.  *buntu will not even install on a system with 256k, and it certainly will not run.

---

### Post by Skripka on 2009-05-10
> **thisllub said:**
> Addons make a difference too.
Opera and Midori are both faster.

Any Webkit based browser will be faster....especially the minimalist ones.


Heck,  run Konqueror with the Webkit backend instead of KHTML and it is just as fast as Arora or Midori.

---

### Post by stwschool on 2009-05-10
> **LightB said:**
> If you're talking about the flash pages, that's flash, no need to blame firefox. It's adobe's fault. Yes, flash is slow on linux.
They ain't Flash, they're javascript. Pure javascript. People underestimate what you can do with it, personally I'm a huge fan of it and use it extensively in the web applications that I build.

---

### Post by RATM_Owns on 2009-05-10
No.

(I compiled my own Firefox Beta with PGO)

---

### Post by Redundant Username on 2009-05-10
In Windows, it doesn't lock up and freeze all the time. I might try the beta to see if it is more stable.

---

### Post by LightB on 2009-05-10
> **stwschool said:**
> They ain't Flash, they're javascript. Pure javascript. People underestimate what you can do with it, personally I'm a huge fan of it and use it extensively in the web applications that I build.

I clearly saw flash on some of those experiment pages.

---

### Post by joey-elijah on 2009-05-10
> **RiceMonster said:**
> I've never noticed any difference. I don't know what people are talking about saying it's faster on Windows.

Firefox launches in less than 0.5 second in Windows 7, takes about 5 seconds to launch in Ubuntu x64... Midori, Epiphany, Opera etc all take less than a second to launch in Ubuntu. 

As for insulting me and anyone else who doesn't agree with you as "not knowing what we're talking about" there are benchmarks that prove firefox run through WINE runs quicker than Firefox on Ubuntu proper. 

[http://tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox](http://tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox)

---

### Post by stwschool on 2009-05-10
Ok I may have missed that, in which case I stand corrected, but most of them are 100% javascript, the point being to demonstrate the power of javascript in Chrome's JS engine.
As I said before, people seem to think that rich animated and interactive content is only possible with plugins like flash but javascript is incredibly powerful once you start to really mess with it, especially when you play with AJAX as well.

---

### Post by qamelian on 2009-05-10
> **joey-elijah said:**
> Firefox launches in less than 0.5 second in Windows 7, takes about 5 seconds to launch in Ubuntu x64... Midori, Epiphany, Opera etc all take less than a second to launch in Ubuntu. 

As for insulting me and anyone else who doesn't agree with you as "not knowing what we're talking about" there are benchmarks that prove firefox run through WINE runs quicker than Firefox on Ubuntu proper. 

[http://tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox](http://tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox)
And those benchmarks may not reflect performance on every machine. On both of my systems at home, there is no noticeable difference in performance in Firefox between Windows or Linux, and it launches and performs much slower in wine. That may not be everyone's experience, but it is mine.

---

