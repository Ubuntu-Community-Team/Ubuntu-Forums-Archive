---
title: "Ubuntu 25.04 ‘Plucky Puffin’"
date: 2024-10-30
forum: Ubuntu Development Version
---

### Post by VMC on 2024-10-30
From [OMG]("https://www.omgubuntu.co.uk/2024/10/ubuntu-25-04-officially-opens-for-development") April 17, 2025 release date

---

### Post by corradoventu on 2024-10-31
[https://discourse.ubuntu.com/t/plucky-puffin-release-schedule/36461](https://discourse.ubuntu.com/t/plucky-puffin-release-schedule/36461)
[https://discourse.ubuntu.com/t/plucky-puffin-release-notes/48687](https://discourse.ubuntu.com/t/plucky-puffin-release-notes/48687)

---

### Post by este.el.paz on 2024-10-31
So does this mean that the repos could now be edited from oracular to plucky . . . or sometime in Nov or Dec there would be something to run with?

---

### Post by guiverc on 2024-10-31
> **este.el.paz said:**
> So does this mean that the repos could now be edited from oracular to plucky . . . or sometime in Nov or Dec there would be something to run with?

I've posted *twice* today on a thread on Ubuntu MATE's discourse

[https://ubuntu-mate.community/t/ubuntu-mate-25-04/28433](https://ubuntu-mate.community/t/ubuntu-mate-25-04/28433)

First post (I made; ~four hours ago) had me report only the *official* news as I know it, in that the repositories were *open for development* (ML thread to that), and note that the *meta-development* release file still reported no *plucky* as available..

A little over two hours later though you'll note another by me, where *plucky* was available for 

```

do-release-upgrade -d

```

use, in fact this machine is now running PLUCKY, as I've upgraded using the `do-release-upgrade -d` option myself earlier today.. and have now rebooted into *plucky*

```

OS: Ubuntu Plucky Puffin (development branch) x86_64 

```

---

### Post by corradoventu on 2024-11-01
I have been using it for more than a week having changed ubuntu.sources
[https://ubuntuforums.org/showthread.php?t=2501545&p=14210493#post14210493](https://ubuntuforums.org/showthread.php?t=2501545&p=14210493#post14210493)
[https://ubuntuforums.org/showthread.php?t=2501545&p=14210492#post14210492](https://ubuntuforums.org/showthread.php?t=2501545&p=14210492#post14210492)

---

### Post by este.el.paz on 2024-11-02
Alrighty . . . booted up in Lubuntu Plucky as we type . . . !!!  In my case the # do-release-upgrade -d  option kept bringing, "please update your system to the latest upgrades" . . . and the "nano sources.list.d/ubuntu xxxx" went to a blank file . . . .  Went back to the simple # nano /etc/apt/sources.list   and changed oracular to plucky . . . ran the update/ugrade . . . removed the unwanted grub-common os-prober  flipped over to my grub handling system to update the bootloader and back over to . . . plucky!!!!

---

### Post by guiverc on 2024-11-02
We don't have *plucky* ISOs yet to test (*too early at this stage*), but a request was made to test out *dracut* ([https://discourse.ubuntu.com/t/please-try-out-dracut/48975](https://discourse.ubuntu.com/t/please-try-out-dracut/48975)) and changes are being made so the ISOs using `calamares` will use this.

[Simon's post refers to Lubuntu]("https://discourse.ubuntu.com/t/please-try-out-dracut/48975/12"), but *flavor* leads of others using `calamares` (Kubuntu, Ubuntu Unity) also gave approval for change, so when we get some dailies built, testing maybe useful to ensure the ISOs boot, and install correctly as they did before...

This is still in the future, but we may have ISOs building this [coming] week.

---

