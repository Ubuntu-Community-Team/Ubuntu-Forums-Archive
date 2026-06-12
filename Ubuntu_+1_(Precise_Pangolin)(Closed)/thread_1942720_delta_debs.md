---
title: "delta debs"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ikt on 2012-03-18
While I sit here waiting for over an hour while this natty box updates to 11.10 I couldn't help but think of delta debs!

Anyone know if there have been any updates or progress on them?

---

### Post by dino99 on 2012-03-18
> **ikt said:**
> While I sit here waiting for over an hour while this natty box updates to 11.10 I couldn't help but think of delta debs!

Anyone know if there have been any updates or progress on them?

oh boy, thats too late on your side :(

---

### Post by grahammechanical on 2012-03-18
Seen this?

[https://wiki.ubuntu.com/UbuntuDebdeltaSupport]("https://wiki.ubuntu.com/UbuntuDebdeltaSupport")

Note the comment about non-trivial changes needed on the server side.

And the unresolved issues.

Otherwise, it sounds like a good idea.

Regards.

---

### Post by VMC on 2012-03-18
This idea of having delta on deb systems has been talked about for a couple of years. It must be more difficult than thought.

That's one of the things I love about Fedora/RPM. 

If I haven't updated Fedora in a while and when I do, as an example, it needs to download 200megs.

 Then delta/presto kicks in and I'm left with only 11 megs to download! This same scenario just happened a few days ago.

 deb systems would need to download the entire 200 megs.

---

### Post by mips on 2012-04-25
Maybe I should start looking at Fedora as a OS then...

---

### Post by sgage on 2012-04-25
> **mips said:**
> Maybe I should start looking at Fedora as a OS then...

Yes, if that is your sole criterion for selecting your OS.

Fedora is an interesting beast, and I try to stay abreast of developments with it. F16 was actually quite nice - solid and usable. Best default wallpaper ever! F17, not so much - in fact the installer ate my backup drive before I caught on to what was happening. But it's still a month away from release.

At the end of the day, I stay with Ubuntu because of the comprehensive repos and the responsive community. The Fedora community is not so bad, either. It's just takes a bit more fiddling to get things set up in Fedora, in my experience.

The diff thing is not a big deal to me - though I guess it might be to some folks. Whatever!

---

### Post by cariboo on 2012-04-25
This seems to come up every development cycle. See Colin's answer [here]("http://askubuntu.com/questions/10167/will-11-04-include-delta-updates/13198#13198")

---

### Post by ranch hand on 2012-04-25
"debdelta" is a package available in the Debian repos.  I have used it.

Was  not particularly impressed.  Do not use it or have it installed on any of my installs currently.

Used it under Debian testing and Sid so there were plenty of updates and upgrades daily.  Saw no real benefit at all.  Actually seemed to take slightly longer than the exact same things run on similar installs with out this "improvement".

It may well be of greater use with rpms as they are slower in my experience anyway.

---

### Post by castrojo on 2012-04-25
> **ranch hand said:**
> Saw no real benefit at all.  Actually seemed to take slightly longer than the exact same things run on similar installs with out this "improvement".

Yeah this is the problem with delta packaging things, you trade bandwidth for I/O, so instead of waiting 10 minutes for a download and 5 minutes to unpack you wait 5 minutes for a download and 10 minutes to unpack. 

I suspect this is why it's not as aggressively pursued as it could be.

---

### Post by sgage on 2012-04-25
> **castrojo said:**
> Yeah this is the problem with delta packaging things, you trade bandwidth for I/O, so instead of waiting 10 minutes for a download and 5 minutes to unpack you wait 5 minutes for a download and 10 minutes to unpack. 

I suspect this is why it's not as aggressively pursued as it could be.

My experience with deltas, exactly. And it seems there are many ways for it to go wrong, especially if you're not upgrading frequently...

---

### Post by Simian Man on 2012-04-25
It's so frustrating as a Linux user that Fedora is the most technologically advanced distro, but Ubuntu has so much more support.  Yum and rpm so much nicer to use.

[quote=castrojo]
Yeah this is the problem with delta packaging things, you trade bandwidth for I/O, so instead of waiting 10 minutes for a download and 5 minutes to unpack you wait 5 minutes for a download and 10 minutes to unpack. 

I suspect this is why it's not as aggressively pursued as it could be.
[/quote]
That sounds good, but my experience using Fedora is the opposite.  Unpacking packages is very fast compared to downloading them.  Maybe if you are running a 386 on a 1 Gbps connection, that would be true.

The reason it isn't pursued is because nobody is willing and able to tackle the problem of updating the old and crusty Debian packaging system.

---

### Post by sgage on 2012-04-25
> **Simian Man said:**
> It's so frustrating as a Linux user that Fedora is the most technologically advanced distro, but Ubuntu has so much more support.  Yum and rpm so much nicer to use.


That sounds good, but my experience using Fedora is the opposite.  Unpacking packages is very fast compared to downloading them.  Maybe if you are running a 386 on a 1 Gbps connection, that would be true.

The reason it isn't pursued is because nobody is willing and able to tackle the problem of updating the old and crusty Debian packaging system.

That sounds good, but my experience of Fedora is the opposite of yours :KS

I'll take apt and deb over yum and rpm any day. Above and beyond speed of upgrades, for which YMMV, yum/rpm doesn't seem to have a concept of autoremove, and unused dependencies build up. In any case, the dpkg system has always seemed in my 15 years of Linux experience to be more robust than rpm.

The reason that delta processing isn't pursued is because the payoff isn't there to make it a high priority.

There, I guess that's settled. :P

---

### Post by castrojo on 2012-04-25
> **Simian Man said:**
> It's so frustrating as a Linux user that Fedora is the most technologically advanced distro, but Ubuntu has so much more support.  Yum and rpm so much nicer to use.

Like many of your claims on this forum, citation needed.

---

### Post by VMC on 2012-04-25
> **Simian Man said:**
> It's so frustrating as a Linux user that Fedora is the most technologically advanced distro, but Ubuntu has so much more support.  Yum and rpm so much nicer to use.


That sounds good, but my experience using Fedora is the opposite.  Unpacking packages is very fast compared to downloading them.  Maybe if you are running a 386 on a 1 Gbps connection, that would be true.

The reason it isn't pursued is because nobody is willing and able to tackle the problem of updating the old and crusty Debian packaging system.

I've had the same experience as you. Preso is fast for me at least. Some folks on the Fedora forums complain as well. I use both. 

When said and done, Ubuntu boots and runs the fastest. That's what really matters to me.

---

