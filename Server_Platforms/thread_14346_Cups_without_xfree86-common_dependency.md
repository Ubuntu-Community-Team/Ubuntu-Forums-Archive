---
title: "Cups without xfree86-common dependency?"
date: 2005-02-06
forum: Server Platforms
---

### Post by Appolusionist on 2005-02-06
Hello to all,

I am looking into switching from Gentoo -> Ubuntu and trying to setup another server. I have everything up and running except for Cups. When I try to install cups via 

sudo apt-get install cupsys

The dependencies are also including xfree86-common. Is there an option  where I can leave that dependency off? Thanks for any help on this one.

Rueshann

---

### Post by SNo0py on 2005-05-22
[QUOTE=Appolusionist]Hello to all,

I am looking into switching from Gentoo -> Ubuntu and trying to setup another server. I have everything up and running except for Cups. When I try to install cups via 

sudo apt-get install cupsys

The dependencies are also including xfree86-common. Is there an option  where I can leave that dependency off? Thanks for any help on this one.

Rueshann[/QUOTE]
Same problem here - exactly the same problem... I switched my Desktop from Gentoo to Ubuntu (updates are *much* faster ;) ) and now I also tried to switch my Server from Gentoo to Ubuntu. And the use-flags system from Gentoo is really great and seems to be missing in Ubuntu... there seems to be no way to install the cups-server without xorg-common.

But it does not make sense to install xorg on a server, that does not have a monitor... Developers, is there any solution for this?

Thanks,
SNo0py

---

### Post by LordHunter317 on 2005-05-22
That package isn't an X server or any part of it.  It's some junk init scripts and the like, incredibly tiny and not a problem.

Don't worry about it.  Install cups.

---

### Post by LordHunter317 on 2005-05-22
[QUOTE=SNo0py] And the use-flags system from Gentoo is really great[/quote]Actually it's somewhat crappy and doesn't work with a binary packaging system.   Which would be why it's not in any distribution but Gentoo (and BSD ports where they ripped it from).

---

