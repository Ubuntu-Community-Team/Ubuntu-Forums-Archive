---
title: "trying to understand this Lubuntu support chart"
date: 2020-08-13
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2020-08-13
[IMG]https://lubuntu.me/wp-content/uploads/2019/07/cycle.png[/IMG]
I'm running Lubuntu 18.04 64-bit.

From the way I understand this support chart, the Lubuntu Team will support Lubuntu 18.04 until 2021, then it's support is transferred to the Ubuntu Community. What does this mean exactly? Does this mean that I can use Lubuntu 18.04 until 2023 with support from the Ubuntu Community? I'm quite happy with Lubuntu 18.04 and would love to use it for a couple of more years really.

---

### Post by guiverc on 2020-08-13
Where does the chart come from?

The Lubuntu Team support for 16.04 has ended, and yes Lubuntu 18.04 LTS provide support until 2021-April.

  The Lubuntu team however is part of the Ubuntu Community, and all Community support sort of ends in 2021-April for 18.04 LTS packages (all flavors end support for 18.04), only 'main' repository software is supported after then (with minor exceptions) only by Canonical.  

I suspect they are talking about user support sites like this, where some people in the community still support beyond the 3 years of 'community' support for packages, though that support is possibly reduced, as people associated with flavors do tend to ignore systems that formally are EOL.

Past 2021-April, the base on which Lubuntu 18.04 LTS (along with all other flavors) will continue with Canonical support, but this applies to 'main' repository software only. 

You can use `ubuntu-support-status` to view the status for your own installed system.

I'd like to know where the chart comes from though.

---

### Post by wildmanne39 on 2020-08-13
Moved to Ubuntu, Linux and OS Chat.

---

### Post by ardouronerous on 2020-08-13
It came from here: [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by ardouronerous on 2020-08-13
Here's what ubuntu-support-status says:

```
~$ ubuntu-support-status

You have 316 packages (17.9%) supported until April 2021 (Community - 3y)
You have 1375 packages (77.7%) supported until April 2023 (Canonical - 5y)
You have 3 packages (0.2%) supported until April 2021 (Canonical - 3y)

You have 6 packages (0.3%) that can not/no-longer be downloaded
You have 69 packages (3.9%) that are unsupported
```

---

### Post by guiverc on 2020-08-13
Thank you.

Yep....   (*loud sigh....*)

I believe it means what I've stated, however I'm going to suggest we (*Lubuntu*) change the wording on that page (*hopefully I'll think of something better; possibly "Wider Ubuntu Community Support", however as it applies really to 'main' or our base system package support that's still rather vague..*).

Thanks for asking, and bringing that to my attention.

As an FYI: If I see a Lubuntu 16.04 LTS question on Ask Ubuntu, I tend to paste this as comment

> FYI: Lubuntu 16.04 LTS being a flavor of Ubuntu had only 3 years of supported life ([https://lubuntu.me/xenial-5-released/](https://lubuntu.me/xenial-5-released/) [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)) which ended 2019-April. Ubuntu 16.04 LTS Server (no desktop) or Desktop (Unity 7) have 5 years of supported life and are still supported. Refer release notes, or use `ubuntu-support-status` or your own system to confirm this is the case. I suggest you move to a supported release of Lubuntu for security reasons, unless you're off-line or are aware of risks.

If the OP (original poster) continues, my next post is usually

> Site rules say only supported releases (not development, EOL/ESM etc), and Ubuntu doesn't want to encourage people using unsupported or past-EOL software, thus you'll not get much support from people associated with Ubuntu projects, flavors, members etc. We of course are happy for people to continue using our software past its supported life, but you're on your own, and cannot any longer use Canonical/Ubuntu infrastructure (this is an official Ubuntu site).

(Additional detail:  *Since I brought up Ask Ubuntu [if you're familiar with it], I personally don't close-vote questions on EOL flavors when the release is still supported with Ubuntu desktop/server of the same release*)

My approach (*which was suggested by others when I became associated with Ubuntu, and learnt of the EOL for flavors when compared to main Ubuntu*) differs to some Ubuntu community members though who'll happily support Ubuntu flavors until the 'main' Ubuntu 16.04 LTS reaches it's EOL (many of them are users themselves of flavors beyond the 3 years of flavor support for LTS).

I'll also add, I'm aware in a number of circumstances & cases where flavors clear their PPAs of packages when that flavor reaches EOL (*eg. 18.04 will be cleared out come 1st-May-2021, though it may be delayed if it's overlooked or people are busy; and don't think I'm only speaking about Lubuntu here*).

My answer is primarily my own opinion, my own understanding as I see it, and as I express it. Lubuntu is no different to other Ubuntu flavors however (at least in my experience).

(*anyway, I've got the page to think about&#8230; we've got the Lubuntu 18.04.5 LTS release [amd64 & i386] in a number of hours, so the page won't be discussed or changed toda*y)

---

### Post by ardouronerous on 2020-08-13
Thanks for all the info, so I have until next year to upgrade. I usually upgrade via clean install. Thanks for all the info again!

---

### Post by mastablasta on 2020-08-13
the apps (e.g. firefox, libre office) still get updated. also the core of the OS (kernel, drivers etc.), the only thing that stays the same is desktop. the desktop itself doesn't get updated. so if there is security issue in the desktop itself then it could be an issue. however as i've been following updates - usually the desktop is not often updated. mainyl in the first year or two and then it is not.

so it *should* be safe to continue to use it, but there is no guarantee. but then again someone can enter thrugh updated OS as well. there is no 100% security there is just risk management. just like with Covid19 at the moment.

---

