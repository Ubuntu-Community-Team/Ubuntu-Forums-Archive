---
title: "Terratec DMX6Fire in Natty"
date: 2011-05-12
forum: Ubuntu Studio
---

### Post by Jay105 on 2011-05-12
Hi Guys  Just picked up a cheap Terratec DMX6Fire off ebay as I saw it was supported under alsa. however i can only get the headphone out on the front panel working. no inputs or anything in ardour or audacity etc and everything on the internet is invariably from 2005 or so and concerns itself with .asoundrc and other scripts that have long since fallen by the wayside.  anything that anyone can offer getting some function out of this would be highly appreciated!

---

### Post by sgx on 2011-05-12
> **Jay105 said:**
> Hi Guys  Just picked up a cheap Terratec DMX6Fire off ebay as I saw it was supported under alsa. however i can only get the headphone out on the front panel working. no inputs or anything in ardour or audacity etc and everything on the internet is invariably from 2005 or so and concerns itself with .asoundrc and other scripts that have long since fallen by the wayside.  anything that anyone can offer getting some function out of this would be highly appreciated!
I think the mixer called envy24control will help, it may be part of the
alsa-tools package, if not available separately in synaptic.

Does  the lsmod  command output include

snd_ice1712 or snd_ice1724  ?

If not, this command:   sudo modprobe snd_ice1712

Using search info based on maudio 24/96 should apply, the same chipset
or very similar one is on the card.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)  visit the links here for
pages with screenshots and directions to connect things in this
qjackctl gui.  Will you be using guitar, keys, mic, all of them?
Cheers

---

