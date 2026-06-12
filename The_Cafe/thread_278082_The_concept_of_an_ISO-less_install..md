---
title: "The concept of an ISO-less install."
date: 2006-10-15
forum: The Cafe
---

### Post by raublekick on 2006-10-15
I was thinking about all the ISO discs I burn, and how little use they actually get. My Dapper disc has gotten the most use, and that's only a few installs. Sometimes I try live discs, and they don't get past the splash screens, so they end up just collecting dust and wasted. 

So, I was thinking about the possibility of ISO-less installs. Well, not completely ISO-less. It would be kinda like a reusable net install. The idea is that the Ubuntu developers (or any other distro for that matter, if they can tailor this to their packaging system) could make a base ISO that contains little more than a kernel, apt, a text editor, and a working live terminal environment.

Lets say they build this base around Dapper. That doesn't mean that it would be useless come Edgy. Since this isn't a full live desktop, it wouldn't be *too* hard to update everything in a live environent. The kernel would be, but I don't even know if it would be necessary. Basically you could update the sources.list to Edgy and then run an installer much like the alternate ISO. You would still be able to partition any everything if you want, but it would then use apt to install the packages you need. 

The key would be a consistent maintainence of packages like ubuntu-base (like a server install), ubuntu-desktop, kubuntu-desktop, and so on, from release to release. As long as there are only a few metapackages that cover a large base, this ISO could be reused over and over from release to release, because the only thing that changes is what the metapackages install. 




Is this something that anyone would find useful? Is it possible? Questions? Concerns? Am I just a nut?

---

### Post by Kateikyoushi on 2006-10-15
Gentoo has a minimal installation cd.

> The Gentoo Minimal Installation CD, a small, no-nonsense, bootable CD which sole purpose is to boot the system, prepare the networking and continue with the Gentoo installation.

I use rewriteable discs for OS isos.

---

### Post by PriceChild on 2006-10-15
Yeah... i used a Debian teeny one this morning (40Mb) but i think that was just for one distro, e.g. Sarge.

Things just change too much between distros to be able to upgrade really.

---

### Post by Old Pink on 2006-10-15
Invest in an CD-RW/DVD-RW.

Multi use/Format-able blank discs. ;)

---

### Post by raublekick on 2006-10-15
> **PriceChild said:**
> Yeah... i used a Debian teeny one this morning (40Mb) but i think that was just for one distro, e.g. Sarge.

Things just change too much between distros to be able to upgrade really.

I think if this was set up so that you edit the sources.list, and then the installer updates itself at the very beginning and restarts, it might work very nicely. 

I don't think things really change all that drastically to make this an impossibility for something like Ubuntu. The sources.list has remained the same throughout the releases with only the release name changing, and ubuntu-desktop has consistantly installed, well, the Ubuntu desktop environmet. Even the file system has remained consistant enough.

---

### Post by John.Michael.Kane on 2006-10-15
Remember rewriteable discs have a set number of re-write's before they begin to fail. 

I would only use re-write disk's to test the OS. Once you have made your choice on an OS use a non re-write disk.


As to the OP question about a net-install cd that does sound like a neat idea,however. Arent these kind of iso's based on endusers having high speed net access to down load the packages since they would not be on the cd?

---

### Post by Kateikyoushi on 2006-10-15
Yes it requires a high speed net otherwise the installation can grow quite long.
The good point these minimal isos decrease the load on the servers.

You download an edgy cd and after the install start a massive update replacing the packages you just downloaded.

I see no reason why should burn the rewriteable to a non rewriteable disc after tried it and installed from it. 
The number of remaining rewrites do not decrease while i store the current release on it.

---

### Post by John.Michael.Kane on 2006-10-15
decrease the load on the servers how so?

Enduser still needs to download xyz packages from the same or some other server.

net-installs are good for corp installs not a homeuser who may mess up his/her install,and need to reinstall thus still having to put load on the server/s.

Unless of course you are offering to be every net install users personal IT go to guy.

---

### Post by alexfittyfives on 2006-10-15
I think this thread on installing without a cd may interest you:

[http://ubuntuforums.org/showthread.php?t=28948]("http://ubuntuforums.org/showthread.php?t=28948")

---

### Post by Kateikyoushi on 2006-10-15
Um right, end users might mess up the install, I did not consider it.
But they can break it with the full cd as well and redownload the updates again so seems it's pretty much the same to me.

Corps could use the same iso to install it on every machine instead of downloading the same packages hundred times.

---

### Post by raublekick on 2006-10-15
please note: i mentioned the alternate installer CD for a reason: this was not suggested to be a replacement of the suggested means of installing Ubuntu, or even a replacement of the alternate installer, and especially not something for beginners. I think it's just something that some people would find useful, and something that sounds cool.

Kateikyoushi brings up a point that I failed to think of: your install will always be up to date right after an install. Right now if you install Dapper off the 6.06 ISO, you will have lots of updates to do, so basically you are installing the packages, and then immediately updating them. Here, you would just be installing the most up to date packages from the start.

So, instead of downloading a 700MB ISO, installing ~1GB worth of data to your hard drive, and then downloading, let's say ~300MB worth of updates, decompressing them, and then installing them, you would simply download all the packages contained in ubuntu-base and ubuntu-desktop and be up to date. Certainly seems much easier on your computer, and arguably for the servers as well.

I would very much like to see a simple net install ISO for Ubuntu, but something that is adaptable from release to release would be amazing to me, and it's something I've never seen in a Debian / apt environment.

---

