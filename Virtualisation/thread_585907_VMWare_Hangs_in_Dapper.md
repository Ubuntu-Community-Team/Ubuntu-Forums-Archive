---
title: "VMWare Hangs in Dapper"
date: 2007-10-21
forum: Virtualisation
---

### Post by coolboarderguy on 2007-10-21
Hi All,

I get the following when running wmplayer, lastest version, under Dapper.

vmplayer
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

it sometimes just displays a box where I can select the file but it won't let me access the directories with that box. I have to then force it to close. Shall I assume I need to install libpng12.so.0? Why doesn't it do that when I install VMware. I've tried un/reinstall.

EDIT: Ok, I found a post that discusses this issue and I see that Gutsy has the patches for it. Thanx.

[http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html](http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html)

---

