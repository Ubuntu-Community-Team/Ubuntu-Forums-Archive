---
title: "Shuttlesworth on DCCA - a detailed statement"
date: 2006-01-05
forum: The Cafe
---

### Post by matthew on 2006-01-05
from [http://lists.ubuntu.com/archives/sounder/2006-January/003630.html](http://lists.ubuntu.com/archives/sounder/2006-January/003630.html)

I don't like to discourage people from pursuing their ideas just because
I don't "get" them. I've been wrong often enough. So in the early days
of the DCC I preferred to let the proponents do their thing and then see
how it all worked out in the end. Now we are pretty close to the end :-)

So I'll answer this in more detail now. I do hope this doesn't turn into
a flamefest. This is simply my view on what will work, and what won't.

1. The Name. From the very outset I thought the "Debian Common Core
Alliance" name was going to be a problem, and it has been. The DCC folks
don't have the right to use the Debian name, and have been told that
very publicly. Their was an attempt to pretend that "DCC stands for DCC
Common Core" but that's pretty much nonsense, even DCC members continue
to refer to it as "Debian Common Core", a name that it cannot legally use.

2. The Commonness. The DCC distro doesn't use the Debian kernel, and it
modifies key pieces of the infrastructure like the linking system and
core system libraries. So it's not really Debian at heart. There is now
discussion of modifying many, many more packages, for example to use the
Ubuntu X.org packages rather than the Sarge XFree86 packages.

3. The Style. The DCC distro is really aimed at shoehorning an
LSB-compatible environment on top of Sarge. I think if LSB was a goal
for Sarge then that could have been achieved directly in Sarge, not in
this hybrid fashion. If we were to do LSB for Ubuntu, it would be done
directly rather than as a compatibility layer.

4. The Premise. The vision behind DCC, which is indeed compelling, is
that it would provide a common platform for certification, and that the
distros that make up the DCC would all ship exactly that same core. But
it strikes me that this approach has never worked in the past. In fact,
every distro ALWAYS modifies elements of the core, and with good reason.
And while we would love that not to be the case, the truth is that the
reasons to specialise outweigh the benefits of homogeneity. Much as it
may be compelling, the common core idea is ultimately flawed, because
it's not just the bits at the core that matter. An ISV that certifies an
OS is not just certifying the pieces on which it's app depends. It's
also certifying the *environment* which it will support, which includes
installer, documentation, even packaging. Screenshots, for example,
won't be useful unless they reflect all of the certified OS's, and
that's not possible in the DCC model. There have been several examples
of places where this idea has failed. United Linux is one.

Now, that said, it's great that Debian-derived commercial distros have a
forum and a mailing list on which to discuss problems they run into, and
I think the DCC project has served as a good touch point for bringing
some of these hidden issues to the fore. So I'm in no way opposed to the
DCC or its members, and in fact there are some neat places where we are
collaborating with the DCC on source code, which is where I think the
collaboration works best. The DCC kernel and Ubuntu kernel will be very
similar if not identical in future DCC releases, and I expect that
collaboration will spread to other parts of the system such as X, ACPI etc.

The essential driver of free software is collaboration to achieve common
goals. And that works best at the source code level. Inasmuch as the DCC
has promoted better collaboration between its members, it's a success.

Mark

---

### Post by kairu0 on 2006-01-05
I agree with that in that bundling the same core with multiple distributions is a virtual impossibility. I mean, in a distribution as young as Ubuntu, what gets changed more? Already, radical changes are taking place in the Breezy -> Dapper evolution. If Breezy were built on a universal Debian core, then most of its congruency with it would already be gone in Dapper. And this is just one distribution! Imagine how development would cease to develop if Debian, Ubuntu, Mepis, etc., etc. were all crippled by such a ball-and-chain whenever they wanted to move on to a new, innovative strategy for their respective audiences.

---

### Post by 23meg on 2006-01-05
I'm 100% behind Ubuntu's attitude to disregard binary compatibility and participation in the DCCA and focus on collaboration on a source level instead. I feel a need to stress the "source" in "open source" when people whine about binary incompatibility.

---

### Post by kairu0 on 2006-01-05
I compile everything that doesn't come in Ubuntu repos and I wouldn't want it any other way.

---

### Post by poofyhairguy on 2006-01-05
Its kinda funny- Mark didn't want to comment on the DCCA until it was seen as less relevent but by not commenting ( or more so not commiting) he was partially responsible for its marginalization.

Not that I blame him- the guy behind it is VERY anti-Ubuntu and compliance would have cost Mark a lot of money.

---

### Post by gasparov on 2006-01-06
[QUOTE=poofyhairguy]
Not that I blame him- the guy behind it is VERY anti-Ubuntu and compliance would have cost Mark a lot of money.[/QUOTE]

Are you talking about Murdock, the founder of Debian?

---

### Post by newbie2 on 2006-01-06
here are some other articles about it -->
[http://www.linux-watch.com/news/NS8432548714.html](http://www.linux-watch.com/news/NS8432548714.html)
[http://www.eweek.com/article2/0,1895,1908680,00.asp](http://www.eweek.com/article2/0,1895,1908680,00.asp)

---

### Post by 23meg on 2006-01-06
He also talks about DCCA and Debian binary compatibility (lack thereof) on his wikipage, in case anyone missed that:

[https://wiki.ubuntu.com/MarkShuttleworth](https://wiki.ubuntu.com/MarkShuttleworth)

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=gasparov]Are you talking about Murdock, the founder of Debian?[/QUOTE]



Yeah...search for his name on the forum to discover our previous problems with his attitude (he likes to spread FUD about Ubuntu).

---

