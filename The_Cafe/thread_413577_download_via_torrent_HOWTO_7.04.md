---
title: "download via torrent HOWTO 7.04"
date: 2007-04-19
forum: The Cafe
---

### Post by phi1ip on 2007-04-19
Dum question, does someone here have  a torrent file i can download to get this 7.04?

post a link?

---

### Post by jvc26 on 2007-04-19
You can get the torrent off the main site, someone linked to
[here]("ftp://ftp.tudelft.nl/pub/Linux/releases.ubuntu.com/7.04/") from this post:

> 
SuperMightyMo
If you want it fast you can just download it here:
[ftp://ftp.tudelft.nl/pub/Linux/relea...untu.com/7.04/](ftp://ftp.tudelft.nl/pub/Linux/relea...untu.com/7.04/)


Not sure whether thats the official release or like the beta?
Il

---

### Post by Rydel on 2007-04-19
[http://ftp.osuosl.org/pub/ubuntu-releases/7.04/ubuntu-7.04-desktop-i386.iso.torrent](http://ftp.osuosl.org/pub/ubuntu-releases/7.04/ubuntu-7.04-desktop-i386.iso.torrent)

Currently 619 seeders and 2013 leechers.

---

### Post by starcraft.man on 2007-04-19
[Here]("http://releases.ubuntu.com/7.04/") is the official torrent files (scroll to bottom, download files ending with torrent, at least I think so... Desktop is the main GUI installer, Alternate install is for text, OEM and Server. Have fun.

---

### Post by phi1ip on 2007-04-19
Hello, Is the official torrent files likely to be any different from the one below? I have already started downloading, half way, so do not want to restart.

Is there a way to check the file is identical? or someone know this will be the same? thanks for replies so far.

-------------------------------------------------------------------
Rydel  	[http://ftp.osuosl.org/pub/ubuntu-rel...86.iso.torrent](http://ftp.osuosl.org/pub/ubuntu-rel...86.iso.torrent)

Currently 619 seeders and 2013 leechers.

---

### Post by greybirds on 2007-04-19
> **phi1ip said:**
> Is there a way to check the file is identical? or someone know this will be the same? thanks for replies so far.

You can let the file download completely, then open a terminal and type the following:
```

cd to/where/you/saved/the/iso/file
md5sum nameOfFile.iso

```
It will churn away for a few minutes and spit out a list of numbers and letters. If they match the one next to the version you downloaded in the list below, then they're identical files. (The list below is from Ubuntu's own downloads page).

50f3655fbcbdba9746d4b05ad8705b0b *ubuntu-7.04-alternate-amd64.iso
ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso
a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso
8a1099f5fa8eaf4ee295bf0087c8b03a *ubuntu-7.04-server-amd64.iso
cf462501e2dc1b82b96dfc497a0404a2 *ubuntu-7.04-server-i386.iso
e016f1e3322848af98d01eae2688568c *ubuntu-7.04-server-sparc.iso

Hope this helps.

---

### Post by Pragmatik on 2007-04-19
Thanks for posting those numbers!  Could you put the link to where you got them so we can send it to our friends?

---

### Post by phi1ip on 2007-04-19
the source of the above numbers

[http://releases.ubuntu.com/7.04/MD5SUMS](http://releases.ubuntu.com/7.04/MD5SUMS)

i found the numbers did not know what to do with them. thanks greybirds!

---

### Post by Pragmatik on 2007-04-19
Many thanks!

---

