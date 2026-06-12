---
title: "How unstable is Debian Sid?"
date: 2009-04-30
forum: The Cafe
---

### Post by Pogeymanz on 2009-04-30
I want to slap Linux on a laptop that I will be using for the summer.
Long story short- I need something quicker to install than Arch, so I thought about Ubuntu of course. But I'm afraid Ubuntu might be a little too bloaty for this laptop. I've had very good experience putting Debian on old hardware, but I always used the stable/testing branches.

Will I be able to get work done with Debian Sid? Or should I just install Testing and manually install any newer packages I want (xfce4.6, mostly).

---

### Post by garythegoth on 2009-04-30
> **Pogeymanz said:**
> I want to slap Linux on a laptop that I will be using for the summer.
Long story short- I need something quicker to install than Arch, so I thought about Ubuntu of course. But I'm afraid Ubuntu might be a little too bloaty for this laptop. I've had very good experience putting Debian on old hardware, but I always used the stable/testing branches.

Will I be able to get work done with Debian Sid? Or should I just install Testing and manually install any newer packages I want (xfce4.6, mostly).

Haha, I really wouldnt. Sid has a very nasty habiting of breaking with the weirdest things. Arch is a much, much better choice.

---

### Post by gymophett on 2009-04-30
> **Pogeymanz said:**
> I want to slap Linux on a laptop that I will be using for the summer.
Long story short- I need something quicker to install than Arch, so I thought about Ubuntu of course. But I'm afraid Ubuntu might be a little too bloaty for this laptop. I've had very good experience putting Debian on old hardware, but I always used the stable/testing branches.

Will I be able to get work done with Debian Sid? Or should I just install Testing and manually install any newer packages I want (xfce4.6, mostly).

If you really are on an old laptop. Arch will be _well_ worth your time.

---

### Post by garythegoth on 2009-04-30
> **gymophett said:**
> If you really are on an old laptop. Arch will be <u>well</u> worth your time.

Replace <> with [] for these forums for **whatever** reason.

---

### Post by gymophett on 2009-04-30
What are the laptops specs?

---

### Post by kerry_s on 2009-04-30
i'd say go with debian testing xfce4.
net installer:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

for xfce4 select advanced options the select desktop, something like that.
there will be kde, xfce4 and lxde.

current version in testing is xfce4 4.4.2.1 which offer the same things as 4.6.

---

### Post by garythegoth on 2009-04-30
Why would anyone want to install an unstable O/S if they want to use if it generally?

---

### Post by supersonicdarky on 2009-04-30
Get sidux. The slogan is "debian unstable made stable". It's basically sid, but with some overriding fix repos (among other small scripts and fixes). Installed in under 4 min on my desktop. Have been running it since september - no problems. Also since it's sid, its rolling release. No whole system upgrades.

[http://sidux.com/](http://sidux.com/)

---

### Post by sertse on 2009-05-01
+1 sidux. Sidux is Debian Sid + Own repos (quick fixes for core components until the fixes are accept in upstream - including (but not just) the "sidux" kernel; sidux devs are active contributer to kernel dev) + community specialising in sid's nuances.

If you read the manual, news on the site and the forums you shouldn't have issues - the instability is somewhat overstated. 
In the same way people assert "Arch is hard" :P, when it really isn't. Like it, the secret is being a user who reads. :)

The main advantage is that it's still debian, you're already familiar with alot of the basics, so slightly easier to get going.

Btw: Xfce 4.6 will in testing in the next couple of day / weeks (some parts made it already)

---

### Post by samjh on 2009-05-01
Sid = very unstable.  I've found it unusable if you want your computer for productive purposes.

+1 to Sidux.

---

### Post by sgosnell on 2009-05-01
With Debian, stable/unstable has nothing to do with whether it will crash.  Stable means it's finished, and there will never be any more changes or fixes.  Unstable means development is still being done.

---

### Post by walkerk on 2009-05-01
+1 for sidux. I run sidux on my HP laptop without issues. Great distro

---

### Post by snowpine on 2009-05-01
> **sgosnell said:**
> With Debian, stable/unstable has nothing to do with whether it will crash.  Stable means it's finished, and there will never be any more changes or fixes.  Unstable means development is still being done.

A *HUGE* +1 to this. In Debian talk, stable/unstable has nothing to do with whether or not your system will crash. Debian "unstable" is less buggy than many other distros. I think sidux Xfce would be perfect for the OP. It is faster and more reliable than Xubuntu in my experience. The difference between sidux and Ubuntu (as I understand it) is as follows: Ubuntu takes a snapshot of Debian Sid every six months, then fixes bugs and adds new features to create a "stable" release twice a year. Sidux, on the other hand, adds a "stabilizing layer" on top of Debian Sid, but is constantly changing and evolving, so that upgrades are available when they're ready, not in six months.

I use both Ubuntu and sidux, so I'm not saying one is better than the other, just trying to explain the difference as I see it.

---

### Post by Pogeymanz on 2009-05-01
Wow it sounds like Sidux is exactly what I'm looking for. Arch will always be my main squeeze, but I just want this laptop up and running without much effort and time.

I'm downloading Sidux-XFCE as I type. Thanks a bunch.

---

