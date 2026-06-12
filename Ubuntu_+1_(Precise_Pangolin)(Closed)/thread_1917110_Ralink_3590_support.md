---
title: "Ralink 3590 support?"
date: 2012-01-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by exploder on 2012-01-29
Will Ubuntu 12.04 support the Ralink 3590 WiFi adapters that are in many of the new HP laptops? Is anyone using a Ralink WiFi?

---

### Post by kaldor on 2012-01-29
If it is not in 12.04 immediately, it will likely get backported into the kernel sometime after it is made available. For example, my new HP desktop had no wireless available on Natty, but the drivers made their way into a kernel update about a month after I bought the PC.

Ralink is usually quite good for compatibility, so I wouldn't worry too much.

---

### Post by exploder on 2012-01-29
Thanks kaldor! I got a new HP laptop for Christmas and still have Windows 7 on it because I have not been able to get the WiFi to work in Linux. I have Ubuntu 12.04 x64 running in Virtualbox right now and am thinking that Unity might be just the thing for the laptop.

My desktop has a huge monitor but the laptop might be easier to use with Unity. I do not want to constantly update the laptop because I do not use it as much as I do the desktop and an LTS release might be an ideal solution.

I have seen drivers available for Linux for the WiFi and am wonering if 12.04 will include them. Unity might be an ideal solution for my laptop.

---

### Post by exploder on 2012-01-29
Just tried today's daily build and the Ralink WiFi is supported out of the box!

Edit: Tried installing the daily build on the laptop but the installer would not get past the check list screen. At least I know there is hope for my WiFi.

---

### Post by kaldor on 2012-01-29
> **exploder said:**
> Just tried today's daily build and the Ralink WiFi is supported out of the box!

Edit: Tried installing the daily build on the laptop but the installer would not get past the check list screen. At least I know there is hope for my WiFi.

Good to know :)

Maybe by now your wireless will work on Oneiric. I just took a look at 11.10's [kernel changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_3.0.0.16.19/changelog"), and apparently some wireless stuff has been backported and is sitting in the proposed repo:

> 
linux-meta (3.0.0.16.19) oneiric-proposed; urgency=low

  [ Leann Ogasawara ]

  * Add compat-wireless v3.2 meta package
    - LP: #918351

 -- Herton Ronaldo Krzesinski <herton.krzesinski@canonical.com>  Wed, 25 Jan 2012 15:46:43 -0200


It might be worth a shot if you have the time to play around with it.

---

### Post by exploder on 2012-01-29
11.10 does not like my ATI graphics... All I get is a black screen. I don't mind waiting for the LTS release to go final. Thanks anyways though.

---

