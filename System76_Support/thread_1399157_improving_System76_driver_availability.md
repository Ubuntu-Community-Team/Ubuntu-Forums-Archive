---
title: "improving System76 driver availability"
date: 2010-02-05
forum: System76 Support
---

### Post by tlroche on 2010-02-05
> **thomasaaron said:**
> Our web hosting service is experiencing a data center-wide outage. We are currently transferring our site to other servers and expect this process to take a couple of days.


As noted, this creates problems for System76 as a business

> **thomasaaron said:**
> we will be unable to take orders while the site is down


but it also creates problems for users, e.g.

> **tlroche said:**
> [I] started a Software Update on the kernel, which is invoking a connection to planet76.com, which is stuck in a loop of timeout/retry.

> **nealaustin said:**
> without the planet 76 repository any upgrade or this fix keeps timing out. Right now I'm without wireless until my Starling can reconect

So I'm wondering, 

[LIST=1]
[*]what **should** System76 do to improve the availability of the System76 driver and therefore the reliability of upgrades, fixes, and installs? E.g. better mirroring?
[*]what **is** System76 doing, or planning to do, to improve the reliability of upgrades, fixes, and installs?
[/LIST]

---

### Post by thomasaaron on 2010-02-05
> As noted, this creates problems for System76 as a business

You're not just whistling Dixie.

> but it also creates problems for users, e.g.

Unfortunately, that is absolutely true.

> 1. what should System76 do to improve the availability of the System76 driver and therefore the reliability of upgrades, fixes, and installs? E.g. better mirroring?

Good question. But I'm going to have to leave it to my managers to address that issue. I'm not really in a position to address infrastructure questions. 

But from a practical perspective, even Ubuntu's mirrors go down from time to time. And the fact that this is the first time we've had a problem of this magnitude probably shows a pretty solid track record. Personally, more mirrors seems like a reasonable idea, though.

To be completely honest, right now everybody is in scramble mode to get everything back up with a more stable hosting company. That should solve some problems right there.

> 2. what is System76 doing, or planning to do, to improve the reliability of upgrades, fixes, and installs?

Same answer as above.

---

### Post by samalex on 2010-02-05
No site has 100% uptime, not even Microsoft, Google, or Yahoo.  I've been following the System76 site for years, and this is the first time I've seen it down.  For me being a web admin many times over the years I know s**t always happens whether your data is hosted in house or at a colo facility.

Granted people will always scream when the site is down, but honestly it's no blow to the reputation of System76.  Just part of dealing with online services.

FWIW...

Sam

---

### Post by Flyers2391 on 2010-02-05
> **samalex said:**
> No site has 100% uptime, not even Microsoft, Google, or Yahoo.  I've been following the System76 site for years, and this is the first time I've seen it down.  For me being a web admin many times over the years I know s**t always happens whether your data is hosted in house or at a colo facility.

Granted people will always scream when the site is down, but honestly it's no blow to the reputation of System76.  Just part of dealing with online services.

FWIW...

Sam

Well said!

---

### Post by tlroche on 2010-02-05
> **tlroche said:**
> [LIST=1]
[*]what **should** System76 do to improve the availability of the System76 driver and therefore the reliability of upgrades, fixes, and installs? E.g. better mirroring?
[*]what **is** System76 doing, or planning to do, to improve the reliability of upgrades, fixes, and installs?
[/LIST]

> **thomasaaron said:**
> I'm going to have to leave it to my managers to address [the second] issue. I'm not really in a position to address infrastructure questions. [Right] now everybody is in scramble mode to get everything back up with a more stable hosting company.

Fair enough. You might keep us posted on what management decides.

> **samalex said:**
> For me being a web admin many times over the years I know s**t always happens whether your data is hosted in house or at a colo facility.


Whether the data is located or colocated is not the issue, it's uptime. And just saying "bleep happens" is no substitute for actually preventing future downtime, which one does by

[LIST=1]
[*]**adaptation** to future failures, e.g. by providing redundant external providers and modifying ```
/opt/system76/system76-driver/src/*.py
``` to use them
[*]**mitigation** of future failures, e.g. by rollover or hotswap to redundant (internal) hosts
[/LIST]

or both.

> **samalex said:**
> people will always scream when the site is down, but honestly it's no blow to the reputation of System76.


People scream because this downtime affects their lives (e.g. breaking installs, updates, upgrades), and those effects are precisely what damage the reputation of System76. That's not a major deal for a bunch of home users and hobbyists, but suppose you were a small business considering forklifting out M$. How interested would you be in a vendor that "just went down" for a couple days?

Net: being pro-System76 does **not** mean ignoring its problems.

---

### Post by jdb on 2010-02-05
> **tlroche said:**
> 
And just saying "bleep happens" is no substitute for actually preventing future downtime

No, but it's a fair thing to say.
No matter what precautions you take or how conscientious you are,

"bleep happens".

And the result in my experience is,

"We're bleeped"

A customer once gave one of my colleagues a hat after big job,
it had the letters,

SHWF

on the front of it :lolflag:


jdb

---

