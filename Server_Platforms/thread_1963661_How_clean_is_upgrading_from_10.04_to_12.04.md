---
title: "How clean is upgrading from 10.04 to 12.04?"
date: 2012-04-22
forum: Server Platforms
---

### Post by xclusive585 on 2012-04-22
Normally, I ALWAYS do clean installs. And planned on doing my server over from scratch with 12.04.

But what if, to save myself from re-doing months of setup, I just do an upgrade using the update manager core?

How clean is it? What are the chances of breaking working packages?

In the end, is an upgraded 12.04 system in ANY WAY different from a clean install of 12.04? I know with windows for example you get a pretty butchered registry when you do an upgrade. Are there any similar downfalls to upgrading Ubuntu?

---

### Post by jerome1232 on 2012-04-22
The main thing to watch out for is sometimes the way config files are written change when you upgrade to the new packages, the update will alert you if a config file is different than the one incoming and give you a chance to inspect and compare the files, modify it, keep yours or allow the new one to overwrite your old one.

I figure if it works then you saved yourself a new install and reconfiguration, if it doesn't, than you wasted a bit of your life and have to reinstall anyways. I think it's a good idea to torrent an iso and upgrade via the iso instead of over the network, repo servers get pretty clogged for about a week.

---

### Post by xclusive585 on 2012-04-22
I do have a ton of manually edited config files for various packages.

Another concern I have is some packages I have running that are not tied into APT, they were manually built or installed by developers install scripts. It's those that I'm kinda concerned about. But as you say, it's probably worth a shot anyways and then if it doesn't work I can do my clean install.

[off topic but, I have a raid10 soft raid volume (non-system, storage only). If I do a fresh install of 12.04, and specify my system partition the same, my raid10 and its chosen mount point should still remain intact, correct?]

---

### Post by CharlesA on 2012-04-22
You might have to edit fstab to mount it by if you are using software RAID, it should be fine.

I've got a few apps running that aren't exactly stock on my 10.04 install and I'm thinking about bumping up to 12.04 because of my hardware. I'll probably do a clean install instead of an upgrade, so I know what I have installed and clean out the stuff I don't use anymore.

---

### Post by xclusive585 on 2012-04-22
I guess I'll be biting the bullet, get my backup machine running the essential services, transfer all my needed data to other network shares, and then re-install on the server with 12.04. I've decided this due to warnings about upgrading systems that use software from non-ubuntu repos, packages like that I have several of, and would like the chance to install some things in a cleaner fashion.

I noticed on my 12.04 test box, the upgrade I did today changed my version from "development branch" to "12.04"... Does this mean 12.04 is done? I heard that happened on the 26th, or is that when the official 12.04 image becomes available?

---

### Post by CharlesA on 2012-04-22
12.04 will be officially released on the 26th but the final freeze was on the 10th.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

---

