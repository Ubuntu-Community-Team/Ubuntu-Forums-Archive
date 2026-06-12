---
title: "Custom Live CD Toolkit?"
date: 2005-09-23
forum: The Cafe
---

### Post by jimcooncat on 2005-09-23
I've just purchased a couple USB Hard drives for my business for backups. I'd like to have a Live CD that will:


[list]
[*]Detect hardware, at least the USB Hard drive and network card. Preferably lots of network card drivers on it.
[*]Boot with LVM support
[*]Get network address with DHCP
[*]Automount the drive using LVM and Reiserfs
[*]Start up an SSH Server with my public keys in place
[*]Start up an rsync daemon, and perhaps monit
[*]Maybe a few more tools, but not a lot else. Small is good.
[/list] 

In other words, I'd like to just take any old box hanging around, plug the hard drive and network into it, boot with the CD and log into it from another workstation. Minimal feedback is fine -- would be good to have "Eth0 working, IP address is 192.168.1.56" type messages -- no GUI.

Any suggestions for a polished toolkit for me to build my own?

---

