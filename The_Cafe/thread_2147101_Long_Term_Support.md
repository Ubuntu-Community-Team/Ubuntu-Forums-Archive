---
title: "Long Term Support"
date: 2013-05-20
forum: The Cafe
---

### Post by Dave_L on 2013-05-20
What exactly does "Long Term Support" mean? (In the context of, for example, "Ubuntu 12.04 LTS")

Does it include general bug fixes, or only security patches?

I couldn't find a policy statement on this.

---

### Post by ibjsb4 on 2013-05-20
This may help

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Dave_L on 2013-05-20
> **ibjsb4 said:**
> This may help

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Not really.  I didn't see an answer to my question there.

---

### Post by binaryhermit on 2013-05-20
This doesn't exactly solve your question, but from the announcement of 11.10's EoL regarding 12.04 (the latest LTS release)
>  Ubuntu 12.04 continues to be actively supported with security updates and select high-impact bug fixes.
Which implies that LTS releases get some, though probably not all, non-security bug fixes.

---

### Post by fontis on 2013-05-22
> **Dave_L said:**
> What exactly does "Long Term Support" mean? (In the context of, for example, "Ubuntu 12.04 LTS")

Does it include general bug fixes, or only security patches?

I couldn't find a policy statement on this.

It pretty much means what it says. The OS has a longer support cycle with updates with regards to stability.
This essentially means that no packages that will break your system will be pushed into your install and maintenance of your system will evolve around fixing whatever bugs that show up. And since most of the apps included in a LTS release are so stable, most fixes just simply evolve security flaws being fixed.

---

### Post by Koori23 on 2013-05-23
Ubuntu and KUbuntu both have 5 year LTS releases I believe, for some reason, XUbuntu only has 3 years between LTS's. 

Think of it in terms of Windows XP. Windows XP has gotten 3 full service packs and lord only knows how many security updates since service pack 3. Windows XP hasn't received any real new "features" since the last service pack. just security updates. Take a look at it vs Windows 7 or 8 and compare feature lists. Apparently that's okay too because people seem to be clinging to XP for dear life nearly 13 years after it's release.

Updates to software could be defined as a security update. Firefox, Flash, Chrome(ium) have all been updated and released in the 12.04 repos VERY recently as well as various kernel patches and updates. Basically, from here on out, expect minor kernel updates in order to support new hardware, updates to internet facing applications among other minor tweaks too numerous to mention. Just don't expect any earth shattering new featues Canonical comes up with may come up with in the next few years.

Why have LTS releases? Well, folks at Google, Wikipedia, City of Munich and many other enterprise level Ubuntu users can't be as fluid and just update the OS every 6 months for fear you'll have a entire organization with broken systems. Many of these organizations use Ubuntu on the server and client side. With that, they have special custom packages that they use internally that might depend on a library or something that might not work in a newer release. These are very high profile targets and downtime is something they can't have.

---

### Post by philinux on 2013-05-23
> **Dave_L said:**
> What exactly does "Long Term Support" mean? (In the context of, for example, "Ubuntu 12.04 LTS")

Does it include general bug fixes, or only security patches?

I couldn't find a policy statement on this.

Nice explanation here.
[http://www.howtogeek.com/162768/should-you-use-ubuntu-lts-or-upgrade-to-the-latest-release/](http://www.howtogeek.com/162768/should-you-use-ubuntu-lts-or-upgrade-to-the-latest-release/)

---

### Post by Dave_L on 2013-05-23
Most of what I've read seems to say that if you're happy with the existing feature set, then stick with the LTS version. There no reason to upgrade to the non-LTS versions unless you want the new features.

But at the same time, some (most?) bugs in the LTS version are not getting fixed, and you have to upgrade to the newest (unstable) version to get those fixes.

That's what I'm unclear about.

See this post, for example: [http://ubuntuforums.org/showthread.php?t=2143584&p=12652457#post12652457](http://ubuntuforums.org/showthread.php?t=2143584&p=12652457#post12652457)

---

### Post by castrojo on 2013-05-23
You can get a new kernel on 12.04 so you can stay on the stable userspace and LTS support:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Dave_L on 2013-05-23
> **castrojo said:**
> You can get a new kernel on 12.04 so you can stay on the stable userspace and LTS support:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I don't fully understand that.

Here's my current kernel, upgraded last week:

> $ uname -a
Linux ... 3.5.0-30-generic #51~precise1-Ubuntu SMP Wed May 15 08:48:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Are you suggesting there's a newer recommended kernel for Ubuntu 12.04.2 LTS?

---

### Post by castrojo on 2013-05-23
Hmm so if the bug is fixed in the quantal kernel but you seem to have it and still having the problem you can try the raring kernel which is backported to the LTS too. 

sudo apt-get install linux-generic-lts-raring

should do the trick and get you up on a 3.8 kernel, then boot into it and see if you're still having the problem.

---

### Post by Dave_L on 2013-05-23
That seems to be 3.8.0.21.20, which is available through synaptic.  Thanks, I'll try that.  If it doesn't work, it's easy enough to revert to the previous kernel.

(That still doesn't explain the LTS conundrum, though.)

---

### Post by castrojo on 2013-05-23
Bugs do get fixed for the LTS, the way it works is let's say your bug is fixed in a future version of ubuntu, it becomes a candidate to be fixed in the LTS through something called the SRU process: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

So major issues are usually fixed and over the life of the LTS. The main problem in the past is that it totally sucked for hardware support if an LTS came out and then a 3 months later a new kind of laptop comes out and the LTS won't run on it or wireless doesn't work or something.

Since the ubuntu kernel team has to maintain kernels for the releases inbetween LTSes _anyway_ the idea is that it's easier for us to just support running those kernels on the LTS. That way you have a stable experience that is supported with bugfixes and security fixes and you get a newer kernel that will work on your hardware. Then a few years down the road when the next LTS comes out everyone gets realigned to that stable kernel. And so on.

---

### Post by Dave_L on 2013-05-23
castrojo: Thanks for the explanation.  That SRU process documentation makes me feel better about the LTS situation.

I upgraded to kernel 3.8.0-21, and so far suspend/resume has been working properly.  :)  But I'll give it a few more days of testing before I'm certain.

Is there an easy way of seeing what kernel changes between 3.5.0-30 and 3.8.0-21 might have affected suspend/resume?

---

