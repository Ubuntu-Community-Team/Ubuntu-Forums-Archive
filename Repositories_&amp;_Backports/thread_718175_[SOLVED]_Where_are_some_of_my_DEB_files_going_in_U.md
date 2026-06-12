---
title: "[SOLVED] Where are some of my DEB files going in Ubuntu 64-bit???"
date: 2008-03-07
forum: Repositories &amp; Backports
---

### Post by OzzyFrank on 2008-03-07
OK, this is something I haven't encountered before: missing .deb files for programs I have installed. On my 32-bit 7.10 machine, I had created a repository folder within my home folder, and so was used to the installers either ending up in there or the usual /var/cache/apt/archives.

In the past week I've built my new Quad-core machine and so went with a fresh install of 7.10 amd64, and just let everything end up in the official folder this time around. However, I've noticed something very strange indeed, being that some programs like Filezilla and even Frozen Bubble don't seem to have .deb files anywhere! They are installed properly, and even using Catfish ( a superior search tool) cannot locate them. The installed folders and files are all where they should be, but the cache doesn't have copies of the installer.

Don't know if there is a way to turn off caching/keeping local versions of the installers, so can assure you if there is a way, I don't know about it, and hence haven't done so. And I can verify that other programs I've installed in the last few minutes end up in /var/cache/apt/archives as they should... so what the hell is going on??

Would appreciate an answer to this, as I back up installers and also pass them on to others, so need to know where these missing ones have gotten to. Cheers

---

### Post by OzzyFrank on 2008-03-15
No one knows this? Seriously?

---

### Post by bruce89 on 2008-03-15
[LIST]
[*]Packages that are downloaded from repositories are held in /var/cache/apt/archives.
[*]These packages' contents are then uncompressed into the filesystem.
[*]The cached archive files are deleted every so often automatically.
[/LIST]

Debian packages (debs) are archives with data files, scripts and information files. The packages' data is put on the filesystem and the scripts are run to do a bit of maintaining.

Therefore, a program may be installed, but the archive doesn't exist any more.

---

### Post by OzzyFrank on 2008-03-16
Hi, and thanks for your reply. As I mentioned, I know where the packages go, but couldn't figure out where the missing ones were. Seems that with my reinstall the default in Synaptic was to have packages that are no longer available to be deleted. Back in the day when I first started using Ubuntu, either this was not the default, or I figured it out and changed it. I was looking around in Software Sources etc for an option and didn't find it, then realised it was probably in Synaptic's preferences (while it is the default package manager, it is after just one of the few available, so thought the answer lay elsewhere in my system menu).

Anyway, that is one stupid default setting, if I may say! I mean, yeah, the package is no longer available... so wouldn't that be more reason I may want to hold onto it for a future reinstall (of that program or the whole system) or something, hehe??

---

