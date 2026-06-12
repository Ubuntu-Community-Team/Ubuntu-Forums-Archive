---
title: "Is Budgie remix 16.04 an LTS?"
date: 2017-03-15
forum: Ubuntu Development Version
---

### Post by lysander6662 on 2017-03-15
I really like Budgie and am interested to install it as my default DE. I could always go with Solus, but Solus doesn't feel as stable to me as Ubuntu, and additionally the Ubuntu community is very helpful. I am also getting quite used to apt-get now.

I am downloading an ISO of budgie remix 16.04.2. Is this supported by Canonical or not? I don't understand the difference seeing as it's build on Ubuntu. Theoretically it would be, wouldn't it? Or maybe it's not because it's not an official flavour, though 17.04 onwards would be. Nevertheless, does it matter if it's not official? Presumably if it's built on 16.04 it would be very stable anyway, would it not?

---

### Post by howefield on 2017-03-15
> **lysander6662 said:**
> I am downloading an ISO of budgie remix 16.04.2. Is this supported by Canonical or not?

From the [website ]("https://budgie-remix.org/downloads/"): 

> 16.04 is community supported – it is supported until upstream ends support (no current plans) and thereafter, as long as budgie-remix users wish to maintain its support.

Any underlying packages from the Ubuntu repositories will likely get the support of Canonical updates for the length of the 16.04 support cycle, but the rest, as above.

---

### Post by lysander6662 on 2017-03-15
Ah, right. Well that answers the first question. Thanks for that. The second: does it matter if it's not supported by Canonical? I suppose I could ask a better question, which would be, what are the differences between community support and Canonical support? Does the community create content or are their contributions purely advisory? Also, I have to admit to being rather ignorant as to what 'upstream support' means.

---

### Post by davidmohammed on 2017-03-15
"upstream" in this case means the developers of budgie-desktop itself.

Usually for Ubuntu releases, the version of the desktop becomes static.  It receives only critical and stability updates.  Not new features.  Some community flavours backport newer versions and make this available via a PPA.

Budgie-remix does not take the usual official community flavour route of a static version - we try to bring the latest version as soon as it is reasonably possible after upstream signals its availability.

Shortly v10.3 will be released.  Thereafter v11 of budgie-desktop sometime this year.  v11 we are not certain at this early stage whether this will be installable on 16.04 LTS because of the relatively old QT packages available in the repositories.

If v11 is not installable then v10.3 will be the last main release under the upstream budgie-desktop umbrella.  Again - no current plans by upstream to say no further support of the v10.3 series once v11 is available.

Assuming at some future date v10.3 becomes no longer supported by upstream, I'm happy to coordinate future developments to the v10.3 series assuming there is interest by any users and developers (of whatever flavour of GNU/Linux).

At this stage though, this is all hypothetical.  v10.3 looks to be an exciting release and we look forward to bringing this for 16.04 users

David (project lead budgie-remix / Ubuntu Budgie)

---

### Post by lysander6662 on 2017-03-16
Thanks David, an interesting post. I had to read it a few times to grasp what's going on. So, by the looks of things, 16.04 doesn't have a set life-cycle end date of 2021 like 16.04 standard, but the end date is basically "as long as it's supported" by the UB team. Fair enough. I take it the end dates for 17.04+ going forward will be set now that UB is an official flavour. I really like the beta of 17.04 UB and am looking forward to seeing what comes of it.

---

### Post by jbicha on 2017-03-16
Budgie Remix is special because it uses a PPA.

What's your update policy for Ubuntu Budgie (the official flavor)?

---

### Post by davidmohammed on 2017-03-16
For Ubuntu Budgie we'll be following normal rules; where there are critical or stability fixes required, follow standard SRU (stable release updates) - [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

For new budgie-desktop versions we'll be using our backports PPA (you can enable this via budgie-welcome) - similar I suppose how kubuntu does newer plasma versions.

---

### Post by lysander6662 on 2017-03-18
I'm using the latest daily build and it's beautiful. Love the amount of control and customisation given to the user, the whole DE feels very smooth and stable. It's a different feel to Unity - Unity feels like it has depth whereas Budgie feels more level. Budgie also feel like there is a lot more space around the desktop in general. 

Is there a way of changing the colour of the highlighted bars in raven/main menu and the main ? At the moment they're blue, can this be modified?

---

### Post by davidmohammed on 2017-03-21
that is the arc-theme.  I've seen various people rave about this - never tried it myself.  [https://github.com/erikdubois/Arc-Theme-Colora](https://github.com/erikdubois/Arc-Theme-Colora)

Other than that - use a different theme - e.g. vimix/paper/adapta.

---

### Post by Frogs Hair on 2017-03-23
I use Budgie on 16.10 , but it is from the repository and not the remix PPA . The remix PPA used with 16.04 upgrades nautilus and affects how nautilus works in Unity which is fine if you only use Budgie. The underlying 16.04 OS is LTS . I've found some some 3rd party themes that work very well in Budgie and others not so well. I did install the remix version of plank via .deb on 16.10 because has more features than the version in the 16.10 repository.

---

