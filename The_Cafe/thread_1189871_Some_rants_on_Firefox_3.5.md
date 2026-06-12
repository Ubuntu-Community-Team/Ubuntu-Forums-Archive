---
title: "Some rants on Firefox 3.5"
date: 2009-06-17
forum: The Cafe
---

### Post by froggyswamp on 2009-06-17
Just to check the difference between the latest builds of FF 3.5 on Linux and windows xp I did the following simple JavaScript test (I dual boot XP and Ubuntu):

```

<html>
<script>
var start = new Date();

document.write("Starting...<p/>");
for(var i=0; i<10000000; i++) {
}

var stop = new Date();
document.write("Done. in " + (stop-start) + " milliseconds.");
</script>
</html>

```Check for yourself, my results are:
Ubuntu: 450 milliseconds
Win XP: 20 milliseconds (yes 20 not 200)

I'd like now to listen to the guys who were shouting (especially on slashdot) that starting with 3.5 Mozilla enabled something they call "profiling" for Linux as well, which was the reason why the windows version was faster.. but in fact the gap in 3.5 has become even bigger/worse.
The other tests are not so bad, but the 3.5 versions gap is still much bigger than between the 3.0 versions.
I can't figure out what da heck is going on at Mozilla?
Why do they let the Linux version lag overall 2 to 4 times behind the windows version?

---

