---
title: "Formatting issues with gnome 3.8"
date: 2013-04-21
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-04-21
cant format an usb stick from nautilus : it is only unmounted
running gparted from the dash or the terminal ends with an endless scanning

note: i'm logged with gnome-shell.

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1171205](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1171205)

If you are also experiencing the same trouble, then add "affect me too" to get a fix quickly before Raring release.

note2: i've also requested a "parted" upgrade to be able to work with the latest hardware (uefi/gpt)

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1171188](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1171188)

---

### Post by Psychobudgie on 2013-04-21
I'm using 3.8 here with ringtail and getting none of the symptoms you are describing. GParted is working as expected and all my usb mem sticks are also working as expected in both Nautilus and GParted. Are you by any chance using the gnome3-staging PPA aswell as the standard gnome3 ppa? It has major regression issues and I wouldn't recommend using staging unless you are willing to fix things yourself. Any packages held back in Staging are held back for a reason. A couple of issues I am aware of is a problem with Samba and an issue with Power Management. The issue you describe wouldn't come as a major surprise.

---

### Post by dino99 on 2013-04-22
what i get with every cold boot:
- nm-applet crash
- that clutter error: (gnome-shell:3610): Clutter-CRITICAL **: clutter_actor_get_accessible: assertion `CLUTTER_IS_ACTOR (self)' failed

but does not use the "staging" ppa

---

### Post by mc4man on 2013-04-22
> **dino99 said:**
> cant format an usb stick from nautilus : it is only unmounted
running gparted from the dash or the terminal ends with an endless scanning

note: i'm logged with gnome-shell.

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1171205](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1171205)

If you are also experiencing the same trouble, then add "affect me too" to get a fix quickly before Raring release.

note2: i've also requested a "parted" upgrade to be able to work with the latest hardware (uefi/gpt)

[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1171188](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/1171188)

gparted works fine here (there is some extended cursor spin but doesn't affect). Though do have a fairly simple partitioning, only ext4

As far as the format option on removable media thru the nautilus sidebar, doesn't work at all. As mentioned just unmounts if mounted, no formating takes place.
(don't see any current bug reports on that...

---

### Post by dino99 on 2013-04-22
> **mc4man said:**
> 
As far as the format option on removable media thru the nautilus sidebar, doesn't work at all. As mentioned just unmounts if mounted, no formating takes place.
(don't see any current bug reports on that...

that's what i firstly said into lp:1171205

As my partitions have been formatted a few releases back (was after Jaunty), so the actual gparted might be disturbed. 
I suppose it's time to do some new ext4 only partitions in a few days/week to start with something cleaner (the lastest partedmagic seems better than gparted)

---

### Post by mc4man on 2013-04-22
> **dino99 said:**
> that's what i firstly said into lp:1171205

As my partitions have been formatted a few releases back (was after Jaunty), so the actual gparted might be disturbed. 
I suppose it's time to do some new ext4 only partitions in a few days/week to start with something cleaner (the lastest partedmagic seems better than gparted)
I know, but that bug is on gparted, should be one on nautilus
(the option was introduced in 3.7.90 though I don't think I tried it back then.

---

### Post by brainwash on 2013-04-22
> **dino99 said:**
> what i get with every cold boot:
- nm-applet crash

Looks like a gtk+ 3.8 issue. Did you already fill a bug report?

---

### Post by dino99 on 2013-04-22
> **brainwash said:**
> Looks like a gtk+ 3.8 issue. Did you already fill a bug report?

nothing done yet (im too lazy :( ), but i wonder if that nm-applet is an old dupe left behind (QQ dist-upgrade) because the panel has a network icon.
I'm waiting a few days to make a clean new ext4 partition to start RR from scratch.

---

### Post by dino99 on 2013-04-22
> **mc4man said:**
> I know, but that bug is on gparted, should be one on nautilus
(the option was introduced in 3.7.90 though I don't think I tried it back then.

oh you are right, i miss it. Seems to me that i've already read something about that issue somewhere else.

---

