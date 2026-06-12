---
title: "Why is scrolling on Linux so much slower than on Windows?"
date: 2011-03-28
forum: The Cafe
---

### Post by lucazade on 2011-03-28
Like thread title:
Why is scrolling on Linux so much slower than on Windows?

I've found a nice benchmark tool for browsers to test scrolling
[http://home.arcor.de/bazonbloch/scrolltest/whyisscrollingonlinuxslowerthanonwindows.htm](http://home.arcor.de/bazonbloch/scrolltest/whyisscrollingonlinuxslowerthanonwindows.htm)

(click on the side arrows to start bench)

I see chromium is faster than Firefox, compositor like compiz affects a bit speed and Firefox under wine is faster than native one.

what about you?

---

### Post by Sean Moran on 2011-03-28
> **lucazade said:**
> Like thread title:
Why is scrolling on Linux so much slower than on Windows?

I've found a nice benchmark tool for browsers to test scrolling
[http://home.arcor.de/bazonbloch/scrolltest/whyisscrollingonlinuxslowerthanonwindows.htm](http://home.arcor.de/bazonbloch/scrolltest/whyisscrollingonlinuxslowerthanonwindows.htm)

(click on the side arrows to start bench)

I see chromium is faster than Firefox, compositor like compiz affects a bit speed and Firefox under wine is faster than native one.

what about you?
Rather the opposite in my experience.  I usually run SeaMonkey on 9.10, and the lethargy when I have a need to revert to XP or 7 and IE is horrendous.  Win 7 seems to let the mouse run around the desktop in accord with my wrist, but still hasn't improved the scrolling delays when I try to scroll down a page that is still loading up a whole lot of flash-trash.  XP just made it simple and set the mouse cursor on time-delay when it was busy working out what to render next.

Compaq Presario CQ60, 2Gb RAM, Ker wireless mouse with fresh nicads. Runs sweet as pie on Ubuntu 9.10 and SeaMonkey/Firefox scroll when my mouse tells them to scroll, whether mouse-wheel or scroll-bar drag.  Rather exactly the opposite experience at this end.

---

### Post by LowSky on 2011-03-28
scrolling seems fine to me, how fast do you really need it?

if you want it to scroll faster see this
[http://www.pcworld.com/article/163639/change_the_speed_of_mousewheel_scrolling_in_firefox.html](http://www.pcworld.com/article/163639/change_the_speed_of_mousewheel_scrolling_in_firefox.html)

---

### Post by 3Miro on 2011-03-28
1100ms on Chromium and 1200 on Firefox. How fast is it supposed to be? Are you having issues with the graphical driver?

---

### Post by lucazade on 2011-03-28
thanks guys for sharing your experiences and feedbacks! 
What bother me is mainly i can't use firefox on my netbook because scroll lags. 
I tought it was a problem with cairo, xul and smooth font rendering. Unfortunately also firefox4 is so slow for me and i'm sad to see firefox under wine faster. :)

---

### Post by Grenage on 2011-03-28
1097 and 1201 up/down in firefox.

The only time I've ever had a problem was when I lacked decent video drivers.

---

### Post by cchhrriiss121212 on 2011-03-28
Do you have smooth scrolling enabled? Disabling could help. I also find that using page up/down is noticeably smoother and faster compared to manual scrolling.

---

### Post by 3Miro on 2011-03-28
> **lucazade said:**
> thanks guys for sharing your experiences and feedbacks! 
What bother me is mainly i can't use firefox on my netbook because scroll lags. 
I tought it was a problem with cairo, xul and smooth font rendering. Unfortunately also firefox4 is so slow for me and i'm sad to see firefox under wine faster. :)

Your problem is with the video card. You can start researching that and/or open a support request thread with all information about your hardware.

---

### Post by lucazade on 2011-03-28
> **3Miro said:**
> Your problem is with the video card. You can start researching that and/or open a support request thread with all information about your hardware.

I know my graphic drivers are not the state of the art and I believe I can't ask anybody help in this because I'm the person mainting gma500 drivers for ubuntu! :P
(thanks Intel!)

But why chrome is so damn faster than firefox in scrolling?
](*,)

(With a powerful pc and good graphic card the issue is less visible but still present.)

---

### Post by gradinaruvasile on 2011-03-28
Firefox is slow. Firefox 4 is better but still slow compared to Chrome/Chromium/Opera. And this is not only on Linux, even on Windows is visible.

I have seen some reports of Firefox scrolling issues over at the nvnews forums and the nvidia engineers said something about Firefox' habit of supplying large bitmaps to the graphics hardware sometimes. So this scrolling issue is definitely Firefox's fault.

[http://www.nvnews.net/vbulletin/showthread.php?t=153577](http://www.nvnews.net/vbulletin/showthread.php?t=153577)

post #4

I dropped Firefox in favor of Opera (and Chrome sometimes). Both of these start fast and run fast - Firefox' Xul seems to hold it back. Opera and Chrome uses some direct-to-X rendering not needing a Xul-like intermediate layer. Chrome/Chromium is also very good on low memory machines.

I have a feeling that Firefox is beginning to fade...

---

### Post by lucazade on 2011-03-28
> **gradinaruvasile said:**
> Firefox is slow. Firefox 4 is better but still slow compared to Chrome/Chromium/Opera. And this is not only on Linux, even on Windows is visible.

I have seen some reports of Firefox scrolling issues over at the nvnews forums and the nvidia engineers said something about Firefox' habit of supplying large bitmaps to the graphics hardware sometimes. So this scrolling issue is definitely Firefox's fault.

[http://www.nvnews.net/vbulletin/showthread.php?t=153577](http://www.nvnews.net/vbulletin/showthread.php?t=153577)

post #4

I dropped Firefox in favor of Opera (and Chrome sometimes). Both of these start fast and run fast - Firefox' Xul seems to hold it back. Opera and Chrome uses some direct-to-X rendering not needing a Xul-like intermediate layer. Chrome/Chromium is also very good on low memory machines.

I have a feeling that Firefox is beginning to fade...

Good to know,
this is why my gfx card with only 8mb of physical videomem suffers so much.. thanks for pointing this out, really.
I share your feeling about firefox going to fade!

---

### Post by ssam on 2011-03-28
it will mostly depend on how well your graphics card/driver can do 2d acceleration.

---

### Post by lucazade on 2011-03-28
> **ssam said:**
> it will mostly depend on how well your graphics card/driver can do 2d acceleration.

This is for sure, but chrome flies and firefox is slow .. so graphic card and drivers I believe are enough for 2D.
It seems the way firefox is implemented in Linux, like gradinaruvasile pointed.

---

### Post by sdowney717 on 2011-03-28
It scrolls so fast and smooth using firefox 4 on my Nvidia gtx 260 that perhaps it cant even record the results!
Chrome i equally fast and smooth.

---

### Post by Grenage on 2011-03-28
> **sdowney717 said:**
> It scrolls so fast and smooth using firefox 4 on my Nvidia gtx 260 that perhaps it cant even record the results!
Chrome i equally fast and smooth.

I assume you clicked on the big arrows, I missed them at first.

---

### Post by sdowney717 on 2011-03-28
thanks,
it is,

1014 up
1060 down

---

### Post by 3Miro on 2011-03-28
> **3Miro said:**
> 1100ms on Chromium and 1200 on Firefox. How fast is it supposed to be? Are you having issues with the graphical driver?

Funny thing, I got pretty much the same results on my work computer with ATI 4250 integrated card (FOSS driver). I home I am using Nvidia GTX 260 (prop driver).

---

### Post by beew on 2011-03-28
> **gradinaruvasile said:**
> Firefox is slow. Firefox 4 is better but still slow compared to Chrome/Chromium/Opera. And this is not only on Linux, even on Windows is visible.

I have seen some reports of Firefox scrolling issues over at the nvnews forums and the nvidia engineers said something about Firefox' habit of supplying large bitmaps to the graphics hardware sometimes. So this scrolling issue is definitely Firefox's fault.

[http://www.nvnews.net/vbulletin/showthread.php?t=153577](http://www.nvnews.net/vbulletin/showthread.php?t=153577)

post #4

I dropped Firefox in favor of Opera (and Chrome sometimes). Both of these start fast and run fast - Firefox' Xul seems to hold it back. Opera and Chrome uses some direct-to-X rendering not needing a Xul-like intermediate layer. Chrome/Chromium is also very good on low memory machines.

I have a feeling that Firefox is beginning to fade...

I don't see a difference. I am intrigued by people who complain about FF slowness because FF3 is only slightly slower on initial start up and FF4 is kind of the same as Opera.  Are people really in such a rush that they cannot wait for a second? Is this ADD at work?

---

### Post by lucazade on 2011-03-28
> **beew said:**
> I don't see a difference. I am intrigued by people who complain about FF slowness because FF3 is only slightly slower on initial start up and FF4 is kind of the same as Opera.  Are people really in such a rush that they cannot wait for a second? Is this ADD at work?

Initial startup time is not a problem for me, I can wait for it.

The problem is that firefox is not usable on my atom netbook because it needs a powerful gpu and good drivers for 2D rendering. This is imho absurd. We are speaking about scrolling text and images...

Never had this problem also a decade ago with a Voodoo3 gfx card and also with an Amiga System! LOL

---

### Post by TBABill on 2011-03-28
[http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+optimization](http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+optimization)
 
Firefox optimization and I believe there is a portion devoted to speeding up performance of scrolling and page rendering.

---

### Post by NightwishFan on 2011-03-28
System:
```
Debian Wheezy (Testing)
Linux-2.6.38-1-ck1 SMP PREEMPT
Gnome 2.30.2
Firefox (Iceweasel) 3.5.17
```

Hardware:
```
CPU: Intel T4400 2.2ghz (2 cores)
RAM: 3gb DDR2
Graphics: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
```

Epiphany Browser is nearly twice as slow as this Firefox result (2000+ms) when scrolling on my system.

Results:

---

