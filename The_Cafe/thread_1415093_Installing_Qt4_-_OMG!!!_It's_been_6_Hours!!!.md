---
title: "Installing Qt4 - OMG!!! It's been 6 Hours!!!"
date: 2010-02-24
forum: The Cafe
---

### Post by madmax.santana on 2010-02-24
I am really bored now... I took on building qt4 package manually through configure, make and make install...

Well configure took some nice 30 minutes!!! 

But make is taking a record time! 6 darn hours!!! And it doesn't even have a progress meter so that I can have a little piece of satisfaction by knowing the estimated time it would take!!!

---

### Post by Tibuda on 2010-02-24
May I ask why are you compiling it from source?

I think it is normal for something as big as a toolkit to take all that time to compile.

---

### Post by jdong on 2010-02-24
On my dual 3.06GHz machine, Qt4 takes on the order of 6 hours to build. Definitely it's a half-day / whole-day ordeal.

---

### Post by Simian Man on 2010-02-24
Now you know why so few people use Gentoo :).

---

### Post by madmax.santana on 2010-02-24
> **jdong said:**
> On my dual 3.06GHz machine, Qt4 takes on the order of 6 hours to build. Definitely it's a half-day / whole-day ordeal.
Mine is solo 3.0GHz!!! Means it's bound to take around 12 hrs? :(

---

### Post by madmax.santana on 2010-02-24
> **danielrmt said:**
> May I ask why are you compiling it from source?

I think it is normal for something as big as a toolkit to take all that time to compile.
I was studying a tutorial! Maybe it is an old one, when possibly there was no installer available... But that is what it directed me to do. Unlucky me!

---

### Post by madmax.santana on 2010-02-24
> **Simian Man said:**
> Now you know why so few people use Gentoo :).
???

You Mean in Gentoo you gotta compile everything from source??? No packages? Oh man!!! That's mean...

---

### Post by kellemes on 2010-02-24
> **madmax.santana said:**
> ???

You Mean in Gentoo you gotta compile everything from source??? No packages? Oh man!!! That's mean...

And not true.. binary versions of the bigger packages are available.

---

### Post by RiceMonster on 2010-02-24
> **Simian Man said:**
> Now you know why so few people use Gentoo :).

That's what I was thinking.

---

### Post by chucky chuckaluck on 2010-02-24
wow! reading this thread makes me want to do it, too.

---

### Post by ~sHyLoCk~ on 2010-02-24
> **chucky chuckaluck said:**
> wow! reading this thread makes me want to do it, too.

I hope you are joking.

---

### Post by chucky chuckaluck on 2010-02-24
> **~sHyLoCk~ said:**
> I hope you are joking.

me?

---

### Post by ~sHyLoCk~ on 2010-02-24
> **chucky chuckaluck said:**
> me?

oh right.. :P

---

### Post by jdong on 2010-02-24
> **madmax.santana said:**
> Mine is solo 3.0GHz!!! Means it's bound to take around 12 hrs? :(


I wouldn't hold your breath for the rest of the day. Have it work in the background and check back on it after several hours. Especially since most of the single-core 3.0GHz processors that come to mind are GHz-for-GHz slower than the core 2 duo 3.06's microarchitecture.

---

### Post by madmax.santana on 2010-02-24
> **jdong said:**
> I wouldn't hold your breath for the rest of the day. Have it work in the background and check back on it after several hours. Especially since most of the single-core 3.0GHz processors that come to mind are GHz-for-GHz slower than the core 2 duo 3.06's microarchitecture.
Yeah, since they are Gigs of Gigs Hertz slower, I am almost unable to do anything on my system... For 6 bloody hours, my GDM has been hanging from time to time and I was thinking like "Oh maybe I should press Ctrl+Alt+Del and restart explorer.exe" :) :) :)

Silly thought, then it occurred to me, "If it were windows, compiling a toolkit as large might have as well taken a week... "

Hahaha. Anyway, Windows solves these problems by doing installations using binaries... And sometimes they crash, too!!! :)

---

### Post by Tibuda on 2010-02-24
> **madmax.santana said:**
> Hahaha. Anyway, Windows solves these problems by doing installations using binaries... And sometimes they crash, too!!! :)

That's why I asked why are compiling it, because there are binaries available in repositories (assuming you are not using Gentoo).

---

### Post by madmax.santana on 2010-02-24
> **danielrmt said:**
> That's why I asked why are compiling it, because there are binaries available in repositories (assuming you are not using Gentoo).
And that's why I already answered that on the previous page... :)

Again: I was following instructions in a tutorial. It was an old one and when it was written there were probably no binaries available... It told me to compile the source using configure, make and make install... By the tone of the tutorial it wasn't obvious that it could take 12 hours just building... :) It was after I had already started make, I came to know that I could use simple binaries... :)

