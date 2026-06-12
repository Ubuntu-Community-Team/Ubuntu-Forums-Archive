---
title: "Nov 12 2011 Adobe Flash Player Plugin installer update 30 min+ to install?  (10.10)"
date: 2011-11-12
forum: Security
---

### Post by Lido on 2011-11-12
I woke up this morning to a couple of Apache updates (probably from yesterday), so I ran them. Then when those finished, there was a new Adobe Flash Player Plugin installer update listed in the Update Manager window by itself. It was 20k, so no problem, install. It's been hung up in the "configuring" phase of the install forever and it looks like it's either receiving or sending data blocks that if my math is right will end up being 13MB. I'll attach a screenshot to this message. Any idea what's going on with this? Could it be sending my entire home directory somewhere...or anything else? I can't see why Flash would need 13MB and take a half hour to install unless it is actually 13MB and their server throttles the bandwidth on individual connections that each installer makes. Maybe this is nothing to worry about, but I haven't seen this before and I've been using Ubuntu for about six years. Thanks.

[IMG]http://i41.tinypic.com/35aog7t.jpg[/IMG]

---

### Post by BillyBoa on 2011-11-12
I made the same update this morning and took me 3-4 minutes. Maybe you should reinstall flash from Synaptic.

---

### Post by lovinglinux on 2011-11-12
Flash is not actually installed from the package. When you install the update, it actually downloads the new version from Adobe or from the partner repo. That's why you saw a 20k package, but a 13Mb download. Nothing to worry about. The Adobe/Partner server was busy.

BTW, I am testing it right now and it is really slow. Will take 19 minutes to download. This problem happens from time to time with the partner repo.

---

### Post by Lido on 2011-11-13
Cool, thanks. Always nice to hear that things are ok and no action is necessary.

---

