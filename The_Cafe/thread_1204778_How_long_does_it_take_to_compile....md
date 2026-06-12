---
title: "How long does it take to compile..."
date: 2009-07-05
forum: The Cafe
---

### Post by lovinglinux on 2009-07-05
I'm starting to compile things myself and due to initial the results with Firefox 3.5, I think will be doing this with other applications as well.

Firefox takes 1 hour to compile in my machine and +2:20 (still compiling now) if I enable PGO. So I'm just curious...

How long does it take to compile whatever you compile on your machine?

Please provide the name of the application and the corresponding compiling time. Also include additional information if relevant.

---

### Post by monsterstack on 2009-07-05
I just tried compiling an application so I could answer this thread. mtpaint took two minutes to compile. Neat.

---

### Post by SunnyRabbiera on 2009-07-05
Well there are many factors on how fast the compile is, Processor, memory, kernel, the type of app you are compiling.
I remember compiling the Nimbus theme, took me about a half hour or so...

---

### Post by lovinglinux on 2009-07-05
> **monsterstack said:**
> I just tried compiling an application so I could answer this thread. mtpaint took two minutes to compile. Neat.

:)

Firefox is still compiling here after 2:30. That PGO must worth the trouble :)

---

### Post by .Maleficus. on 2009-07-05
@lovinglinux:  What gcc options are you using?  Are you on 32-bit?  I'm curious about the results you're expecting.

---

### Post by lovinglinux on 2009-07-05
> **.Maleficus. said:**
> @lovinglinux:  What gcc options are you using?  Are you on 32-bit?  I'm curious about the results you're expecting.

Actually, I'm not expecting anything, I'm just curious :) I understand the variables that could affect compiling time and I'm aware my machine will take longer. I have a 32bit P4 3.06Ghz HT Prescott, with 2Gb DDR2 RAM.

Here is my mozconfig file:

```
    . $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O3 -march=prescott -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O3 -march=prescott -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O3 -march=prescott -pipe -fomit-frame-pointer"

ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-optimize 
ac_add_options --enable-profile-guided-optimization
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-xft
ac_add_options --enable-extensions=default
ac_add_options --enable-strip
ac_add_options --enable-install-strip
ac_add_options --enable-pango
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-mochitest
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls
ac_add_options --with-pthreads
```


BTW, Firefox just finished. Let's try it...

---

### Post by PmDematagoda on 2009-07-05
You could decrease the compile time with the -j3 option(considering you have two processors with HT on).

And I have a P4 Prescott at 3.2 Ghz and 1 Gb RAM, the kernel takes about 3 hours to compile, so if you want something big to compile, try that or OpenOffice, I've heard that OOo is pretty big as something to compile.

Speaking of which, I'm trying to get Google Chrome through their SVN server, and it's already reached 1 Gb and still counting.... although most of the stuff seem to be just tests.

---

### Post by SunnyRabbiera on 2009-07-05
I too have a P4, Cedar Mill with hyperthreading.

---

### Post by lovinglinux on 2009-07-05
> **PmDematagoda said:**
> You could decrease the compile time with the -j3 option(considering you have two processors with HT on).


Thanks. I'm not sure where to put it. Is in the flags like below?

```
    export CFLAGS="-O3 **[color=#990000]-j3[/color]** -march=prescott -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O3 **[color=#990000]-j3[/color]** -march=prescott -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O3 **[color=#990000]-j3[/color]** -march=prescott -pipe -fomit-frame-pointer"
```

> **PmDematagoda said:**
> And I have a P4 Prescott at 3.2 Ghz and 1 Gb RAM, the kernel takes about 3 hours to compile, so if you want something big to compile, try that or OpenOffice, I've heard that OOo is pretty big as something to compile.

Aside from personal configurations, does compiling the kernel improves performance considerably, specially using the proper -march option?

> **PmDematagoda said:**
> Speaking of which, I'm trying to get Google Chrome through their SVN server, and it's already reached 1 Gb and still counting.... although most of the stuff seem to be just tests.

I was wondering how fast Chromium would be when optimized. It is already 50% than Firefox 3.5 on my machine :)

---

### Post by gjoellee on 2009-07-05
I have AMD Athelon XP + 300, and I compiled Firefox-PGO between 4-6 hours. (I don't remember to accurate).

---

### Post by lovinglinux on 2009-07-05
> **gjoellee said:**
> I have AMD Athelon XP + 300, and I compiled Firefox-PGO between 4-6 hours. (I don't remember to accurate).

Wow!

---

### Post by RiceMonster on 2009-07-05
My laptop compiles firefox in about 10 minutes (Intel Core2 Duo 1.66 GHZ). My desktop compiles firefox in about 2 minutes or so (AMD Phenom II X4 2.6 GHZ).

Edit: Haven't tried enabling PGO

---

### Post by lovinglinux on 2009-07-05
> **RiceMonster said:**
> My laptop compiles firefox in about 10 minutes (Intel Core2 Duo 1.66 GHZ). My desktop compiles firefox in about 2 minutes or so (AMD Phenom II X4 2.6 GHZ).

Edit: Haven't tried enabling PGO

OMG, that's freaking fast.

---

### Post by PmDematagoda on 2009-07-05
> **lovinglinux said:**
> Thanks. I'm not sure where to put it. Is in the flags like below?

```
    export CFLAGS="-O3 **[color=#990000]-j3[/color]** -march=prescott -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O3 **[color=#990000]-j3[/color]** -march=prescott -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O3 **[color=#990000]-j3[/color]** -march=prescott -pipe -fomit-frame-pointer"
```


Yes, that aught to do the trick. Don't expect a drastic improvement though, HT only acts like there are two processors and doesn't really just create two out of thin air. Also you probably will find it hard to do anything on the PC while it's compiling due to the large system load.

---

### Post by lovinglinux on 2009-07-05
> **PmDematagoda said:**
> Yes, that aught to do the trick. Don't expect a drastic improvement though, HT only acts like there are two processors and doesn't really just create two out of thin air. Also you probably will find it hard to do anything on the PC while it's compiling due to the large system load.

Thanks and yep, HT doesn't make miracles, but it does help to increase my system performance.

---

