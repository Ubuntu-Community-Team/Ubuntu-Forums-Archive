---
title: "Using dpkg to maintain multiple /usr trees"
date: 2009-06-28
forum: Server Platforms
---

### Post by nick_d on 2009-06-28
hi,
This isn't technically a question about the server edition, but about servers in general... I want to run diskless workstations of multiple architectures, and I was just turning over in my mind the possibility of trying to use /share as it's meant to be used - ie. for arch independent data.  So if I installed some /share-heavy program like latex for example, and I installed the amd64 version onto the root filesystem, could I somehow get dpkg to grab the i386 packages too, but only install the arch-dependent stuff out of them, into an alternate /usr for the clients that happen to be i386?  Or is this too big an ask... considering that the i386 repository might be a bit out of sync version-wise with the amd64... or might have some arch-specific hacks to get things working that could have affected /share?  I know I'm probably making things difficult for myself... but it would be quite satisfying to get it working... what do others think?
cheers, Nick
PS. I understand I would need a separate /var for each workstation... but what about if dpkg tries to create directories in /var or put stuff there?  Will it?  Or do the programs create their own /var stuff when they run?  Also what about /etc?  Does it prove necessary to have a separate /etc per diskless workstation, to allow customizing for the installed hardware/network setup of each workstation?  If so, then what if dpkg puts things in there, can I tell it to maintain all separate /etc directories?  Is there already some kind of handling for these situations?

---

