---
title: "Firefox 8.0 beta3 building in Launchpad"
date: 2011-10-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-10-18
Firefox 8.0 b3 will soon hit the Precise repos.

See here:
[https://launchpad.net/ubuntu/precise/+source/firefox/8.0~b3+build1-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/firefox/8.0~b3+build1-0ubuntu1)

We already have Thunderbird 8.0 beta 2
[https://launchpad.net/ubuntu/precise/+source/thunderbird/8.0~b2+build1-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/thunderbird/8.0~b2+build1-0ubuntu1)

---

### Post by VinDSL on 2011-10-20
> **Harry33 said:**
> Firefox 8.0 b3 will soon hit the Precise repos.

See here:
[https://launchpad.net/ubuntu/precise/+source/firefox/8.0~b3+build1-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/firefox/8.0~b3+build1-0ubuntu1)

We already have Thunderbird 8.0 beta 2
[https://launchpad.net/ubuntu/precise/+source/thunderbird/8.0~b2+build1-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/thunderbird/8.0~b2+build1-0ubuntu1)
Yep!  Hit the repos...  :)


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-20-oct-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-oct-2011.png")[/INDENT]


Working fine, but...

I had to turn off hardware acceleration in Precise et al. - browsers, Adobe Flash, blah, blah, blah).

Since I did that, UbuPP has been flying like the wind!  ;)

---

### Post by Harry33 on 2011-10-21
> **VinDSL said:**
> 

...

I had to turn off hardware acceleration in Precise et al. - browsers, Adobe Flash, blah, blah, blah).

Since I did that, UbuPP has been flying like the wind!  ;)

Why did you have to do that?

---

### Post by VinDSL on 2011-10-21
> **Harry33 said:**
> Why did you have to do that?
Well, you know how testing goes.  Maybe, I didn't have to do it, but...  :)

I tried numerous browsers, about a year ago.  After several months of "testing" different ones, I settled on three; Opera (now Opera-Next), Chromium, and Firefox (in order of personal preference).

On THIS system (see sig) all three browsers function equally well, doing normal tasks.  The only quantifiable difference is when I'm playing online Flash games on Facebook. Zynga games are particularly brutal on the limited resources in this machine.

Fast forward to Precise...

All of a sudden, I was getting hard locks, when playing online Flash games, on all three browsers.  I was experiencing sluggishness at times, in Oneiric, but OMG!!! I didn't have to hit the power button 10 times an hour (to force a reboot).

I tried all the usual tricks, but nothing seemed to make much of a difference.  Reconfig'ing swappiness helped a bit.  Dittos for turning off hardware acceleration in Adobe Flash.

That's when I discovered the browsers (mentioned above) had started implemented hardware acceleration too.

The latest version of Opera-Next was almost unusable - massive screen blurring when Flash content was present - hard locks.  Turning off the hardware acceleration in Opera-Next did the trick.

Firefox wasn't as bad, but turning off the hardware acceleration worked a treat too.

Chromium has provisions for enabling hardware acceleration, but it wasn't turned on by default, like the others.

Everything worked great but, sadly, two days of updating Precise has made the hard locks return.

Soooo...

Turning off hardware acceleration wasn't an end-all solution - just a temporary crutch.  ;)

I need to run the Flash games again, in a couple of hours.  I'll give GS a test, and see how it does.

If GS doesn't experience any hard locks, I suppose that will help ferret out the rat(s) in Unity...  :D

---

### Post by Harry33 on 2011-10-21
OK, thanks for the info.
Keep us posted.

---

### Post by VinDSL on 2011-10-21
GS had the same problem, so...

I bumped my swappiness to '40' and haven't had a hard lock since.

[fingers crossed]  :)

---

