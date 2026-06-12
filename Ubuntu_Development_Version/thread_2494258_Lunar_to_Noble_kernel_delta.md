---
title: "Lunar to Noble kernel delta"
date: 2024-01-10
forum: Ubuntu Development Version
---

### Post by carbonbased80 on 2024-01-10
I have a group of systems which I've been trialing with the current Lunar kernel (6.1.0-16), but would like to eventually deploy with the LTS supported Noble kernel.

When I git clone `git://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/noble`, however, it looks like it's still cloning the Lunar kernel (at least that's the most recent tag reported from `git tag`).

I see some mention that noble may release with a Linux 6.6 kernel.

I'm wondering a few things:
 * Can anyone comment on the likeliness of a 6.6 kernel being used in Noble?
 * Is there a development branch I can use from git://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/noble in order to build a candidate kernel to test with?
 * Are there any expected hurdles/possible-contention-points that might be expected when upgrading/transitioning from the Lunar kernel to the Noble kernel?

Essentially, I'm just looking to get more info, and investigate any risks as early as possible.

Thanks,
Jeff

---

### Post by IanW on 2024-01-11
Both 6.6 & Noble are labelled as "LTS" versions. I'd say it's almost certain.
Noble just jumped to 6.6 the other day.

---

### Post by carbonbased80 on 2024-01-16
When I pull [COLOR=#000000]git://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/noble[/COLOR] it's still pulling 6.1, though (last commit in that branch was 11 months ago).

In order to build/keep-in-sync with the noble distribution, which branch should I be building a kernel out of?  Should I be using master-next (which seems to be a 6.7 now), or some other branch?

Thanks,
Jeff

---

### Post by jbicha on 2024-01-16
I suggest asking at [https://discourse.ubuntu.com/c/kernel](https://discourse.ubuntu.com/c/kernel)

---

