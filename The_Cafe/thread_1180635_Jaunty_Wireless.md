---
title: "Jaunty Wireless"
date: 2009-06-07
forum: The Cafe
---

### Post by Gias Kay on 2009-06-07
Hi,

This is not meant to be a serious discussion, so I am posting it here.

I heard from my friend that Jaunty has a lot of wireless problems so am kinda hesitate about going from Intrepid to Jaunty. Is it true?

---

### Post by pwnst*r on 2009-06-07
i use jaunty on a 3 month old HP HDX 16T and it's been working great.

---

### Post by BslBryan on 2009-06-07
While I run 8.04, the 9.04 LiveCD is what I usually run if I need to boot into a Live environment.  My wireless chipset is never recognized, but I run two simple commands in the terminal:
```
sudo rmmod ssb
sudo modprobe wl
```

And then my wireless light comes on.  5 minutes later at the most, and I'm on the internet.  I suppose you can set those commands to run at startup if you're in the same boat I am, or use that wireless to figure out a better solution.

---

### Post by itsStephen on 2009-06-07
Wireless works fine in Jaunty for me! It's also so much quicker to connect than the previous releases.

---

### Post by perce on 2009-06-07
If Jaunty has wireless problems, they are with some chipset, not with all of them. You should try to understand which chipsets give problems (by searching the forum for Jaunty wireless for example) and see if yours is one of them. 

Usually every piece of hardware is a different story, so statements of the type X has problems with Y don't usually make much sense if you don't specify which model is Y.

As far as I can tell you, I have an Intel wireless Pro 3945 abg and it works very well. On the other hand Network Manager is still kind of buggy in my opinion, but not more than it was in Intrepid.

---

### Post by 3rdalbum on 2009-06-07
Jaunty did improve the speed and reliability of my RTL8187 wireless, so I don't think there's anything to what your friend was saying. Maybe one or two isolated chipsets have regressions under Jaunty, but then Intrepid's RTL8187 driver was almost useless compared to Hardy's.

---

### Post by ghindo on 2009-06-07
> **Gias Kay said:**
> Hi,

This is not meant to be a serious discussion, so I am posting it here.

I heard from my friend that Jaunty has a lot of wireless problems so am kinda hesitate about going from Intrepid to Jaunty. Is it true?Nope.

---

