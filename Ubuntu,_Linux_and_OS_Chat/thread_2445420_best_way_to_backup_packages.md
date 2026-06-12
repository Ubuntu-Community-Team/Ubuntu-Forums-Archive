---
title: "best way to backup packages"
date: 2020-06-14
forum: Ubuntu, Linux and OS Chat
---

### Post by mintmag on 2020-06-14
Hi there. I've been trying to write a bash script to backup packages. There's actually a few different methods to do this and I wanted to ask which one you guys think is best for reality and functionality.

There are 3 ways that I am aware of. 

#1 To backup the deb files from the archives directory and use the command ```
dpkg -i *.deb
``` to install them. Though sometimes things can break and not every thing goes in especially if there's been a lot of stuff installed. 

#2 Another method is to use the code  ```
sudo dpkg -iGER 
``` this one is new to me I just found out about it. It seems to be a much better option than just using -i because it can prevent downgrades. 


#3  Finally you can also backup and restore the following
/var/cache/apt/archives
/var/lib/apt/lists
/etc/apt/sources.list.d
/etc/apt/trusted.gpg.d

This will allow you to use the apt to install updates and packages even without internet. You can even use the software center to do it. But you have to remember what it is you've backed up. I'm not aware of anyway to to make apt check the cache for available packages.


Out of these 3 which ones do you think are best. I prefer not to use programs or apps to backup because they can deprecate, also this way gives me more hands on control over the Linux system.

---

### Post by wildmanne39 on 2020-06-14
*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by TheFu on 2020-06-14
i just backup the list of manually installed packages because the actual packages will constantly be updated.  A list is tiny and restoring is just a few minutes.  if the network has an apt-cache-ng caching server, then current packages will be stored their after the first system loads it.

To make a list of manually installed packages, use** apt-mark showmanual**

---

### Post by mintmag on 2020-06-14
> **TheFu said:**
> i just backup the list of manually installed packages because the actual packages will constantly be updated.  A list is tiny and restoring is just a few minutes.  if the network has an apt-cache-ng caching server, then current packages will be stored their after the first system loads it.

To make a list of manually installed packages, use** apt-mark showmanual**

Wouldn't a list like that require the internet to restore the programs?

---

### Post by TheFu on 2020-06-14
> **mintmag said:**
> Wouldn't a list like that require the internet to restore the programs?

Not if you have apt-cache-ng on another system, assuming that other system is on the LAN.  This way the caching of packages is automatic.

But you asked for a solution without stating the real problem to be solved.  We don't backup OSes or easily retrieved packages and haven't for about a decade.  There is probably a good solution to the real problem.

Had an OS disk failure earlier this week.  The replacement HDD arrived yesterday and I&#8217;ll restore it later today.  Just need to figure out which physical disk failed. When there are 12 disks connected to a system, knowing which one failed requires some physical checking to see the S/N or WWN and recognize the missing disk.  Really it is just down to 3 of that brand, but i still need to physically locate those.  While I&#8217;m pulling disks, some reorganization will be likely. Planning to "shuck" a few USB3 8TB disks an put them into an eSATA array for better performance.

---

### Post by mintmag on 2020-06-25
Sorry for the late reply. I'm looking for an easy way to backup that won't require the internet to restore. THe programs you download from the software center.

---

### Post by TheFu on 2020-06-25
> **mintmag said:**
> Sorry for the late reply. I'm looking for an easy way to backup that won't require the internet to restore. THe programs you download from the software center.

apt-cacher-ng is what we use.  It sits between every apt request and keeps local copies of the packages.  I've not attempted to restore anything with the internet down, but all the packages for every system are on in the apt-cache managed by that software. Every week when I patch our systems, only the first system actually causes the internet to download the package. It is placed into the cache and every other system will use that cache to install assuming the systems are all running the same OS, on the same architecture.  Because our system are a little different from each other, about ... let me check the numbers ...```

Transfer statistics
Period                                   Cache efficiency Requests             Data
                                           Hits   Misses      Total         Hits          Misses               Total
