---
title: "TOR for Karmic Koala?"
date: 2009-10-31
forum: Security
---

### Post by viking_maniac on 2009-10-31
I noticed that TOR doesn't support Karmic Koala in their repository; at least not yet. Do anyone have any status for the future regarding support for Karmic?

Although, there's actually a way to get TOR to work in Karmic. The only drawback as I can see now, is that you'll get the v0.2.1.19 instead of the very latest v0.2.1.20. I don't know how much difference this will make regarding security, but it does work so far. You just need to replace <DISTRIBUTION> with [COLOR=Red]sid[/COLOR]. Then you'll get the TOR Debian version.
Some info:
[COLOR=Blue]http://www.webupd8.org/2009/10/installing-tor-in-ubuntu-karmic.html
[/COLOR]

---

### Post by viking_maniac on 2009-11-01
I'm just bumping this thread in a hope that someone who missed it might know more about this than I do. This is important to me since I see that most other operating systems are supported by TOR with the latest release, except for Debian and Ubuntu, so I might need to change to OpenSUSE; even though I prefer (K)Ubuntu.

Thanks in advance.

---

### Post by Soul-Sing on 2009-11-01
From source or adding repos.: [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)
or: [https://edge.launchpad.net/~sevenmachines/+archive/tor](https://edge.launchpad.net/~sevenmachines/+archive/tor)

---

### Post by viking_maniac on 2009-11-01
I just got an answer from Peter Palfrader by mail, he who maintains the TOR Debian and Ubuntu packages, after I asked him a couple of questions:

> 
> I'm using Ubuntu 9.10 (Karmic Koala) and can't see any TOR deb-packages for
> Karmic in the [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) repositories.
>
> I'm just wondering if Karmic will be supported in the future.

Eventually I will get around to building packages for karmic.

> By the way, I'm using the Debain-Sid package in Karmic as I write, but I don't
> know if this is a secure solution for us Karmic users?

If they work, why not. Jaunty might have been safer choice.

Cheers,
Peter
So it looks like there will be TOR deb packages for Karmic soon!

As you see, it might be a security issue running the Debian-Sid in Karmic, but as far as I can see, it works.

Thanks to Mr. Palfrader for his quick reply and clarification. :)

---

### Post by e633 on 2009-11-22
I hope so, i am so pissed off about this... TOR is a CRITICAL piece of Open Source software. Not to mention the thread i saw the other day of a poor chinese guy asking for help circumventing the Great Firewall of China cause he couldn't find tor in the repos anymore and without it he colud NOT browse anywhere else useful.

---

