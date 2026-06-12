---
title: "PanP5 suspend/hibernate CPU bug"
date: 2012-01-23
forum: System76 Support
---

### Post by PGScooter on 2012-01-23
Hi,

I'm wondering if System 76 has made any progress in getting this bug fixed. A few of us users have tried, see the page here: 

[http://ubuntuforums.org/showthread.php?t=1458647&page=3](http://ubuntuforums.org/showthread.php?t=1458647&page=3)

and here for the bug report:
[https://bugs.launchpad.net/ubuntu/+source/cpufrequtils/+bug/364514](https://bugs.launchpad.net/ubuntu/+source/cpufrequtils/+bug/364514)

The bug seems specific to System 76 hardware, so I don't expect much from Ubuntu developers.

Any progress or new ideas? Thanks

---

### Post by isantop on 2012-01-24
Do you still have the bug in 11.10? We typically focus more of our development effort to the latest release, so if it's something that only affects 10.04, we're not likely to put a lot of effort into it, particularly with 12.04 so close to release.

---

### Post by PGScooter on 2012-01-24
> **isantop said:**
> Do you still have the bug in 11.10? We typically focus more of our development effort to the latest release, so if it's something that only affects 10.04, we're not likely to put a lot of effort into it, particularly with 12.04 so close to release.

that sounds like a very reasonable policy. I have the bug in 11.04. The last post on the bug report I linked to says that there is still a bug in 11.10. I would assume that it is also in 12.04, but I will wait until the final release of 12.04 to install it. However, if it would help you a lot and you would put some time into it, then I would be willing to test with earlier versions of 12.04.

---

### Post by isantop on 2012-01-25
Does the workaround in that post work for you to get every back to normal? Also, where are you checking the CPU frequency?

I wouldn't recommend running 12.04 until it's released. I'll see if we have a PanP5 in the shop here and do some testing.

---

### Post by PGScooter on 2012-01-25
Great! Thanks a lot for looking into it. I have 11.04 (the user in the last post has 11.10). There is no cpufreq-set command in 11.04.

---

### Post by PGScooter on 2012-01-25
I don't know about others, but I am only interested in 12.04. I'm not interested in trying to get rid of the bug in 11.04. So maybe it would be better if I bugged you when 12.04 is released?

Thanks again for your help.

---

### Post by marshmallow1304 on 2012-01-26
This bug is still present on my PanP5 running Gentoo with linux-3.2.1.  It affects the ondemand cpu governor when resuming from suspend.  It does not seem to affect any other governors or hibernation.

Here's how to reproduce:
1) set cpu governor to ondemand
2) start multiple instances of glxgears or similar
  - ondemand governor properly adjusts cpu frequency to handle load
3) suspend
4) resume
5) start multiple instances of glxgears or similar
  - ondemand governor is stuck at the lowest frequency (800 MHz on my machine)

If I set the frequency manually, it changes.  Then if I go back to the ondemand governor, frequency will stay at higher levels as needed.  However, once the frequency drops, it will never increase to a higher level.  A reboot fixes things.

---

### Post by isantop on 2012-01-27
That's actually excellent information. I'll try and pull out a PanP5 and replicate this bug, then get it filed. It's good to know it's a kernel bug, too. Knowing the source of a problem is sometimes half of getting it fixed.

---

### Post by PGScooter on 2012-02-21
Hey Ian, have you had a chance to look at this?

---

### Post by HotShotDJ on 2012-02-23
This is still going on in Ubuntu?  What I can tell you is that it was fixed in OpenSUSE since at least version 11.4 -- my PanP5 happily suspends/resumes without "locking" the CPU with OpenSUSE 12.1.

If the bug is upstream -- that is, with the Kernel -- then perhaps trying a newer kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) might help.  IIRC, I noticed that the bug had been fixed for me in OpenSUSE starting with the 3.0 kernel... but I might be wrong on that, but it was certainly fixed by 3.1.

Given that Marshmallow is reporting the problem with Gentoo + Kernel 3.2, I suspect that the problem might be with the way that Ubuntu kernel maintainers are compiling the kernel rather than with the kernel itself. But I haven't been tracking Ubuntu development and I don't have a machine to test this hypothesis.

I hope this info helps you track down the problem.

---

### Post by isantop on 2012-02-23
If the bug was fixed in 3.1, then it will be fixed in Ubuntu for 12.04.

In my testing, I was able to confirm this. It's looking like this is the kernel bug. I haven't done testing with Precise yet, though I suspect this will see the problem solved.

---

### Post by PGScooter on 2012-02-23
Great! I am very happy to hear this. Thanks for looking into it.

---

### Post by samalex on 2012-03-05
My PanP5 is still having this problem as well, but I'm still on 10.04 LTS too.  I'll probably move to 12.04 LTS when it's released, but for now [my work around]("http://ubuntuforums.org/showpost.php?p=9426457&postcount=26") noted in the thread PGScooter mentioned from 2010 is still what I have to do after each reboot or wake-up.

I figured this was just one of those quirks since it occurred with 9.04 then with 10.04, but good to see it may be fixed in 12.04.

Sam

---

