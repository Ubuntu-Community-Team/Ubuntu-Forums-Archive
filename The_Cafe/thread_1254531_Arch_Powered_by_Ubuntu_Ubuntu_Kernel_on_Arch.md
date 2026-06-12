---
title: "Arch Powered by Ubuntu: Ubuntu Kernel on Arch"
date: 2009-08-31
forum: The Cafe
---

### Post by juancarlospaco on 2009-08-31
**[CENTER][SIZE="5"][COLOR="Sienna"]Arch Powered by Ubuntu: Ubuntu Kernel on Arch[/COLOR][/SIZE][/CENTER]**

**When Arch Linux need Stability, uses and recommend Ubuntu LTS Kernel.**

[LIST]
[*][http://www.mail-archive.com/arch-general@archlinux.org/msg07103.html]("http://www.mail-archive.com/arch-general@archlinux.org/msg07103.html")

[*][http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm]("http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm")
[/LIST]

Uses Ubuntu Kernel on Arch to get Stability, the new Kernel are named *"kernel26-lts"*

***Would be nice if they sync the releases* with Ubuntu releases too!***

*[SIZE="1"]*releases, isos, snapshot, whatever[/SIZE]*
:P

---

### Post by eldragon on 2009-08-31
hmm, no, its not ubuntu's kernel.

its kernel.org's 2.6.27 branch.

they might have picked ubuntu patches on the way, but there is nothing that indicates its an ubuntu kernel (if there is such a thing).

when the arch servers are back, i'll check the PKGBUILD and report back.

---

### Post by juancarlospaco on 2009-08-31
***Kernel from Kernel.org 2.6.27.x + All Ubuntu Patch and Optimizations.***

---

### Post by Swarms on 2009-08-31
Could be nice if they synchronised with the Ubuntu release schedule.

---

### Post by juancarlospaco on 2009-08-31
> **Swarms said:**
> Could be nice if they synchronised with the Ubuntu release schedule.

**+1**

They have an *"Arch Brainstorm"* or something...?,
*to post the idea and vote.*

---

### Post by eldragon on 2009-08-31
> **juancarlospaco said:**
> ***Kernel from Kernel.org 2.6.27.x + All Ubuntu Patch and Optimizations.***

where did you get this from? ive been following the arch dev mailing list and there is no mention on using ubuntu's patches.

---

### Post by lykwydchykyn on 2009-08-31
> **Swarms said:**
> Could be nice if they synchronised with the Ubuntu release schedule.

Synchronized what, exactly?  It's a rolling release distro.

---

### Post by Nepherte on 2009-08-31
> **juancarlospaco said:**
> **[CENTER][SIZE="5"][COLOR="Sienna"]Arch Powered by Ubuntu: Ubuntu Kernel on Arch[/COLOR][/SIZE][/CENTER]**

**When Arch Linux need Stability, uses and recommend Ubuntu LTS Kernel.**

[LIST]
[*][http://www.mail-archive.com/arch-general@archlinux.org/msg07103.html]("http://www.mail-archive.com/arch-general@archlinux.org/msg07103.html")

[*][http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm]("http://www.serverwatch.com/tutorials/article.php/3715071/Ubuntu-Server--Kernel-Configuration-Considerations.htm")
[/LIST]

Uses Ubuntu Kernel on Arch to get Stability, the new Kernel are named *"kernel26-lts"*

***Would be nice if they sync the releases* with Ubuntu releases too!***

*[SIZE="1"]*releases, isos, snapshot, whatever[/SIZE]*
:P
And how exactly would you try to synchronize arch with ubuntu releases when arch doesn't have releases? And it's not really based on the "ubuntu kernel". It just uses the latest official kernel-lts branch, with some patches here and there (like the ones from red hat to support ext4 partitions). Your second link is just used as a reference for what settings could be used for a server kernel.

---

### Post by juancarlospaco on 2009-08-31
The same..., 
i got the same Ubuntu and upgrading and upgrading, 
Arch releases a *"Snapshot"* time to time,
syncronize the .ISO release time.

*So this is a "release" of their Distro too.*

---

### Post by Skripka on 2009-08-31
There is so much odd unsupported bizzarro claims in this thread that I've gotten a headache.

---

### Post by snowpine on 2009-08-31
There is some serious confusion in this thread. :) Arch uses the latest stable kernel (2.6.30 currently). All they've done here is make an older kernel available for those who need it (for whatever reason). "When Arch Linux need Stability" implies that Arch uses an unstable, testing kernel, which it does not.

---

### Post by Skripka on 2009-08-31
> **snowpine said:**
> There is some serious confusion in this thread. :) Arch uses the latest stable kernel (2.6.30 currently). All they've done here is make an older kernel available for those who need it (for whatever reason). "When Arch Linux need Stability" implies that Arch uses an unstable, testing kernel, which it does not.

I think the main reason is the ATi drivers, in that often folks revert to trying to use older Xorg versions (which depend on much older kernels) to get the ATi drivers to work with their card.

---

### Post by eldragon on 2009-08-31
> **juancarlospaco said:**
> The same..., 
i got the same Ubuntu and upgrading and upgrading, 
Arch releases a *"Snapshot"* time to time,
syncronize the .ISO release time.

*So this is a "release" of their Distro too.*

actually, sincronizing the arch snapshot would mean squat, since the first thing you do once you install is upgrade to the latest version. heck, everyone using arch knows he/she ought to use the net installer which makes your point moot.

it does not matter which snapshot you use for arch, in the end you get the latest version of packages. this is not the same with a feature frozen distro, like ubuntu. so there.

in response to another poster. yes, there are too much unfounded assertions in this thread.

---

### Post by LowSky on 2009-08-31
My head hurts. Now it did hurt before I started reading this thread, but now its throbbing, and I blame that squarly on some of the statements in this thread. Time for some Advil

Thanks.

---

