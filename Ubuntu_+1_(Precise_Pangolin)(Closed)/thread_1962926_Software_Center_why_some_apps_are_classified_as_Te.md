---
title: "Software Center: why some apps are classified as Technical items"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pt123 on 2012-04-21
When I tried to install a gmail notifier application, I noticed that gm-notify was hidden away under 'technical items'.
When you search "gmail" it had the highest ratings and the number of reviews.

I was wondering why it was placed under technical items?

Slight off-topic I was perplexed to find Gmail Watcher was not in software center.
[https://launchpad.net/gmailwatcher](https://launchpad.net/gmailwatcher)

When Mark Shuttleworth recommeneded it in his blog 18 months ago.
[http://www.markshuttleworth.com/archives/520](http://www.markshuttleworth.com/archives/520)

---

### Post by critin on 2012-04-21
> When I tried to install a gmail notifier application, I noticed that gm-notify was hidden away under 'technical items'.
When you search "gmail" it had the highest ratings and the number of reviews.

I was wondering why it was placed under technical items?


Probably because it integrates a gmail notification directly into the Ubuntu messaging system.   It is technical.

---

### Post by 3rdalbum on 2012-04-22
Two theories:

1. Packages that do not contain a .desktop file will automatically be classed as a "technical item" in Software Center? An indicator or notification area program might not have a .desktop file.

2. It might be classified as a "technical item" because it uses the old "notification area" API and would need to be whitelisted in Unity before it can work.

---

### Post by fluteflute on 2012-04-22
> **pt123 said:**
> I was wondering why it was placed under technical items?It shouldn't be. This is a bug.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/863869](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/863869)


> **pt123 said:**
> Slight off-topic I was perplexed to find Gmail Watcher was not in software center.
[https://launchpad.net/gmailwatcher](https://launchpad.net/gmailwatcher)Because nobody with the skills to package it for Ubuntu has been motivated to volunteer their time to do so.

[https://bugs.launchpad.net/gmailwatcher/+bug/631019](https://bugs.launchpad.net/gmailwatcher/+bug/631019)

---

