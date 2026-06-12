---
title: "No internet"
date: 2010-03-30
forum: Ubuntu Studio
---

### Post by anthony2010 on 2010-03-30
Hi all.

Struggling with a fresh install of studio 9.10 (386). Its on a Dell inspiron d600.

I have no internet whatsoever be it by cable (inserted during install) or wireless.

So far I used another computer to download ndiswrapper then installed it on the dell. No go, nothing.

Ive done everything necessary in 'network' setting it to automatic dchp for wired and also for wireless I put in name and password to network.

I tried typing 'sudo /etc/init.d/network restart' - still nothing.

I'm out of ideas and need to ask for more experienced help.

Naturally with no internet, I can't download anything nor can I seem to be able to unpack wicd (also downloaded on another pc, transferred over and unpacked.

If someone can help, I would be most grateful.

Anthony.

---

### Post by n0dix on 2010-03-30
Show the output from 'lspci' command.
Do you have internet with a Live CD?

---

### Post by anthony2010 on 2010-03-30
Hi nOdix

No office on dell (had to elect not to install software to get it to install at all) so cant copy / paste / transfer over so Ive manually written here what I think is relevant from lspci. Also Ubuntu studio dvd doesn't have a live cd option.

Heres the info:

00:if.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)

02.00.0 Ethernet controller: Broadcom Corporation Netextreme BCM5705M Gigabit Ethernet (rev 02)

02:03.0 Network controller Ralink RT2561/RT61 rev B 802.11g

---

