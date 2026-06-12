---
title: "Several Samsung and Crucial SSD bad experiences"
date: 2015-10-05
forum: The Cafe
---

### Post by mike353 on 2015-10-05
[B]Crucial M500 480GB SATA SSD:
[/B]
It ran well for about 5 minutes and then started having these strange performance hiccups where it became sluggish for a bit. So I discovered there was a firmware update but it was a royal pain to apply it because it was only distributed as a DOS (NOT Windows, DOS!) .exe file. So you had to make a FreeDOS boot CD in order to run it. (I think Crucial now distributes a premade bootable DOS iso with it installed.) After that hassle, M500 has worked well.

[B]Crucial M550 512GB msata SSD:
[/B]
OOTB, massive thermal problems! This thing idles at 80C+ independent of OS. (I tried OS X, Linux, FreeBSD.) Firmware update had no effect. Several days wading through various Linux forums led me to TLP and the ability to set the SATA ALPM to minimum power and suddenly the drive was running at 45C idle, 65C under heavy load(ZFS scrub). Seems to work well for the last few months now.

[B]Samsung EVO 850 500GB SSD:
[/B]
I'd heard Samsung had a good rep for SSDs....This was the worst SSD yet! Ubuntu installed fine. Then, after about 10 minutes of apt-get installing various packages, apt-get and dpkg started giving strange errors and stopped working. Googling samsung linux ssd revealed some problem with Native Command Queueing (NCQ) was causing files to be corrupted randomly all over the drive. I was just lucky that parts of dpkg/apt were affected early on to alert me to the problem.  

The kernel was patched (a blacklist to disable NCQ on certain drives) in July, so upgrading IMMEDIATELY after reinstalling seems to have  solved the problem. Let's hope I was quick enough so that not too many files got corrupted. Seems ok, but it's only been a few weeks. I'm never gonna use this drive on work system; this one's relegated to the old retro-gaming/movie watching netbook!

These were all brand new drives and I was attempting to install Ubuntu 15.10. What ever happened to hard drives just working? I could understand if I were testing some obscure piece of hardware on a fringe OS like Haiku or ReactOS, but there's no quality control testing for Ubuntu Linux at Samsung and Crucial? Am I just lucky or is this the typical Linux SSD experience?

---

### Post by QIII on 2015-10-05
Unfortunately, the OEMs apparently did not test well enough on Linux.

However, consider their point of view:  how much effort can you expend on a two percent market share?

And I haven't perused the Windows forums enough to know whether or not Windows users are having similar issues.  Since this is a firmware issue, it may not be limited to Linux at all.

---

### Post by Bucky Ball on 2015-10-05
*Thread moved to **The Cafe**.*

---

### Post by yoshii on 2015-10-07
That's too bad, man.  I'm not as surprised about Samsung issues, but I am surprised about those issues with Crucial.  Too bad.

---

### Post by QIII on 2015-10-07
I'm surprised about Samsung, since they are a Platinum Member of the Linux foundation and they were one of the first, along with Intel, that supported trim with Linux.

---

