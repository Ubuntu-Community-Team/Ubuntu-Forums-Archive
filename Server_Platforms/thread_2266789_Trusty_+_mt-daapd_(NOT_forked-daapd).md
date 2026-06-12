---
title: "Trusty + mt-daapd (NOT forked-daapd) ?"
date: 2015-02-25
forum: Server Platforms
---

### Post by MrEgg on 2015-02-25
Hi all,

Does anyone know if there's a way to install mt-daapd ([http://sourceforge.net/projects/mt-daapd/](http://sourceforge.net/projects/mt-daapd/)) on Trusty? This project has been replaced in the repos by forked-daapd, which is really half-baked imho.

My main concern with with forked-daapd is that it cannot read mp3 which contain embedded artwork:
> [https://github.com/jasonmc/forked-daapd](https://github.com/jasonmc/forked-daapd):
Embedded artwork is not supported; libav (ffmpeg) doesn't support this yet, if
and when this is added to libav, forked-daapd will support it.

This, however, works perfectly with mt-daapd on my old lucid server (which I need to retire). Anyone facing the same issue? Any idea around it?

EDIT:

Maybe is it time for me to move on to a new project? Any suggestion as to what I should replace mt-daapd with? I want to be able to connect to my server from rhythmbox, Android, and (possibly) an iPhone.

Thanks,
Egg

---

### Post by diapente2 on 2015-03-06
I have installed mt-daapd packages from Lucid Lynx on Trusty Tahr on numerous machines.

They have proven to be rock solid on Trusty and Precise machines that I have.

You may find the instructions on the 'HOW-TO' section on this link [www.diapente.net]("http://www.diapente.net")

Also, latest Fedore Core still has mt-daapd packages, if you don't mind changing distros. [rpmfind.net]("http://rpmfind.net//linux/RPM/fedora/21/x86_64/m/mt-daapd-0.2.4.2-18.fc21.x86_64.html")

---

