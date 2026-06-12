---
title: "Novell Strips BitTorrent DHT Technology from openSUSE"
date: 2009-11-22
forum: The Cafe
---

### Post by lovinglinux on 2009-11-22
[http://torrentfreak.com](http://torrentfreak.com/novell-strips-bittorrent-dht-technology-from-opensuse-091122/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Torrentfreak+%28Torrentfreak%29)

> Sponsored by Novell, openSUSE is a free and Open Source operating system, based on Linux. Following in the footsteps of Ubuntu, OpenSUSE recently decided to include Transmission as the default BitTorrent client.

However, the addition of Transmission to openSUSE was not straightforward. Since Transmission comes with DHT support – a technology that helps BitTorrent users to find peers – Novell thought that the application could possibly make openSUSE liable for copyright infringement under German law.

I don't see how removing DHT would help to avoid copyright infringement. This is kind of scary and a silly move. What else they will remove next, Firefox download manager?

---

### Post by FuturePilot on 2009-11-22
This has been the case since 2006. Why is everyone just picking up on this now?

[https://bugzilla.novell.com/show_bug.cgi?id=205390]("https://bugzilla.novell.com/show_bug.cgi?id=205390")

---

### Post by Mornedhel on 2009-11-22
Possibly because The Pirate Bay is now distributing torrents mainly through DHT.

---

### Post by mivo on 2009-11-22
> **FuturePilot said:**
> This has been the case since 2006. Why is everyone just picking up on this now?

Because The Pirate Bay permanently turned off their tracker a few days ago and people are going to use "magnetic links", and that requires DHT. 

Transmission isn't the only torrent client out there.

---

### Post by FuturePilot on 2009-11-22
> **Mornedhel said:**
> Possibly because The Pirate Bay is now distributing torrents mainly through DHT.

Oh, right. Didn't put 2 and 2 together. :P

> **mivo said:**
>  

Transmission isn't the only torrent client out there.

What does Transmission have to do with anything? I hate Transmission anyway.

---

### Post by SunnyRabbiera on 2009-11-22
I too dislike transmission so I always install other BT clients anyhow.
Dont bother me.

---

### Post by Giant Speck on 2009-11-22
> **FuturePilot said:**
> What does Transmission have to do with anything? I hate Transmission anyway.

Deluge > Transmission

---

### Post by FuturePilot on 2009-11-22
> **Giant Speck said:**
> Deluge > Transmission

This is true.

---

### Post by samh785 on 2009-11-22
They should have just used a disclaimer for German downloaders.

---

### Post by gnomeuser on 2009-11-22
> **mivo said:**
> Because The Pirate Bay permanently turned off their tracker a few days ago and people are going to use "magnetic links", and that requires DHT. 

Transmission isn't the only torrent client out there.

Actually it is not:

[https://bugzilla.redhat.com/show_bug.cgi?id=492297](https://bugzilla.redhat.com/show_bug.cgi?id=492297)

As you will note this specific instance of DHT disabling predates the Pirate Bay switch. SuSE has traditionally not shipped any "real" p2p technology such as DHT, I am unaware of the exact legal reason but it has been the case for years.

---

### Post by mivo on 2009-11-22
> **gnomeuser said:**
> [https://bugzilla.redhat.com/show_bug.cgi?id=492297](https://bugzilla.redhat.com/show_bug.cgi?id=492297)

Does this have an effect on a user self-compiling a client or getting a package from a different repository?

---

### Post by samh785 on 2009-11-22
from the same article:
> After discussion with Novell’s German lawyer, it was agreed to include Transmission with DHT in future releases, but with an added popup informing users that they should only use the BitTorrent client for legal transfers. This means that the next openSUSE release will include a fully-functional BitTorrent client.
Nothing to see here folks. 

Though the pop-up would indeed be annoying.

---

