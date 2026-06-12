---
title: "Slow local network transfer speeds"
date: 2011-02-24
forum: The Cafe
---

### Post by kahlil88 on 2011-02-24
I've just started learning and experimenting with SSH, mostly so I can transfer files between my laptop and desktop on a local network. My router is a Linksys WRT54G which should max out at 54Mb/s (~6MB/s) if numbers don't deceive, however my transfers are maxing at 1.1 MB/s.

---

### Post by ssam on 2011-02-24
54Mb/s of wireless is a maximum under ideal conditions.

SSH does strong encryption, so it is also limited by CPU speed. you may find that using blowfish encryption (weaker, but faster) helps. also are you doing the transfer with nautilus, or the command line? i think nautilus can slow it down.

---

### Post by kahlil88 on 2011-02-24
> **ssam said:**
> 54Mb/s of wireless is a maximum under ideal conditions.

SSH does strong encryption, so it is also limited by CPU speed. you may find that using blowfish encryption (weaker, but faster) helps. also are you doing the transfer with nautilus, or the command line? i think nautilus can slow it down.

Wasn't sure how to transfer files between computers via command line so I've just been using Nautilus. I have noticed that copying data to flash drives with Nautilus seems slower than command line but I'm curious how it makes any difference.

---

