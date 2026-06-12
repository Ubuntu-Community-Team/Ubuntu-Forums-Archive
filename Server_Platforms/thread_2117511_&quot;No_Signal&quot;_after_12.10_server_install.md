---
title: "&quot;No Signal&quot; after 12.10 server install"
date: 2013-02-18
forum: Server Platforms
---

### Post by bobmanuk on 2013-02-18
Hi all,

I have recently been asked to setup a server for various games for a lan party that i will be attending in the next few months, the machine i have to use is an old shuttle machine, not 100% on the specs but its a Pentium based CPU, approx 2.4GHz, 2GB ram, 80GB ide hdd.

I installed ubuntu fine and it manages to reboot ok, but it gets to grub screen and then goes blank with the usual "no signal" or "out of range" errors synonymous with people using nvidia or ati graphics.

Im not using either, iirc the graphics chip is a sis one, I booted with the server disk again and set /etc/default/grub file to have nomodeset, this hasnt helped. I cant even force a grub prompt by holding shift, same blank screen appears.

I have scoured so much of the internet and all of the pages i find seem to relate to the above and im out of ideas.

I mean its not like i need to run a gui, I wouldnt mind the lack of display if i could ssh onto the box, but it wont pick up an IP address and i need some sort of display to configure the address if it cant get one via DHCP.... 

ive never ever wanted to throw a box out of the window so badly, so please, if you have any ideas, please let me know.

Cheers

EDIT - ok so it was still grub that wasnt behaving nicely, after leaving it on for a while it obviously auto chose an option, i have since edited the grub config to not wait for an option, it now boots straight into linux... albeit freezing at waiting for network configuration :(

---

### Post by wildmanne39 on 2013-02-19
*Thread moved to **Server Platforms**.*

---

