---
title: "Ouch"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kelpdip on 2012-03-02
I was looking forwards to trying this, installing from scratch, but this is the most broken ubuntu beta I've ever seen. Three separate problems are preventing install.

1: Memory leak in ubiquity gives it ~10 minute lifespan before requiring command line kill.

2: Odd Realtec wireless regression. Mostly working wifi, but constant attempts in syslog to reload rtl8192cfw.bin
Possibly related to #1?

3: Custom partition setup bug prevents installing over 2 existing partitions, which is a very common set-up.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/924660](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/924660)

Normally I like to check out the LTS betas as a preview, but this installer is a train wreck, and there is no "alternate install". Anyone succesfully work around these problems? Hardware is a x120e thinkpad.

---

### Post by lnxguit on 2012-03-02
The "desktop" iso wouldn't work for me because of the partitioning bug, but the "alternate" iso worked great. I think this will be a solid LTS.

---

### Post by kelpdip on 2012-03-02
> **lnxguit said:**
> The "desktop" iso wouldn't work for me because of the partitioning bug, but the "alternate" iso worked great. I think this will be a solid LTS.

*Where can I find the alternate iso? It's not in the precise daily / beta directory.*

Nevermind, found it, didn't look hard enough. The directory listing on the beta release page is incomplete.

---

### Post by cariboo on 2012-03-02
> **kelpdip said:**
> I was looking forwards to trying this, installing from scratch, but this is the most broken ubuntu beta I've ever seen. Three separate problems are preventing install.

1: Memory leak in ubiquity gives it ~10 minute lifespan before requiring command line kill.

2: Odd Realtec wireless regression. Mostly working wifi, but constant attempts in syslog to reload rtl8192cfw.bin
Possibly related to #1?

3: Custom partition setup bug prevents installing over 2 existing partitions, which is a very common set-up.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/924660](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/924660)

Normally I like to check out the LTS betas as a preview, but this installer is a train wreck, and there is no "alternate install". Anyone succesfully work around these problems? Hardware is a x120e thinkpad.

That's why you are testing the Precise beta, to file bug reports on the problems you run into.

If you're not sure how to file a bug, I'd suggest you review [this]("https://help.ubuntu.com/community/ReportingBugs") page

---

