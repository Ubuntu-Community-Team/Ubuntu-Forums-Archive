---
title: "IBM, Linux and Printing"
date: 2007-09-20
forum: Server Platforms
---

### Post by Sunforge on 2007-09-20
I'm posting in the servers forum because this may be something that another admin has wrestled with. I did post a while ago in the Red Hat forum to see if anyone in there had any ideas but didn't come up with much.

I'm testing IBM 5250 emulation under Ubuntu. I'm trying to see whether it is possible to roll out Linux workstations in parts of our organisation for basic terminal access and printing. There are a ton of options to solve this problem (dumb terminals, hardware emulators, tin of baked beans and string) which I am also looking at.

There are two parts to any solution: client session & print and server printing.

So far I can see two options for the client side:

1. AS/400's come with a licence for IBM 5250 Client Access which is their proprietary programme.
2. tn5250 which is free in the repos.

Of the two IBM's version is more user friendly, although both achieve the same end, which is accessing an AS/400.

I can reliably install either tn5250 (from repos) or IBM Client Access (via RPM/Alien) using the following "how to" for the IBM programme:
[http://ubuntuforums.org/showthread.php?t=368894](http://ubuntuforums.org/showthread.php?t=368894)

I can set either of the above up so that I can screen print which is something end users do all day long when printing orders etc.

Now on the server side it's useful to maintain printer emulation, so that an AS/400 can print to bog standard HP printers without getting into the expense of IPDS cards or other hardware emulation devices. I've found a programme in the repos called lp5250 which handles basic printing quite well, but it chokes on more complex prints involving forms overlays.

Has anyone come up with any clever ideas for transforming AS/400 output to PDF via a linux box? If you have I'd love to hear from you as I'm a little stumped on this at the moment.

---

### Post by Sunforge on 2007-09-20
bump...?

---

