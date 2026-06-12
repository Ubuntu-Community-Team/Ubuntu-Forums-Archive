---
title: "Snap is broken and it needs to be fixed"
date: 2023-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2023-05-06
Hello guys, I and some other people have created bug reports for snap and I think these bug reports need more eyeballs.

[Bug #2017926 "Unused content snaps not autoremoved"]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2017926")
[Bug #2018626 "Unused dependencies not removed when uninstalling a snap program"]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2018626")
[Bug #2018627 "[Feature Rquest] '--no-cache' command to not cache during uninstallation of snaps"]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2018627")

I don't really have a problem with Canonical forcing snap on it's users, but I do have a problem if the snap platform isn't ready and it's being forced on us, and it's not ready based on the problems I experienced. I really want to love and use snaps, but Canonical needs to fix these issues:

1. Uninstalling snaps is a pain in the ass. In apt and flatpak, they have options to auto-remove the software and it's dependencies, but snap doesn't have that, you have to know beforehand what snaps were installed alongside the main snap and one by one uninstall these snaps.

As a test, I've installed KompoZer. Before I installed KompoZer, this is what my snap list output looks like:

```
Name               Version          Rev    Tracking         Publisher   Notes
bare               1.0              5      latest/stable    canonical&#10003;  base
core               16-2.58.3        14946  latest/stable    canonical&#10003;  core
core20             20230404         1879   latest/stable    canonical&#10003;  base
firefox            112.0.2-1        2605   latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-38-2004    0+git.6f39565    140    latest/stable  canonical&#10003;  -
gtk-common-themes  0.1-81-g442e511  1535   latest/stable/&#8230;  canonical&#10003;  -
snapd              2.59.1           18933  latest/stable    canonical&#10003;  snapd
```

After I installed KompoZer, these dependencies were installed: core18 and gtk2-common-themes.

After I uninstalled KompoZer, the dependencies for KompoZer were still listed in `snap list`:

```
Name                Version          Rev    Tracking         Publisher   Notes
bare                1.0              5      latest/stable    canonical&#10003;  base
core                16-2.58.3        14946  latest/stable    canonical&#10003;  core
core18              20230320         2721   latest/stable    canonical&#10003;  base
core20              20230404         1879   latest/stable    canonical&#10003;  base
firefox             112.0.2-1        2605   latest/stable/&#8230;  mozilla&#10003;    -
gnome-3-38-2004     0+git.6f39565    140    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes   0.1-81-g442e511  1535   latest/stable/&#8230;  canonical&#10003;  -
gtk2-common-themes  0.1              13     latest/stable    canonical&#10003;  -
snapd               2.59.1           18933  latest/stable    canonical&#10003;  snapd
```

Snap leaves behind unused dependencies. Snap doesn't have an auto-remove unused dependencies command, you have to remember what dependencies were installed and remove them one by one, which leads me to my second problem.

2. No history.log for snaps. Apt has history.log, which records what dependencies were installed alongside the software, which I use as a reference in uninstalling software and it's dependencies, in snap, you have to do this manually:

```
sudo snap install kompozer && snap tasks --last=install --abs-time >> /home/ardouronerous/.snap_history.log
```

This command will create a log file that will tell me what dependencies were installed alongside KompoZer, so if I want to uninstall KompoZer, I can uninstall it and all it's unused dependencies using this log file as reference.

A log file should be created by default without user intervention.

3. Snap keeps a cache of uninstalled software so you don't have to download the snaps if you decide to reinstall. You could see this as a feature, but if you are low on disk space, this becomes a problem. I wish there was an option not to cache during uninstall.

As noted in this AskUbuntu post: [https://askubuntu.com/questions/1075050/how-to-remove-uninstalled-snaps-from-cache](https://askubuntu.com/questions/1075050/how-to-remove-uninstalled-snaps-from-cache)

Snap keeps a cache of uninstalled software so you don't have to download the snaps if you decide to reinstall. While I can see this as a useful feature, but this becomes an issue if you are low on disk space, to remedy this issue, some users, as noted in the AskUbuntu post, have to run this command in the Terminal to clear the snap cache:

```
sudo sh -c 'rm -rf /var/lib/snapd/cache/*'
```

This cleared about 2GB of space for me. A '--no-cache' command to not cache during uninstallation of a snap should be an option for users who are low on disk space.

---

### Post by exploder on 2023-05-09
Every time the "snap store" has an update I end up having to kill the process to be able to update it. After a year of running 22.04, I switched to Linux Mint. After being out for a year, I should not have problems with snaps on an LTS release.

---

### Post by TenPlus1 on 2023-05-09
Being a beginner distro, Ubuntu should not have these problems in an LTS release at all, which is why I see more and more users leaving for Linux Mint or the more experienced users removing snap altogether.

---

### Post by poorguy on 2023-05-09
> **TenPlus1 said:**
> Being a beginner distro, Ubuntu should not have these problems in an LTS release at all, 


A problem free Linux distro would be nice.

I guess I'm one of the lucky ones using Ubuntu 22.04.2 the default Snaps work without problems OOTB on my 2013 curb find.

---

### Post by monkeybrain20122 on 2023-05-11
The first thing I do after installing Ubuntu is purge snap. Pretty easy to do. I would rather use flatpak.

---

### Post by ajgreeny on 2023-05-11
> **monkeybrain20122 said:**
> The first thing I do after installing Ubuntu is purge snap. Pretty easy to do. I would rather use flatpak.

And I do likewise except that so far I have only a few appimages for some applications, no flatpacks yet, and have found the direct download of firefox .tar.gz from Mozilla to be very reliable but with my own control of when it upgrades. My chromium comes from a PPA which I've been using for the three or more years since it became a snap meaning I have nothing of the snap infrastructure on any of my systems, all of which work faultlessly.

---

### Post by ardouronerous on 2023-05-12
> **monkeybrain20122 said:**
> The first thing I do after installing Ubuntu is purge snap. Pretty easy to do. I would rather use flatpak.

Same, I prefer flatpak over snap.

It's always been a policy of mine to leave default software alone and don't use them, but I kinda want snap to succeed and this is why did those bug reports so that snap improves.

---

