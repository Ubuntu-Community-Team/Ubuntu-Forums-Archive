---
title: "Bug?"
date: 2016-12-30
forum: Ubuntu/Debian BASED
---

### Post by mattonfire on 2016-12-30
This is run on Kali yes, but it is the same troubleshooting as other versions of Linux. I have looked up and found this bug everywhere I have no idea how to fix it, anyone have any ideas here is the screenshot.

[http://imgur.com/a/vp2gF](http://imgur.com/a/vp2gF)
Try and uninstall it won't work, try and install dependencies and it won't work.
It literally won't let the user do anything, please help.

---

### Post by ian-weisser on 2016-12-30
Package conflict, not bug.

You are trying to install two packages, both versions of libc6, that provide the same file.
In Debian/Ubuntu, you cannot do that. Those two packages *conflict*,. and cannot be installed together. You can install either one, but not both together.

Read the error message carefully. It will tell you which package you already have installed, and which conflicting package you are trying to install, and the file that is the bone of contention.

Usually this kind of error occurs when you install third-party packages. The way to fix is to eliminate that third-party source and use the software from within your own distro.
One of the original reasons for the development of distros 20 years ago was to avoid precisely this kind of package conflict headache.

In Debian, eliminating the third-party source and packages means:
1) Disable or delete the source in /etc/apt/sources.list*
2) Since you changed your sources, refresh apt's package database with 'sudo apt update'
3) Uninstall any already-installed packages from that source using dpkg
4) Purge your local package cache to prevent the files from getting re-installed using 'apt clean <packagename>' Or simply nuke the entire local cache using 'apt clean'

---

### Post by mattonfire on 2016-12-30
There were no added sources, only the default sources that is put in when Kali is installed.

---

### Post by ian-weisser on 2016-12-30
I'm not telling you what the cause definitely is, nor how to fix it in Kali.
I can only tell you what the error means, and the most common cause.

Are you intentionally using multiarch? That seems a part of the problem.

---

