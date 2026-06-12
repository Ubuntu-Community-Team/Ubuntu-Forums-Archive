---
title: "Ubuntu Server 8.04.2 &amp; Realtek 8111/8168B Network"
date: 2009-04-18
forum: Server Platforms
---

### Post by MunkyJunky on 2009-04-18
I have some spares I'm looking to turn into a server installation, but I use a Realtek 8111/8168B network card (onboard). 

Basically, due to 8.04 having a bug with the r8169 driver series, I'm left with no internet on the machine. I downloaded the driver from Realteks website, but when I tried **make clean modules** I got an error saying 'make is not installed'. Since I have no internet, I can't install 'make' either. 

Ideally, I'd like the correct driver so I can reinstall my system and at install load in the correct driver. I know that 8.10 works perfect with this card, since it got fixed by 8.10, but I'd really like to use 8.04 for the LTS. 

Any help on how to move forward with this?

---

### Post by cariboo on 2009-04-18
Install build essentials, if I remember correctly it is on the install cd. Make sure you have the cd enabled in /etc/apt/sources.list

Jim

---