### Post by lovinglinux on 2009-06-17
Could you post the results of [Peacemaker](http://service.futuremark.com/peacekeeper/index.action) benchmark for each version?

---

### Post by Tews on 2009-06-17
> **froggyswamp said:**
> Just to check the difference between the latest builds of FF 3.5 on Linux and windows xp I did the following simple JavaScript test (I dual boot XP and Ubuntu):

```

<html>
<script>
var start = new Date();

document.write("Starting...<p/>");
for(var i=0; i<10000000; i++) {
}

var stop = new Date();
document.write("Done. in " + (stop-start) + " milliseconds.");
</script>
</html>

```Check for yourself, my results are:
Ubuntu: 450 milliseconds
Win XP: 20 milliseconds (yes 20 not 200)

I'd like now to listen to the guys who were shouting (especially on slashdot) that starting with 3.5 Mozilla enabled something they call "profiling" for Linux as well, which was the reason why the windows version was faster.. but in fact the gap in 3.5 has become even bigger/worse.
The other tests are not so bad, but the 3.5 versions gap is still much bigger than between the 3.0 versions.
I can't figure out what da heck is going on at Mozilla?
Why do they let the Linux version lag overall 2 to 4 times behind the windows version?

OMG in heaven ... like you can tell the visual difference between 450 millionth of a second and 20 millionth of a second of a second .... Lets keep it real here. ..

---

### Post by BackwardsDown on 2009-06-17
> **Tews said:**
> OMG in heaven ... like you can tell the visual difference between 450 millionth of a second and 20 millionth of a second of a second .... Lets keep it real here. ..

Milisecond != millionth

---

### Post by RiceMonster on 2009-06-17
> **BackwardsDown said:**
> Milisecond != millionth

we're still talking about 0.45 seconds vs 0.02 seconds here. That's still a pretty insignificant difference here.

---

### Post by sim-value on 2009-06-17
Though it somes up in interfaces entirely controlled by JS like Yahoo mail

---

### Post by caravel on 2009-06-17
I've not gone into actually benchmarking it. But I've been running v3.5 beta for a while on my work pc running XP.  It just seems a lot more bloated than v3.x.  I have since taken it off and gone back to 3.x.  On my home PC I'm running Iceweasel (Firefox) 3.x and that's quick but still not as quick as Firefox v3.x running under Win32.  I've read in the past that Firefox was never really designed or optimised for Linux...

---

### Post by BackwardsDown on 2009-06-17
> **RiceMonster said:**
> we're still talking about 0.45 seconds vs 0.02 seconds here. That's still a pretty insignificant difference here.

Up to half a second, I think thats significant.

---

### Post by Tews on 2009-06-17
> **BackwardsDown said:**
> Up to half a second, I think thats significant.

Not significant enough to get twisted over ...

---

### Post by Colonel Kilkenny on 2009-06-17
> **Tews said:**
> Not significant enough to get twisted over ...

That difference was made with just couple lines of JS.
What do you think the difference is when a modern internet site may have thousands of lines just for UI...

The difference is significant and it would be great if Mozilla could offer the same speed in Linux. Although it might have also something to do with Linux in general.

---

### Post by Tews on 2009-06-17
> **Colonel Kilkenny said:**
> That difference was made with just couple lines of JS.
What do you think the difference is when a modern internet site may have thousands of lines just for UI...

The difference is significant and it would be great if Mozilla could offer the same speed in Linux. Although it might have also something to do with Linux in general.

Is it possible that it may be the way that Linux implements JavaScript rather than Firefox?

---

### Post by lovinglinux on 2009-06-17
> **caravel said:**
> I've not gone into actually benchmarking it. But I've been running v3.5 beta for a while on my work pc running XP.  It just seems a lot more bloated than v3.x.  I have since taken it off and gone back to 3.x.  On my home PC I'm running Iceweasel (Firefox) 3.x and that's quick but still not as quick as Firefox v3.x running under Win32.  I've read in the past that Firefox was never really designed or optimised for Linux...

I didn't test it on Windows, but Firefox 3.0.11 without extensions gets 500 points and Firefox 3.5 gets 780 points on my machine.

---

### Post by RiceMonster on 2009-06-17
> **Tews said:**
> Is it possible that it may be the way that Linux implements JavaScript rather than Firefox?

Shouldn't be, as it's the browser's job to handle javascript.

---

### Post by BackwardsDown on 2009-06-17
> document.write("Starting...<p/>");
for(var i=0; i<10000000; i++) {
}

> **Colonel Kilkenny said:**
> That difference was made with just couple lines of JS.
What do you think the difference is when a modern internet site may have thousands of lines just for UI...

looping 10000000-times is an overkill even for a completely ajax based gui

---

### Post by froggyswamp on 2009-06-17
The example with loops is just **an example** where the difference is best seen. When you take into consideration all other cases (not only loops) you'll understand the actual impact when running multiple tabs with modern/heavyweight sites.
Once again, it has nothing to do with Linux, I've particularly tested the same code in Java ( Java is not JavaScript) on XP and Linux, and Linux is a bit faster.

For those saying like "**half a second doesn't matter**" - you just don't get the whole picture.

---

### Post by wersdaluv on 2009-06-17
That's more than 20 times faster. Imagine an older computer that would run it for 5 secs on Ubuntu

---

### Post by geoken on 2009-06-17
> **BackwardsDown said:**
> looping 10000000-times is an overkill even for a completely ajax based gui

No it isn't. The loop has no code in it. It's easily comparable to 100 iterations of a loop that actually does something.

Either way, the point of the example is to show a percentage based difference between the two. You can then take that ratio and apply it to a js heavy site like google docs to see what kind of a difference you would get.

---

### Post by swoll1980 on 2009-06-17
> **Tews said:**
> OMG in heaven ... like you can tell the visual difference between 450 millionth of a second and 20 millionth of a second of a second .... Lets keep it real here. ..

A millisecond is 1/1,000 of a second, not 1/1,000,000

---

### Post by Colonel Kilkenny on 2009-06-17
> **froggyswamp said:**
> 
Once again, it has nothing to do with Linux, I've particularly tested the same code in Java ( Java is not JavaScript) on XP and Linux, and Linux is a bit faster.


Well, the JavaScript and the interpreter itself doesn't have anything to do with Linux as it is indeed the browser which is doing all the work BUT... Opera has the same problems also with Linux builds (perhaps the difference isn't so big but still). E.g. Profile-Guided Optimizations were introduced to Windows builds over a year ago and I'm not actually sure whether they are present in Opera 10 linux build which was released yesterday.

I'm no expert when it comes to compilers and optimizations but the information I have received is pretty much saying that Visual Studio compiler (and I guess Intel compilers as well?) is/are atm. running circles around gcc.