2020-06-24 07:58 - 2020-06-25 07:58  98 (75.97%)  31 (24.03%)  129     0.02 MiB (0.21%)    11.14 MiB (99.79%)  11.17 MiB
2020-06-23 07:58 - 2020-06-24 07:58  96 (93.20%)  7 (6.80%)    103     0.02 MiB (2.97%)    0.69 MiB (97.03%)   0.72 MiB
2020-06-22 07:58 - 2020-06-23 07:58  99 (76.74%)  30 (23.26%)  129     0.02 MiB (0.06%)    43.83 MiB (99.94%)  43.86 MiB
2020-06-21 07:58 - 2020-06-22 07:58  98 (81.67%)  22 (18.33%)  120     29.69 MiB (88.32%)  3.92 MiB (11.68%)   33.61 MiB
2020-06-20 07:58 - 2020-06-21 07:58  294 (70.50%) 123 (29.50%) 417     290.66 MiB (60.58%) 189.11 MiB (39.42%) 479.76 MiB
2020-06-19 07:58 - 2020-06-20 07:58  97 (87.39%)  14 (12.61%)  111     0.11 MiB (5.43%)    1.90 MiB (94.57%)   2.01 MiB
2020-06-18 07:58 - 2020-06-19 07:58  96 (94.12%)  6 (5.88%)    102     0.29 MiB (28.69%)   0.71 MiB (71.31%)   1.00 MiB
```
So you can see that on 2020-06-20, I patched the systems. About 500MB was downloaded and about 60% of the data needed for patching was used on more than 1 system.  Most of the systems here run 16.04. We have 1 20.04 box, which uses all new code, always.

That's for .deb packages.

Snaps, flatpaks, AppImages, and manually installed from source stuff isn't part of this solution.  You can come up with a standard idea for those, but snaps have a terrible practice of patching whenever they like, without permission.  AppImages and Flatpaks don't automatically patch, ever, so we have to manually get the new versions for those packages. So much for making our lives easier.  Plus, snaps don't allow anything like a PPA or a local repository.

If you have just one system, then backup the files where they sit and all the files that are connected.  I'm not positive about APT, but probably everything under /var/lib/apt* is needed.

---

### Post by mintmag on 2020-06-26
I think one of the biggest challenges for independent Linux distribution is software management. Like you said there doesn't seem to be a real solution to this.

---

### Post by TheFu on 2020-06-26
> **mintmag said:**
> I think one of the biggest challenges for independent Linux distribution is software management. Like you said there doesn't seem to be a real solution to this.

I disagree. Since the late 1990s, package managers have made Linux software management 1000x safer and 1000x easier than what other platforms do.  APT is freakin' amazing.

There are a few ways for independent software to be distributed.
[LIST]
[*]Create a package file and get a PPA. This works for Debian-based software packages. PPAs are free or you can host your own. RH rpm packages have a similar idea, though the packaging is different. Whatever Arch uses is similar too.
[*]Create a snap package (distro agnostic, in theory); snaps can only be distributed via Canonical's Snap-Store. In theory, this is for security reasons, but there have been a number of failures where a 3rd party created a snap package with crypt-mining malware inside. Canonical didn't catch any of it. Anyone can create a snap package, but for the package to be available, it must have constraints enabled. Snaps that aren't updated by the snap creator become security nightmares. snap updates are pushed and there's no way to stop them.
[*]Create a flatpak (distro agnostic, in theory); I only know a little about these. They don't update without manual effort for each.
[*]Create an AppImage (distro agnostic, in theory); These are closest to the setup.exe method, but prevent commonly used methods to run the programs.
[*]Distribute as source, but with minimal dependencies (good for small/trivial projects only); youtube-dl works well this way. Complex programs like ffmpeg are difficult to distribute this way.
[/LIST]

Each method has problems. 

I'll stay with using trusted repositories and PPAs whenever possible. It works well and I can wrap high-risk programs in firejails with locally controlled directory access choices.

**Package management is one of the main reasons I avoid Windows broken software model.**

Single user systems that aren't on a network bring challenges for all sorts of things. If you absolutely must have everything without any networking available, create a clone using fsarchiver. This will require downtime, unless you install using a volume manager that has snapshot capabilities - LVM or ZFS can be used.

---

### Post by mintmag on 2020-06-27
> **TheFu said:**
> I disagree. Since the late 1990s, package managers have made Linux software management 1000x safer and 1000x easier than what other platforms do.  APT is freakin' amazing.

I thought you were criticizing them. You did say snaps patch without permission which is a bad thing.
> **TheFu said:**
> 
There are a few ways for independent software to be distributed.
[LIST]
[*]Create a package file and get a PPA. This works for Debian-based software packages. PPAs are free or you can host your own. RH rpm packages have a similar idea, though the packaging is different. Whatever Arch uses is similar too.
[*]Create a snap package (distro agnostic, in theory); snaps can only be distributed via Canonical's Snap-Store. In theory, this is for security reasons, but there have been a number of failures where a 3rd party created a snap package with crypt-mining malware inside. Canonical didn't catch any of it. Anyone can create a snap package, but for the package to be available, it must have constraints enabled. Snaps that aren't updated by the snap creator become security nightmares. snap updates are pushed and there's no way to stop them.
[*]Create a flatpak (distro agnostic, in theory); I only know a little about these. They don't update without manual effort for each.
[*]Create an AppImage (distro agnostic, in theory); These are closest to the setup.exe method, but prevent commonly used methods to run the programs.
[*]Distribute as source, but with minimal dependencies (good for small/trivial projects only); youtube-dl works well this way. Complex programs like ffmpeg are difficult to distribute this way.
[/LIST]

Each method has problems. 

This seems to contradict your opening statement about not agreeing. At the very least fall into line with what I said "[COLOR=#000000]*I think one of the biggest challenges for independent Linux distribution is software management.*[/COLOR]" This is what I was talking about. There's a lot of methods but most of them bring along new problems and most distros reject them. It's easy to see why Linux Mint refuses to support snap and appimage is pretty much dead. Apt isn't bad but it's not appropriate for everything.

---

### Post by TheFu on 2020-06-27
> **mintmag said:**
> I thought you were criticizing them. You did say snaps patch without permission which is a bad thing.

Yes, I was.  For my needs, any packages that automatically update is a bad thing. Heck, I don't want to be automatically notified about new or out of date packages either.  But I patch weekly almost always, at a time of my selection.  Make normal end-users don't, but I'd only suggest patching automatically after a month of the package manager NOT being used at all.  And the 'apt' tool should have been modified to handle updates for APT, Snaps, Flatpaks and AppImages already too.

> **mintmag said:**
> This seems to contradict your opening statement about not agreeing. At the very least fall into line with what I said "[COLOR=#000000]*I think one of the biggest challenges for independent Linux distribution is software management.*[/COLOR]" This is what I was talking about. There's a lot of methods but most of them bring along new problems and most distros reject them. It's easy to see why Linux Mint refuses to support snap and appimage is pretty much dead. Apt isn't bad but it's not appropriate for everything.

I can agree that > Apt isn't bad but it's not appropriate for everything.  Linux is about choice, not being forced.  Canonical has been forcing stuff rather than providing the choice to use it.  They forced systemd (and about 10 unwanted systemd-{something} addons). They forced UnityDE. They forced snaps. They forced Wayland. They forced Gnome3.  They forced PulseAudio AND broke it unlike most other Linux distros where Pulse "just works".  
Linux people prefer to have choices.

I think Ubuntu 10.04 was the closest to perfect Ubuntu release. Everything just felt "right." Almost everything worked as expected.  Then Canonical decided to "fix" stuff and broke many things. resolvconf has finally been removed, but it has been replaced by something even worse - systemd-resolved.  Now I have to purge 2 packages, not just 1.  resolv.conf has been used since before there was a Linux.  Of course, the systemd guys decide to misspell it as "resolved" to make things better.  I have to believe they really do want to make things better, regardless of the hundreds of failures.  

Same for the snap dev team. Let me know when snaps work with NFS.

---

