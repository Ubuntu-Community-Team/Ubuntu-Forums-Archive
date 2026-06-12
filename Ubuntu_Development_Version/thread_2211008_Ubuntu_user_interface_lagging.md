---
title: "Ubuntu user interface lagging"
date: 2014-03-13
forum: Ubuntu Development Version
---

### Post by startas on 2014-03-13
So, the biggest ubuntu problem right now is very laggy dash - appear/disappear animations lags, when searching, it takes quite a few seconds for icons to appear, even if result is 1 or 5 items. removing blur improves situation, but only by a bit. The lag also makes hard to pin programs to launcher, as you have to do it very slowly for it to work. And it is the biggest ubuntu problem, because the whole ubuntu unity thing is 99% about its dash, so its like 99% of ubuntu is stuck in 1960's. Not so good, heh.

---

### Post by andrew.46 on 2014-03-13
I have to say that I have no such problem here on a fresh installation of Trusty. Perhaps disable the online search?

---

### Post by blitzd on 2014-03-13
I found the auto-hide on the dash to be pretty broken too, as in it never unhides for me. Could be because I'm running it within a VM though. I tried modifying the settings, but it doesn't seem to even read them.

---

### Post by andrew.46 on 2014-03-13
> **blitzd said:**
> I found the auto-hide on the dash to be pretty broken too, as in it never unhides for me. Could be because I'm running it within a VM though. I tried modifying the settings, but it doesn't seem to even read them.

Same problem here, also running through VM....

---

### Post by craig10x on 2014-03-13
Vm can be troublesome...a hard install would be like the difference between day and night...you wouldn't likely have those kind of problems...unity is very smooth, fast, and snappy...

---

### Post by blitzd on 2014-03-13
It's quite smooth and snappy on my VM as well, and I'd be using it in 14.04 if I could move the min/max/close buttons... 

It only seems to be the edge detection that doesn't work well - even with workspace/show-desktop/etc on the corners they sometimes work, sometimes don't.

---

### Post by startas on 2014-03-14
Online search is disabled, it doesnt make any difference, and btw, dash lags not only in 14.04 but in all ubuntu versions with unity.

---

### Post by gifford on 2014-03-14
I am also experiencing the lag. Overall, 14.04 seems much slower than 12.04.  I am using amd64 version on two machines and both are affected.

---

### Post by Rustan on 2014-03-14
in KDE I also have lag, I suspect a problem in the new version of the Mesa ...

---

### Post by ventrical on 2014-03-14
> **gifford said:**
> I am also experiencing the lag. Overall, 14.04 seems much slower than 12.04.  I am using amd64 version on two machines and both are affected.


All my trusty installs are working super fast!! The only ones I had problems with were ones that retrofitted to llvmpipe. Check <about this computer   ...   and see what the video (driver) settings are.

---

### Post by andrew.46 on 2014-03-14
> **ventrical said:**
> All my trusty installs are working super fast!! 

Indeed, I see no lag whatsoever.

---

### Post by ventrical on 2014-03-14
> **andrew.46 said:**
> Indeed, I see no lag whatsoever.


:)


```

ventrical@ventrical-P5QL-PRO:~$ uname -a
Linux ventrical-P5QL-PRO 3.13.0-17-generic #37-Ubuntu SMP Mon Mar 10 21:44:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-P5QL-PRO:~$ 

```

---

### Post by blitzd on 2014-03-28
I can confirm that the edge detection I mentioned earlier is working better without using a VM, but it's still flaky - sometimes it stops working altogether.

---

### Post by x-shaney-x on 2014-03-28
I don't see any lag in general, almost everything seems really snappy these days, the one notable exception being the dash.
That does lag horribly for me and often takes several seconds for it to do anything after opening or searching.  All online results are turned off.

---

### Post by forcecore on 2014-03-29
Those with lag can kernel 3.14 give better performance?

---

### Post by ventrical on 2014-03-29
I'll say again, the only time I experience 'lag' is when I have an offset Radeon or nVidia graphics card and the driver doesn't load right or llvmpipe is incorpotated.

At this stage we don't even know what the OPs hardware config is.... so if he has an older system it may be llvmpipe or other.

---

### Post by forcecore on 2014-03-29
If it is llvmpipe then sad thing that lag is inevitable, for example i had to set Ubuntu to someone's desktop and he must use llvmpipe because GPU(8600m) is faulty but with llvmpipe it works in usable level for internet browsing and news reading and file managment.

---

### Post by ventrical on 2014-03-29
> **forcecore said:**
> If it is llvmpipe then sad thing that lag is inevitable, for example i had to set Ubuntu to someone's desktop and he must use llvmpipe because GPU(8600m) is faulty but with llvmpipe it works in usable level for internet browsing and news reading and file managment.


That is why there are other flavours, to deal with more recent-legacy machines. Ubuntu (Unity) takes up a lot of video graphics resource. There are several other DE's that will work great with the trusty kernels on older machines -- just not Ubuntu Unity.

---

### Post by x-shaney-x on 2014-03-31
Well in my case I have a Core i5 with Intel graphics so I don't think llvmpipe is involved.
And as said, the lag only involves Dash.  Is there anything that can be done to make Dash run better since I don't think it is going to improved for me by release?

---

### Post by mc4man on 2014-03-31
While I probably don't need to as a matter of course set the Dash blur  to "No Blur"  which is known to help performance. 
Generally speaking No blur isn't suitable unless one also sets a decent amount of opacity to the Dash thru the "Background color" setting

That works ok here as I use #000000 as the background color so with a fairly stiff opacity get a Dash similar to what unity-2d used to provide
(why anyone would want to see thru the Dash is beyond me anyway...

---

