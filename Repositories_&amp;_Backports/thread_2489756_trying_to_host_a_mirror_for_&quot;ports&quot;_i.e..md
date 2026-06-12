---
title: "trying to host a mirror for &quot;ports&quot; i.e. arm64 but no rsync upstream mirrors availabl"
date: 2023-08-09
forum: Repositories &amp; Backports
---

### Post by roberto-riedl on 2023-08-09
none of the ones listed here with "(ports)" [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) allow rsync access and even the official one "ports.ubuntu.com" gives me "permission denied" :|

Does anyone know of a public rsync mirror for arm64 ?

Or how to contact the mirror team behind ports.ubuntu.com ?

---

### Post by TheFu on 2023-08-09
Consider [https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror) instead.

I've been using apt-cacher-ng for about a decade. About once every 5 yrs, I have to do something with it. The rest of the time, it just works.

Nobody here works for Canonical.  Generally, the best way to contact them is via IRC or Discord, but I won't use discord and when IRC moved, I didn't reconfigure my IRC bouncer. It was easier to just shut down that process.  IRC was usually a good place, IME.

---

### Post by roberto-riedl on 2023-08-10
thank you @TheFu

actually we just moved away from debmirror because its a huge strain on infrastructure to use it - we have been using a modified version of this script here [https://github.com/rocky-linux/rocky-tools/blob/main/mirror/mirrorsync.sh](https://github.com/rocky-linux/rocky-tools/blob/main/mirror/mirrorsync.sh) - which already works fine for the amd64/i386 or DVD/iso releases of ubuntu (and loads of other distributions) - but for some strange reason, ubuntu doesn't ship their arm64 binaries via their main mirror like i.e. Debian does.

So I need a different upstream mirror  in order to have the same setup for each mirror.

I'll try discord or IRC then

Edit: i couldn't find a discord and IRC says contact by mail via [email]mirrors@ubuntu.com[/email], so I did that

---