Next time, I will definitely install through binaries.. Man, 12 hours... I'm gonna turn into wax...

---

### Post by NoaHall on 2010-02-24
> **madmax.santana said:**
> And that's why I already answered that on the previous page... :)

Again: I was following instructions in a tutorial. It was an old one and when it was written there were probably no binaries available... It told me to compile the source using configure, make and make install... By the tone of the tutorial it wasn't obvious that it could take 12 hours just building... :) It was after I had already started make, I came to know that I could use simple binaries... :)

Next time, I will definitely install through binaries.. Man, 12 hours... I'm gonna turn into wax...

So not only are you configuring from source unneed, but you're also installing a old version?
Nice one, dude :)

---

### Post by Warpnow on 2010-02-24
Most people don't use the make flag to use both cores when compiling. Very possible that it will be done soon for you.

---

### Post by madmax.santana on 2010-02-24
> **NoaHall said:**
> So not only are you configuring from source unneed, but you're also installing a old version?
Nice one, dude :)
No no no!!! The source that I downloaded was the latest... From Trolltech website... It's just the instructions that I am following are old!!! :)

They might have kept in mind the source which did not have a relative binary package available. So they told to "download the source from Trolltech website and do this this this..."...
I downloaded the source which, of course was the latest, and started acting on the instructions... It was after I had rum "make" command that I came to know that a relative binary package was also available on the same page from where I downloaded the source. :(
And afterwards, searching the forums, I came to know that besides the binaries provided by the Trolltech website, Ubuntu repos contained a full fledge package named libqt4-dev... :) That is why I said earlier, "UNLUCKY ME"... Or maybe I should say "IMPATIENT ME"... Hahaha

---

### Post by madmax.santana on 2010-02-24
> **Warpnow said:**
> Most people don't use the make flag to use both cores when compiling. Very possible that it will be done soon for you.
That is, if I have two cores...Whereas I have only one core... It is an old PC...

Intel 915 Desktop Board
Pentium IV 3.0GHz Processor
1 GiB RAM
Onboard Intel Graphics Card
Onboard Realtek Sound Card

:) Sounds pretty much like the 1999-2003s! But I am happy with Ubuntu specially which manages my system so nicely that I don't even feel like I am using an old machine... Probably Windows Vista or 7 wouldn't even run on this machine... But Ubuntu sprints!!!

I have an HP HDX 16 Laptop as well... I have Windows Vista and Linux Mint Helena installed on it... Ubuntu on my old i386 is faster than the 64-bit Vista on my Dual Core Lappy!!! :)

---

### Post by jdong on 2010-02-24
Before all the compile-from-source flaming commences, there certainly can be legitimate reasons why someone would want the latest Trolltech version of Qt4 compiled from source -- for example, if a book is based off a certain release, it's less confusing for a beginner to be using the exact same. Or, if one is running an old release of Ubuntu without that particular version of Qt4 available.


On a Netburst (Pentium 4) 3.0, I'd expect this compile to take anywhere from 12 to 24 hours and heat up your room pretty well. Qt4 is a massive toolkit, though rewardingly comprehensive :)

---

### Post by madmax.santana on 2010-02-24
IT'S DONE!!! 

Complete 12 Hrs 40 Mins (give or take a few seconds) :)

---

### Post by dragos240 on 2010-02-24
> **madmax.santana said:**
> IT'S DONE!!! 

Complete 12 Hrs 40 Mins (give or take a few seconds) :)

I built KDE and ALL of it's dependencies from source. Gentoo rocks!

---

### Post by Tibuda on 2010-02-24
> **dragos240 said:**
> I built KDE and ALL of it's dependencies from source. Gentoo rocks!

[[img]http://imgs.xkcd.com/comics/cautionary.png[/img]]("http://xkcd.com/456")

---

### Post by NoaHall on 2010-02-24
> **dragos240 said:**
> I built KDE and ALL of it's dependencies from source. Gentoo rocks!

The same with everything else I use on Gentoo.

---

### Post by dragos240 on 2010-02-24
> **danielrmt said:**
> [[IMG]http://imgs.xkcd.com/comics/cautionary.png[/IMG]]("http://xkcd.com/456")
It's not THAT hard to compile your kernel!

---

### Post by dragos240 on 2010-02-24
> **NoaHall said:**
> The same with everything else I use on Gentoo.

Well yes, gentoo is indeed a source distro.

---

### Post by madmax.santana on 2010-02-24
> **danielrmt said:**
> [[IMG]http://imgs.xkcd.com/comics/cautionary.png[/IMG]]("http://xkcd.com/456")
Hahahahahahahahahaha!!!

ROFL LMFAO LMFAO LMFAO!!!

God, you got me **danielrmt**!!! ;) Love that =)

---

