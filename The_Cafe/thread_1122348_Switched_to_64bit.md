---
title: "Switched to 64bit"
date: 2009-04-11
forum: The Cafe
---

### Post by FuturePilot on 2009-04-11
Yep, add another one to the 64bit crowd :D
I finally bit the bullet and made the switch on my laptop. I wiped my 32bit Jaunty install and put on 64bit Jaunty and I'm really loving it. I do notice a speed improvement over 32bit. Maybe a placebo effect? Nah it really does feel snappier. :guitar:

It's come a long way now that there are native 64bit Flash and Java plugins and it will only continue to get better as 64bit becomes standard.

---

### Post by FuturePilot on 2009-04-12
No one has any thoughts on 64bit Ubuntu or 64bit in general? :(

---

### Post by swoll1980 on 2009-04-12
I need to get a 64bit computer first. :p

---

### Post by chris200x9 on 2009-04-12
welcome to the dark side :mad:

---

### Post by Sealbhach on 2009-04-12
It's a bit annoying when you can't get some apps for 64bit - like Boxee. I sometime dpkg --force install stuff but it didn't work with Boxee.


.

---

### Post by kevin11951 on 2009-04-12
i would like to somehow benchmark the difference between 32 and 64bit general speed, how?

---

### Post by SKLP on 2009-04-12
Sadly, 64-bit native flash does not work as good as 32-bit flash in nspluginwrapper.
This is due to the fact that the native plugin has no support for accelerated full-screen.
Other than flash, 64-bit works great in my experience.

---

### Post by mips on 2009-04-12
> **FuturePilot said:**
> No one has any thoughts on 64bit Ubuntu or 64bit in general? :(

No, it works so why comment. Been using it for years.

---

### Post by kevin11951 on 2009-04-12
> **Sealbhach said:**
> It's a bit annoying when you can't get some apps for 64bit - like Boxee. I sometime dpkg --force install stuff but it didn't work with Boxee.


.

did you make sure you had the dependencies installed?

---

### Post by 4th guy on 2009-04-12
> **FuturePilot said:**
> No one has any thoughts on 64bit Ubuntu or 64bit in general? :(
Some patches take a long time to go upstream from 32bit.

For example 8.04 32bit can detect onboard ethernet port, while 8.04 64bit would not without installing the kernel deb from 8.10

---

### Post by FuturePilot on 2009-04-12
> **chris200x9 said:**
> welcome to the dark side :mad:

lol :)

---

### Post by MellonCollie on 2009-04-12
> **kevin11951 said:**
> i would like to somehow benchmark the difference between 32 and 64bit general speed, how?

I don't know about benchmarks, but, for what it's worth, I didn't notice any speed difference in general usage when I moved to 64-bit.

---

### Post by Paqman on 2009-04-12
> **kevin11951 said:**
> i would like to somehow benchmark the difference between 32 and 64bit general speed, how?

You'll have to install both separately. To make it a fair benchmark both systems would have to be identical. So the easiest would be to use a two fresh installs.

The thing is, performance will really depend on what benchmark you choose. 64-bit won't show any performance improvement at all if you choose a task that's mainly governed by disk I/O (for example), but it should slaughter 32-bit on CPU-intensive tasks like re-encoding media.

If you're expecting a big speed boost, you'll probably be disappointed. Personally I use 64-bit because I figure that if you've got a 64-bit chip, why throttle it down, even by 5%? 32-bit is old hat, not even Windows is stuck in 32-bit land any more.

---

### Post by Sealbhach on 2009-04-12
> **kevin11951 said:**
> did you make sure you had the dependencies installed?

Yes, I did all that - I followed a guide. But when I tried t run Boxee it said that there was some .so file missing (even though locate found it).

Probably I just needed to -s link it to somewhere else but I couldn't be bothered to find out.

---

### Post by FuturePilot on 2009-04-12
> **Paqman said:**
> 
If you're expecting a big speed boost, you'll probably be disappointed. Personally I use 64-bit because I figure that if you've got a 64-bit chip, why throttle it down, even by 5%? 32-bit is old hat, not even Windows is stuck in 32-bit land any more.

Exactly. 32bit is going to be obsolete in a few years. Just about any computer being sold today is 64bit capable, yet it usually has a 32bit OS stuck on it. If you have a 64bit computer might as well take advantage of it.

---

### Post by steeleyuk on 2009-04-12
> Sadly, 64-bit native flash does not work as good as 32-bit flash in nspluginwrapper.

If you mean it doesn't crash as good as nspluginwrapper... in my experience, the 64-bit Flash has been pretty much rock-solid.

64-bit for me has been excellent, I installed Handbrake on it and got an immediate speed boost over the 32-bit version.

---

### Post by hyperdude111 on 2009-04-12
I have never needed it but you can try ia32 libs so all 32bit apps install with dpkg --force

---

### Post by SKLP on 2009-04-12
> **steeleyuk said:**
> If you mean it doesn't crash as good as nspluginwrapper... in my experience, the 64-bit Flash has been pretty much rock-solid.

64-bit for me has been excellent, I installed Handbrake on it and got an immediate speed boost over the 32-bit version.

In my experience, both 32-bit flash in nspluginwrapper and  64-bit native flash crash quite a bit :(
In the native player though, accelerated full screen does not appear to be available at all (which is why I'm using nspluginwrapper atm)

---

### Post by FuturePilot on 2009-04-12
> **steeleyuk said:**
> If you mean it doesn't crash as good as nspluginwrapper... in my experience, the 64-bit Flash has been pretty much rock-solid.

64-bit for me has been excellent, I installed Handbrake on it and got an immediate speed boost over the 32-bit version.

I've been using the 64bit Flash Beta and it's been working great. Haven't had any problems with it so far.

---

### Post by Sealbhach on 2009-04-12
> **FuturePilot said:**
> I've been using the 64bit Flash Beta and it's been working great. Haven't had any problems with it so far.

How do you get that? is it in the Jaunty beta?


.

---

### Post by stmiller on 2009-04-12
> **SKLP said:**
> Sadly, 64-bit native flash does not work as good as 32-bit flash in nspluginwrapper.
This is due to the fact that the native plugin has no support for accelerated full-screen.
Other than flash, 64-bit works great in my experience.

Sadly?

Native 64bit flash is rock solid and has WAY better cpu performance than any wrapper and 32bit version I have found.

---

### Post by SKLP on 2009-04-12
> **stmiller said:**
> Sadly?

Native 64bit flash is rock solid and has WAY better cpu performance than any wrapper and 32bit version I have found.
If you don't care about accelerated full-screen, then sure it might be a bit lower on the cpu usage

---

### Post by toupeiro on 2009-04-12
I used to suggest to new linux users that they start with 32-bit, as it is truly the mature architecture which software is developed for.  However, 64-bit has come such a long way that I am less and less often making this recommendation.

---

### Post by blastus on 2009-04-12
Windows Media Audio v3 doesn't work on 64bit Linux at this time.

---

### Post by gn2 on 2009-04-12
> **Sealbhach said:**
> How do you get that?

64-bit Flash at the bottom of the page [here]("http://labs.adobe.com/downloads/flashplayer10.html") and installation instructions [here]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml").

---

### Post by Sealbhach on 2009-04-12
> **gn2 said:**
> 64-bit Flash at the bottom of the page [here]("http://labs.adobe.com/downloads/flashplayer10.html") and installation instructions [here]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml").

Cool, using it now. Thanks!

.

---

