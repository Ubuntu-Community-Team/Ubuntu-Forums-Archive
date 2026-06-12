---
title: "Mono 1.2.6"
date: 2007-12-18
forum: Repositories &amp; Backports
---

### Post by safknw on 2007-12-18
I'm using Kubuntu 7.10, which has mono 1.2.4.

Is there any repo which provide latest Mono packages?

---

### Post by charlesew on 2007-12-30
Hi there, I can't tell you if there is repo for latest mono however you can get the latest mono using the "all other distros" download from the mono site heres what I did.

[LIST=1]
[*]Make sure that mono isn't installed (use package manager).
[*]Download "Linux Installer for x86" from "http://www.mono-project.com/Downloads"
[*]Install it!
[*]Edit monodevelop file.
[LIST=a]
[*]Open "~/mono-1.2.6/bin/monodevelop" (assumes you just installed mono in your home directory)
[*]Replace line 55 with "MD_BIN_PATH=~/mono-1.2.6/lib/monodevelop/bin"
[*]rename all absolute references to relitive references (ie /usr/bin/mono to mono)
[/LIST]
[*]rename ~/mono-1.2.6/lib/libz.so.1 to libz.so.1.bak and ~/mono-1.2.6/lib/libz.so.1.2.1 to libz.so.1.2.1.bak.
[/LIST]

Note: That I used version 1.2.6_6 and that some of these problems could be fixed in future releases, also note that while monodevelop works for me there could be bugs in other programs that I haven't tried, but like the bugs I found with monodevelop are probably related to inconsistent library versions and absolute name problems (usually fairly easy to fix). Also note that I'm not using Kubuntu so you might have to install some gnome based libraries to but I'll leave that up to you (or others) to sort out.

---

