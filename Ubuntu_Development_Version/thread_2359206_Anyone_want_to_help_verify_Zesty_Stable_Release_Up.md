---
title: "Anyone want to help verify Zesty Stable Release Updates?"
date: 2017-04-21
forum: Ubuntu Development Version
---

### Post by jbicha on 2017-04-21
Is there anyone still on Ubuntu 17.04 Zesty that would be interested in verifying some Stable Release Updates? At the time I am writing this, the Artful archives are closed which means they probably aren't that interesting to y'all yet.

Visit the [SRU tracker]("https://people.canonical.com/~ubuntu-archive/pending-sru.html").
If you scroll down towards the bottom, you'll see several uploads targeted at zesty.
Right now, there's all the old zesty-proposed stuff that will just be moved over to artful-proposed soon. I would ignore anything that wasn't accepted into zesty-proposed after zesty was released.
In the second to last column are the LP bug reports for the update. If they are colored green, they've already been verified.
If not, you can read the bug report. If it's interesting to you, you can install the updated packages from zesty-proposed.
If the update works for you, and you can complete the Test Case, leave a comment on the bug. Mention the exact version you tested and on what system. (We don't really want to have verifications for zesty-proposed updates on artful, sorry!).
You can then edit the tags line of the bug to remove verification-needed and add verification-done.

If the bug affects multiple Ubuntu series (like if it affects Yakkety too), don't set it to verification-done until you've tested the Yakkety update too. If you only test the Zesty version, you can set the tag to verification-done-zesty though.

The tracker gets updated periodically. If you set a bug to verification-done, the bug will turn green on the tracker, maybe in an hour or so.

Once an update has been verified successfully with no issues and it has been at least 7 days in -proposed, it can be released as an update by a member of the Stable Release Update team.

You can read the wiki for more details about how [Stable Release Updates]("https://wiki.ubuntu.com/StableReleaseUpdates") work.

---

### Post by howefield on 2017-04-24
> **jbicha said:**
> Visit the [SRU tracker]("https://people.canonical.com/~ubuntu-archive/pending-sru.html").

"503 Service Temporarily Unavailable" error on the link.

---

### Post by ventrical on 2017-04-24
> **howefield said:**
> "503 Service Temporarily Unavailable" error on the link.

  same here "down for service"

---

### Post by jbicha on 2017-04-24
Yes, some critical infrastructure is getting upgraded today so some services aren't working right now.

---

### Post by howefield on 2017-04-24
> **jbicha said:**
> Yes, some critical infrastructure is getting upgraded today so some services aren't working right now.

Cool, thanks jchiba, will have another go tomorrow.

---

### Post by #&amp;thj^% on 2017-04-24
> **jbicha said:**
> Is there anyone still on Ubuntu 17.04 Zesty that would be interested in verifying some Stable Release Updates? At the time I am writing this, the Artful archives are closed which means they probably aren't that interesting to y'all yet.

Visit the [SRU tracker]("https://people.canonical.com/~ubuntu-archive/pending-sru.html").
If you scroll down towards the bottom, you'll see several uploads targeted at zesty.
Right now, there's all the old zesty-proposed stuff that will just be moved over to artful-proposed soon. I would ignore anything that wasn't accepted into zesty-proposed after zesty was released.
In the second to last column are the LP bug reports for the update. If they are colored green, they've already been verified.
If not, you can read the bug report. If it's interesting to you, you can install the updated packages from zesty-proposed.
If the update works for you, and you can complete the Test Case, leave a comment on the bug. Mention the exact version you tested and on what system. (We don't really want to have verifications for zesty-proposed updates on artful, sorry!).
You can then edit the tags line of the bug to remove verification-needed and add verification-done.

If the bug affects multiple Ubuntu series (like if it affects Yakkety too), don't set it to verification-done until you've tested the Yakkety update too. If you only test the Zesty version, you can set the tag to verification-done-zesty though.

The tracker gets updated periodically. If you set a bug to verification-done, the bug will turn green on the tracker, maybe in an hour or so.

Once an update has been verified successfully with no issues and it has been at least 7 days in -proposed, it can be released as an update by a member of the Stable Release Update team.

You can read the wiki for more details about how [Stable Release Updates]("https://wiki.ubuntu.com/StableReleaseUpdates") work.
I went ahead and hand changed all zesty-proposed stuff to artful--proposed so that i would not be confused by the two.

> **howefield said:**
> "503 Service Temporarily Unavailable" error on the link.
I also see the same as howefield..."503 Service Temporarily Unavailable" error on the link.

---

### Post by ventrical on 2017-04-24
> **howefield said:**
> Cool, thanks jchiba, will have another go tomorrow.

If you scroll down to the bottom you will see pending here:

[http://people.canonical.com/~ubuntu-archive/pending-sru.html](http://people.canonical.com/~ubuntu-archive/pending-sru.html)

---

### Post by ventrical on 2017-04-24
> **jbicha said:**
> Yes, some critical infrastructure is getting upgraded today so some services aren't working right now.

Oh yeah .. it's there now.

---

