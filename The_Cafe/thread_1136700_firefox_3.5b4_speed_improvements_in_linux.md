---
title: "firefox 3.5b4 speed improvements in linux"
date: 2009-04-25
forum: The Cafe
---

### Post by xir_ on 2009-04-25
Looks like there is some improvements on their way.

[http://www.tuxradar.com/content/benchmarked-firefox-35-beta-4](http://www.tuxradar.com/content/benchmarked-firefox-35-beta-4)

Does anyone know why it is so slow on Linux?

---

### Post by Namtabmai on 2009-04-25
I believe it's because the stock Windows version is built with profile guided optimization and the Linux one isn't. Well there are several other reasons but this difference would probably account for a large part.

---

### Post by xir_ on 2009-04-25
> **Namtabmai said:**
> I believe it's because the stock Windows version is built with profile guided optimization and the Linux one isn't. Well there are several other reasons but this difference would probably account for a large part.

would compiling from source make much of an improvement?

---

### Post by Namtabmai on 2009-04-25
> **xir_ said:**
> would compiling from source make much of an improvement?

If you enabled PGO then yes.

---

### Post by RottingChrist on 2009-04-25
Better late than never.

---

### Post by xir_ on 2009-04-25
> **Namtabmai said:**
> If you enabled PGO then yes.

cheers for the reply, i think you may have already helped me on a research project i have to do this summer.

---

### Post by Sand &amp; Mercury on 2009-04-25
I've never noticed any difference in speed across either platform.

---

### Post by Giant Speck on 2009-04-25
> **Sand & Mercury said:**
> I've never noticed any difference in speed across either platform.

Same here.

---

### Post by Daisuke_Aramaki on 2009-04-25
firefox has always been fast on my machines, and doesn't take up much memory as well. but i am on a source based distro, Lunar Linux, and i built it from source with profile guided optimization. It just took a while to build, otherwise the end result has been pretty good.

---

### Post by xir_ on 2009-04-25
> **Daisuke_Aramaki said:**
> firefox has always been fast on my machines, and doesn't take up much memory as well. but i am on a source based distro, Lunar Linux, and i built it from source with profile guided optimization. It just took a while to build, otherwise the end result has been pretty good.

did you happen to try high-level optimisations as well?

---

### Post by speedwell68 on 2009-04-25
> **Sand & Mercury said:**
> I've never noticed any difference in speed across either platform.

> **Giant Speck said:**
> Same here.

Me neither. Not that I have really used Windows and FF together much in nearly 3 years.  The speed of it on my current 3 machines is more than fine.

---

### Post by Namtabmai on 2009-04-25
Give Fabien Tassin's PPA a try, it looks like he ( she? ) already has pre-packaged versions of Firefox with PGO enabled

[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

NOTE: I'm not Tassin, nor do I know him, so use at your own risk.

---

### Post by Daisuke_Aramaki on 2009-04-25
> **xir_ said:**
> did you happen to try high-level optimisations as well?

like? it is perfectly optimized for my system.

---

### Post by Giant Speck on 2009-04-25
What exactly is PGO?  Also, has Firefox 3.5b4 been released yet?

---

### Post by Namtabmai on 2009-04-25
Profile guided optimization. Allows a compiler to produce very fast/optimised code by examining the code it produces ( then producing the optimised version ).

---

### Post by Giant Speck on 2009-04-25
> **Namtabmai said:**
> Profile guided optimization. Allows a compiler to produce very fast/optimised code by examining the code it produces ( then producing the optimised version ).

Is it difficult to set up?

---

### Post by Namtabmai on 2009-04-25
> **Giant Speck said:**
> Is it difficult to set up?

You just need to enable it when compiling Firefox, I believe the PPA I posted before contains Firefox packages where it has been built with this already set up. If you want to compile it yourself I believe it's just a matter of passing the right flag to configure when building Firefox.

---

### Post by Daisuke_Aramaki on 2009-04-25
> **Giant Speck said:**
> Is it difficult to set up?

you can probably check out that ppa page that was linked earlier. if you compile from source, it's rather straighforward. Have a look at this.

[https://developer.mozilla.org/En/Building_with_Profile-Guided_Optimization]("https://developer.mozilla.org/En/Building_with_Profile-Guided_Optimization")

you have to pass the option in the configure command

```
./configure --enable-profile-guided-optimization
```

---

### Post by Giant Speck on 2009-04-25
> **Daisuke_Aramaki said:**
> you can probably check out that ppa page that was linked earlier. if you compile from source, it's rather straighforward. Have a look at this.

[https://developer.mozilla.org/En/Building_with_Profile-Guided_Optimization](https://developer.mozilla.org/En/Building_with_Profile-Guided_Optimization)

I try to avoid compiling from source like it's the plague.

---

### Post by collinp on 2009-04-25
I'm using Firefox 3.5b5pre, downloaded from [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/) . Noticeable speed improvement in almost every area. Lets hope it just stays that way.

---

### Post by sports fan Matt on 2009-04-25
I imported the ppa's and the keys...I'll see what happens

---

### Post by adamlau on 2009-04-25
I posted some portable, optimized 3.0.9 PGO builds here: [http://ubuntuforums.org/showthread.php?t=1137488](http://ubuntuforums.org/showthread.php?t=1137488)

---

### Post by xir_ on 2009-04-25
> **Daisuke_Aramaki said:**
> like? it is perfectly optimized for my system.

hmm i was just wondering if you had. i have a big project coming up where i need to compile some fairly substantial code using the intel compiler and was just picking your brain :P

---

### Post by Daisuke_Aramaki on 2009-04-25
> **xir_ said:**
> hmm i was just wondering if you had. i have a big project coming up where i need to compile some fairly substantial code using the intel compiler and was just picking your brain :P

if that is the case you should look at compiling source code in general. for instance, i have custom optimization flags set for my gcc compiler, that is best suited for my machine, so compilation of any program is is well tuned for my computer. in addition, i also build programs, by removing unwanted, unnecessary support, that i know i might never use. this results in programs built precisely for my machine, no more, no less. you will learn a lot if you look up some information on source code compilation and optimization.

---

### Post by xir_ on 2009-04-25
> **Daisuke_Aramaki said:**
> if that is the case you should look at compiling source code in general. for instance, i have custom optimization flags set for my gcc compiler, that is best suited for my machine, so compilation of any program is is well tuned for my computer. in addition, i also build programs, by removing unwanted, unnecessary support, that i know i might never use. this results in programs built precisely for my machine, no more, no less. you will learn a lot if you look up some information on source code compilation and optimization.

i think you may have a very good point.

my brief is to try and compile this FORTRAN quantum chemistry code (as im a theoretical chemist) using the intel compiler, unfortunately this code was designed to compile with the portland compiler.  But i think it will be a fun challenge.

---

