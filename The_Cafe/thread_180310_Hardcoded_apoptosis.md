---
title: "Hardcoded apoptosis?"
date: 2006-05-22
forum: The Cafe
---

### Post by glotz on 2006-05-22
What do you think, should Ubuntu come with "hardcoded selfdestruct date"? Does it allready? I mean, does the version on the installation disk allready know, when it'll be obsolete? It should IMHO. And it should notify the user of the state of things. Also, the installer should know it. As in [http://www.ubuntu.com/news/410eol](http://www.ubuntu.com/news/410eol)

This thread is inspired by someone who just asked for instructions to install *Warty*! ](*,)

---

### Post by K.Mandla on 2006-05-22
Well, no, because I can see a situation where one version might work better, depending on the hardware. I tried to install Warty about two months ago on an ancient laptop, and while it wasn't successful, it wouldn't have been any help whatsoever if it had refused to install outright.

Or perhaps I misunderstand what you're suggesting, in which case please correct me. :)

---

### Post by halfvolle melk on 2006-05-22
I had to look op apoptosis. Then I had to look up metazoans. From there the number of things I had to look up seem to increase exponentially.

Anyway, there's allready a self destruct mechanism in place.
[http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)
In 32 years 32-bit unix computers will explode and fire and brimstone will rain down upon man kind.

---

### Post by drogoh on 2006-05-22
[QUOTE=glotz]What do you think, should Ubuntu come with "hardcoded selfdestruct date"?
[/quote]
No way, bad idea.  It shouldn't decide that you don't want something because it's "too old".  Bad for compatibility with older hardware.
> Does it allready? I mean, does the version on the installation disk allready know, when it'll be obsolete?

Probably not, the developers that deal with the installer would be able to answer this though.
> It should IMHO. And it should notify the user of the state of things. Also, the installer should know it. As in [http://www.ubuntu.com/news/410eol](http://www.ubuntu.com/news/410eol)

The installer should, but it should still let the user stick their finger in the light socket if they want, just let them know the potential risks and do it with a big neon sign and marching band if possible.

---

### Post by BoyOfDestiny on 2006-05-22
[QUOTE=halfvolle melk]I had to look op apoptosis. Then I had to look up metazoans. From there the number of things I had to look up seem to increase exponentially.

Anyway, there's allready a self destruct mechanism in place.
[http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)
In 32 years 32-bit unix computers will explode and fire and brimstone will rain down upon man kind.[/QUOTE]

Sweet, the joys of running 64-bit.

"Using a 64-bit value introduces a new wrap around date in about 290 billion years, on Sunday, December 4, 292,277,026,596 15:30:08 UTC. This problem is not, however, widely regarded as a pressing issue."

Anyway, what of those on warty 64? ;)

It should be a user's choice. To be honest, even if it's hooked to the net, the default install wouldn't have have daemons listening on open ports... For things that listen, they'd better be ready to patch it themselves :P

---

### Post by Parkotron on 2006-05-22
I think this is a good idea, but the information should be provided in a very friendly, easily dismissable manner. The installer should compare the system date to the release date of the installer, and if they differ by more than more than 6 months, give inform the user that

```
Newer version may be available
-------------------------------------------------------------

This release of Ubuntu is more than 6 months old. There is 
most likely a newer release available. For more information 
see www.ubuntulinux.org.


         [Cancel installation]               [Continue]


```

I agree that trying to check for newer versions via the Internet is a bad idea and only likely to complicate things unnecessarily.

Of course this issue gets more complicated when you consider the LTS (Long Term Support) releases like Dapper, which some users are very likely to want to install, rather than the latest but possibly less stable release. Maybe the LTS releases should wait 2 years before giving the warning.

---

### Post by BoyOfDestiny on 2006-05-22
[QUOTE=Parkotron]I think this is a good idea, but the information should be provided in a very friendly, easily dismissable manner. The installer should compare the system date to the release date of the installer, and if they differ by more than more than 6 months, give inform the user that

```
Newer version may be available
-------------------------------------------------------------

This release of Ubuntu is more than 6 months old. There is 
most likely a newer release available. For more information 
see www.ubuntulinux.org.


         [Cancel installation]               [Continue]


```

I agree that trying to check for newer versions via the Internet is a bad idea and only likely to complicate things unnecessarily.

Of course this issue gets more complicated when you consider the LTS (Long Term Support) releases like Dapper, which some users are very likely to want to install, rather than the latest but possibly less stable release. Maybe the LTS releases should wait 2 years before giving the warning.[/QUOTE]

AFAIK The new update manager handles upgrades to the next version of a distro... I assume a little notification will say, edgy eft ubuntu 6.10 is available, would you like to upgrade? Or something along those lines...

As for the 6 month thing, that isn't the support life, that's the release cycle...

---

### Post by curuxz on 2006-05-22
I have to say I think this is the worst idea EVER....I don't mean to sound harsh but to hard code a self destruct would be terrible, I mean what happens if the world ends and you are the last person left on earth, you spend months building a wind turbine, fighting off rabid dogs etc.....finally finally you get power so you decide to power up your laptop and BAMB..nope sorry wont work because the version is out of date, and neither will your other versions of Ubuntu. Im sorry if im the only one who thinks the idea of an apocalypse using windows is one not worth surviving...

---

