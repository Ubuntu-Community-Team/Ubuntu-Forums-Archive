---
title: "Handbrake locks up system"
date: 2011-06-13
forum: System76 Support
---

### Post by steigerjb on 2011-06-13
I was trying to convert a video file using handbrake on my new System76 Leopard Extreme but everytime my system freezes/locks up.  I suspect it is locked up because I can't use the mouse and keyboard shortcuts don't work.  I am posting this issue in the System76 section because the same problem occurs on the Windows 7 partition too.  It must not be an Ubuntu issue.  Could it be a computer issue?  My computer should be able to handle it:

3.30ghz Core i7
12gb ram

It worked fine before with my old 1.76ghz 2gb laptop.

---

### Post by JohnAStebbins on 2011-06-14
Encoding video is one of the most stressful things you can ask your computer to do.  It is a good way to expose hardware faults.  A lockup can be caused by a number of things.  Overheating (inadequate cooling), bad memory module, inadequate or bad power supply... the list goes on.  You should do some stress tests with programs like prime95 and memtest86 to see if you can narrow down the fault.

---

### Post by isantop on 2011-06-14
I would definitely try running MemTest86. You can download it from here:

[http://memtest.org](http://memtest.org)

You should download the latest ISO version, 4.20, then burn it to a CD as you would an Ubuntu live CD. That will give us a lot of information to use.

---

### Post by 311005901 on 2011-06-15
You might just have a buggy version of Handbrake. Try adding a different PPA (I use the [snapshot one]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots") with no problems) to see if the new version fixes your issues.

Also, Handbrake can lock up on different conversion settings (or locations e.g. DVD drive / external media) and playing around with them can give you different CPU loads.

---

### Post by steigerjb on 2011-06-15
> **JohnAStebbins said:**
> Encoding video is one of the most stressful things you can ask your computer to do.  It is a good way to expose hardware faults.  A lockup can be caused by a number of things.  Overheating (inadequate cooling), bad memory module, inadequate or bad power supply... the list goes on.  You should do some stress tests with programs like prime95 and memtest86 to see if you can narrow down the fault.

memtest86 said:

> error: too small lower memory (0x99100 > 0x8f000)

---

### Post by steigerjb on 2011-06-15
> **311005901 said:**
> You might just have a buggy version of Handbrake. Try adding a different PPA (I use the [snapshot one]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots") with no problems) to see if the new version fixes your issues.

Also, Handbrake can lock up on different conversion settings (or locations e.g. DVD drive / external media) and playing around with them can give you different CPU loads.

I used that one.

---

### Post by isantop on 2011-06-15
Did you download MemTest or use the one included with Ubuntu. I see that error all the time from the one included in Ubuntu, but the downloaded one usually works okay.

---

### Post by steigerjb on 2011-06-15
> **isantop said:**
> Did you download MemTest or use the one included with Ubuntu. I see that error all the time from the one included in Ubuntu, but the downloaded one usually works okay.

I ran both.  The one from Ubuntu had the error.  The one downloaded finished 1 pass without any errors.  When I have the time, I'll run the downloaded one again it have it go all the way through.  I had work to do earlier so I stopped it during the second pass.  How many passes are there?

---

### Post by steigerjb on 2011-06-15
I did notice that Memtest said I had 1066 MHz ram.  I am supposed to have 1600 MHz.  Was the given the wrong thing? :confused:

---

### Post by isantop on 2011-06-15
I wouldn't trust MemTest to give accurate clock speeds of anything. It may get your processor right, but beyond that, I haven't found it to be particularly reliable on that. You can trust it to detect how much RAM you have, but beyond that, only the test results are super accurate.

---

### Post by steigerjb on 2011-06-19
I ran Memtest for almost 23 hours without errors.  My computer still freezes when trying to use Handbrake.  Like I said before, it freezes using Handbrake in Windows.  I also found out it freezes when trying to render with Camtasia too.

---

### Post by Flyers2391 on 2011-06-20
Is there anything available for the video card that is the equivalent of memtest for RAM?

---

### Post by thomasaaron on 2011-06-20
Have you tried different video conversion software?

---

### Post by steigerjb on 2011-06-28
> **Flyers2391 said:**
> Is there anything available for the video card that is the equivalent of memtest for RAM?

Not that I know of.

---

### Post by steigerjb on 2011-06-28
> **thomasaaron said:**
> Have you tried different video conversion software?

Other programs don't suit my needs.

---

