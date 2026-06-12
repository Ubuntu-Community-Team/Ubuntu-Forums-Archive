---
title: "Lucid Lynx slow throughput to Windows machines"
date: 2010-06-16
forum: Server Platforms
---

### Post by Jester2109 on 2010-06-16
Having finally got Samba shares and printer shares working on my Lucid Lynx server, I've noticed that the throughput from/to those shares is very slow to what I was used to when I had those shares on a W2K server.

Having Googled this problem, I noted that there was a known issue with this in Karmic (believe Brian Wu was looking at it). However, I don't see any results in Google as to this being a problem in Lucid.

I know ipv6 can cause a problem in this regard but having issued the command

lsmod | grep inet6

...I know that ipv6 is indeed disabled on my Lucid server.

Does anyone have any knowledge or further information on whether the error reported in Karmic still applies in Lucid, and can this be addressed in any way ?

Cheers

---

### Post by Jester2109 on 2010-06-16
Actually, as an addendum to the above, could it be related to an issue in / between Samba and Lucid Lynx ?

I only ask as I have a range of machines accessing those shares and all have the same throughput problem (but only to the Lucid server). The Lucid server is a wired connection to the rest of the network through a 10/100 ethernet card.

For information, I have machines accessing those shares from Windows XP, Windows Vista, Windows 7, Macintosh OSX Leopard and an Ubuntu Desktop.

Cheers

---