---

### Post by swoll1980 on 2009-06-17
> **lovinglinux said:**
> Could you post the results of [Peacemaker](http://service.futuremark.com/peacekeeper/index.action) benchmark for each version?

I did the peace maker for both about a month ago. I don't have the results, but the win version scored around 350, while the Linux version scored around 275. Google chrome scored around 450.

---

### Post by lovinglinux on 2009-06-17
> **swoll1980 said:**
> I did the peace maker for both about a month ago. I don't have the results, but the win version scored around 350, while the Linux version scored around 275. Google chrome scored around 450.

Would you mind telling your computer specs? I'm asking this because I think your results are a little bit odd. For instance, Chrome or Chromium should have higher results. I had similar results for Firefox when I first installed Jaunty, but improved a lot with some tweaks and updates.

My benchmarks when first installed Jaunty:

Opera 9 - 285 points
Firefox 3 - 330 points / with extensions - 220 points
Firefox 3.5 - 450 points
Chromium - 800 points

My current benchmarks:

Firefox 3 - 507 points / with extensions - 410 points
Firefox 3.5 - 780 points
Opera 10 - 830 points
Chromium - 1530 points

My system specs:

P4 3.06 Ghz HT
2GB DDR2 RAM
nVidia 7300 GT with 180 driver
ext4 SATA HDD  (root and home)
ext4 IDE HDD (backup and storage)

---

### Post by swoll1980 on 2009-06-17
> **lovinglinux said:**
> Would you mind telling your computer specs? I'm asking this because I think your results are a little bit odd. For instance, Chrome or Chromium should have higher results. I had similar results for Firefox when I first installed Jaunty, but improved a lot with some tweaks and updates.

My benchmarks when first installed Jaunty:

Opera 9 - 285 points
Firefox 3 - 330 points / with extensions - 220 points
Firefox 3.5 - 450 points
Chromium - 800 points

My current benchmarks:

Firefox 3 - 507 points / with extensions - 410 points
Firefox 3.5 - 780 points
Opera 10 - 830 points
Chromium - 1530 points

My system specs:

P4 3.06 Ghz HT
2GB DDR2 RAM
nVidia 7300 GT with 180 driver
ext4 SATA HDD  (root and home)
ext4 IDE HDD (backup and storage)

I have a p4 2.66 GHz 1 GB RAM, a Nvidia 6200 128 b 256 MB RAM, and an
old 40 GB IDE hard disk

---

### Post by lovinglinux on 2009-06-17
> **swoll1980 said:**
> I have a p4 2.66 GHz 1 GB RAM, a Nvidia 6200 128 b 256 MB RAM, and an
old 40 GB IDE hard disk

It is not that different from my system. Try some of my tips [from here](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1152095). They might help you increase performance and the benchmarks.

I know you are not asking for help and didn't complained about the performance of your machine, but I just wanted to let you know about my results and what I did to get improvements.

---

### Post by swoll1980 on 2009-06-17
> **lovinglinux said:**
> It is not that different from my system. Try some of my tips [from here](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1152095). They might help you increase performance and the benchmarks.

I know you are not asking for help and didn't complained about the performance of your machine, but I just wanted to let you know about my results and what I did to get improvements.

Thanks for the tips. I will try them out.

---

### Post by Daisuke_Aramaki on 2009-06-17
thanks for the peacemaker link. my firefox 3.0.11 got 782. it was compiled from source with pgo enabled of course.

1.86GHz, 1GB RAM, DualCore E6300. Graphic card is onboard, so I use vesa. And the filesystem is ext3.

/edit

i did the same on my laptop, intel dual t2410, 2 GHz, 2gig ram, and powered by Lunar Linux. Firefox 3.0.11 got 932

---

### Post by Dimitriid on 2009-06-17
> **froggyswamp said:**
> Just to check the difference between the latest builds of FF 3.5 on Linux and windows xp I did the following simple JavaScript test (I dual boot XP and Ubuntu):

```

<html>
<script>
var start = new Date();

document.write("Starting...<p/>");
for(var i=0; i<10000000; i++) {
}

var stop = new Date();
document.write("Done. in " + (stop-start) + " milliseconds.");
</script>
</html>

```Check for yourself, my results are:
Ubuntu: 450 milliseconds
Win XP: 20 milliseconds (yes 20 not 200)

I'd like now to listen to the guys who were shouting (especially on slashdot) that starting with 3.5 Mozilla enabled something they call "profiling" for Linux as well, which was the reason why the windows version was faster.. but in fact the gap in 3.5 has become even bigger/worse.
The other tests are not so bad, but the 3.5 versions gap is still much bigger than between the 3.0 versions.
I can't figure out what da heck is going on at Mozilla?
Why do they let the Linux version lag overall 2 to 4 times behind the windows version?

Out of curiosity can you run that through epiphahy and konqueror?

---

### Post by lovinglinux on 2009-06-17
> **Daisuke_Aramaki said:**
> thanks for the peacemaker link. my firefox 3.0.11 got 782. it was compiled from source with pgo enabled of course.

1.86GHz, 1GB RAM, DualCore E6300. Graphic card is onboard, so I use vesa. And the filesystem is ext3.

/edit

i did the same on my laptop, intel dual t2410, 2 GHz, 2gig ram, and powered by Lunar Linux. Firefox 3.0.11 got 932

I guess the dual core makes a huge difference.

---

### Post by FuturePilot on 2009-06-17
> **lovinglinux said:**
> I guess the dual core makes a huge difference.

I don't think it has anything to do with a dual core processor

> it was compiled from source **with pgo enabled** of course.

PGO, that's why.

---

### Post by CJ Master on 2009-06-17
What's PGO?

---

### Post by FuturePilot on 2009-06-17
> **CJ Master said:**
> What's PGO?

[Profile-Guided Optimization]("http://en.wikipedia.org/wiki/Profile-guided_optimization")

The Windows builds of Firefox have it enabled. The Linux version doesn't.

---

### Post by swoll1980 on 2009-06-17
> **FuturePilot said:**
> I don't think it has anything to do with a dual core processor



PGO, that's why.

The Windows version has PGO by default, if I'm not mistaken, and it only scored a 350 on my machine which has a much faster clock speed. The dual core must be the deciding factor.

---

### Post by lovinglinux on 2009-06-17
> **FuturePilot said:**
> I don't think it has anything to do with a dual core processor

PGO, that's why.

Do you know a tutorial that explains how to do it?

> **CJ Master said:**
> What's PGO?

I guess it is [Profile-guided optimization](http://en.wikipedia.org/wiki/Profile-guided optimization) [wikipedia.org]

---

### Post by FuturePilot on 2009-06-17
> **lovinglinux said:**
> Do you know a tutorial that explains how to do it?



I guess it is [Profile-guided optimization](http://en.wikipedia.org/wiki/Profile-guided optimization) [wikipedia.org]

[https://developer.mozilla.org/en/Building_with_Profile-Guided_Optimization]("https://developer.mozilla.org/en/Building_with_Profile-Guided_Optimization")

---

### Post by CJ Master on 2009-06-17
Why doesn't the Linux version come with it by default?

---

### Post by lovinglinux on 2009-06-17
> **FuturePilot said:**
> [https://developer.mozilla.org/en/Building_with_Profile-Guided_Optimization]("https://developer.mozilla.org/en/Building_with_Profile-Guided_Optimization")

Thanks. I will look into it. This might sound stupid, but how do you update it? Do you need to compile each new version? Do you need to uninstall Firefox before updating with a new build?

---

### Post by FuturePilot on 2009-06-17
> **lovinglinux said:**
> Thanks. I will look into it. This might sound stupid, but how do you update it? Do you need to compile each new version? Do you need to uninstall Firefox before updating with a new build?

You would have to compile each new version. I'm not sure if you need to uninstall the old one.

---

### Post by lovinglinux on 2009-06-17
> **FuturePilot said:**
> You would have to compile each new version. I'm not sure if you need to uninstall the old one.

Thanks. How does flash behaves?

---

