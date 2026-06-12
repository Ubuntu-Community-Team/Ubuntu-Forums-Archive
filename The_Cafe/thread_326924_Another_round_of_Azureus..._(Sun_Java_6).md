---
title: "Another round of Azureus... (Sun Java 6)"
date: 2006-12-28
forum: The Cafe
---

### Post by jdong on 2006-12-28
Well, we all know the Azureus saga. With J2SE 1.4, it would wait till you're not looking, then suddenly start eating up all your RAM, and die in the middle of the night doing that important download..

With J2SE 5, the monster has been brought under control RAM-wise, staying below 150MB even with 5 decentralized torrents. However, it was still slow, full of UI lag especially when opening new dialogs.

Around this time, GCC Java came around promising native performance. Well, it didn't deliver. "Natively compiled" Azureus actually started twice as slow as normal Azureus, runs with even more lag than Sun Java, doesn't use less RAM, has had several plugins disabled, requires new plugins to be manually recompiled into a .db native database, not to mention it takes around 500MB of free RAM to compile in the first place. Oh yeah, it spews out random exceptions and tracebacks to the consoles, sometimes leading it to halt all network activity after only a few minutes of running.

Well, J2SE 6 is out now, and I gotta say, congrats to the Java guys at Sun, but running Sun J2SE6 with Eclipse and Azureus, I no longer feel "Java lag". Azureus still stays under its 150MB RSS memory cap, and under 100MB of reported "memory" usage.

Both measures actually aren't terribly accurate, but I limited my system to 128MB RAM and torrented a Ubuntu ISO and some FreeBSD ISO's under XFCE and Azureus, and the system didn't die. I call that an accomplishment.

Perhaps we can all finally splurge on our beloved but bloated tree frog again? ;-)


P.S. For those listing alternative clients we can use (i.e. Deluge, KTorrent), Azureus is the only Linux-capable client other than uTorrent+WINE that supports Peer Exchange, a very important feature if you have to fall back to trackerless/decentralized often.

---

### Post by hanzomon4 on 2006-12-28
How did you install java 6?

---

### Post by jdong on 2006-12-28
I used prevu to build it from feisty. Issue 'prevu sun-java6', assuming that feisty deb-src lines are in your sources.list, or issue 'prevu http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6_6-00-0ubuntu1.dsc' with the latest (0.4.x) version of prevu.

A backport is being investigated at the moment but I'd like to hold off until we see another package revision or two to iron out natural first-package bugs :)

---

### Post by mips on 2006-12-28
In gentoo it would be as simple as emerge -av sun-jre-bin ;)

---

### Post by kripkenstein on 2006-12-28
> **jdong said:**
> 
Azureus is the only Linux-capable client other than uTorrent+WINE that supports Peer Exchange, a very important feature if you have to fall back to trackerless/decentralized often.

True, but note that Azureus uses a different Peer Exchange than utorrent, so the two aren't really comparable. They also use different DHTs.

But since Azureus and utorrent both have such large client bases, either Peer Exchange (/DHT) is good enough (but sad that they don't use the same one).

---

### Post by jdong on 2006-12-28
> **kripkenstein said:**
> True, but note that Azureus uses a different Peer Exchange than utorrent, so the two aren't really comparable. They also use different DHTs.

But since Azureus and utorrent both have such large client bases, either Peer Exchange (/DHT) is good enough (but sad that they don't use the same one).
Right, they are completely incompatible, but in a torrent swarm, you typically see 40% azureus, 40% uTorrent, 10% bitcomet, 10% other anyway, so with PEX+DHT either client only has to locate one other of its compatible buddies and it should come up with a pretty comprehensive peer list.

---

