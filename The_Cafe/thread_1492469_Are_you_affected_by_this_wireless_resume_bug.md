---
title: "Are you affected by this wireless resume bug?"
date: 2010-05-24
forum: The Cafe
---

### Post by aysiu on 2010-05-24
Since upgrading my netbook to 10.04, I've noticed a regression, and I'm curious as to what others' experiences of this have been.

Have you also experienced this bug? If so, does it bother you? What workarounds have worked for you, if applicable?

How long does it take you to resume? (It takes my computer anywhere between 15 seconds and 2 minutes with a Broadcom 4312 and the wl driver.)

If you're not experiencing this bug, what wireless card do you have?

Here's the bug report:
[network manager slow to reconnect after suspend/resume](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

P.S. WICD hasn't given me any faster a resume after sleep.

---

### Post by mamamia88 on 2010-05-24
it usually reconnects pretty quickly.  probably 15 seconds tops.  never actually timed it.  btw it's a broadcom card not sure which one

---

### Post by aysiu on 2010-05-24
> **mamamia88 said:**
> it usually reconnects pretty quickly.  probably 15 seconds tops.  never actually timed it.  btw it's a broadcom card not sure which one
The bug isn't that it times out but that it just takes a really long time to reconnect.

By the way, do you mind if I ask what wireless card you're using?

---

### Post by FuturePilot on 2010-05-24
Every once in a while that will happen to me on my laptop. It has an Intel 3945ABG card. It happens a lot less frequently than it used to though. However, I've never had it happen on my netbook which has a Broadcom BCM4312 card and I've never had it happen on my old laptop which has an Atheros card. Both are always connected before I can unlock the screen.

When it does happen though, usually right clicking on network manager and disabling and re-enabling wireless usually gives it good kick.

---

### Post by PuddingKnife on 2010-05-24
I do not have it, but my wireless is disabled every time I power on the laptop.

---

### Post by aysiu on 2010-05-24
By the way, the /usr/lib/pm-utils/sleep.d/55NetworkManager file says this at the top: > # If we are running NetworkManager, tell it we are going to sleep.
# TODO: Make NetworkManager smarter about how to handle sleep/resume
#       If we are asleep for less time than it takes for TCP to reset a
#       connection, and we are assigned the same IP on resume, we should
#       not break established connections.  Apple can do this, and it is
#       rather nifty.
 Yes, Apple does do this on Macs, and it is rather nifty. Too bad Ubuntu's undergone several releases with this comment in the file and no actual progress on fixing this problem.

---

### Post by NightwishFan on 2010-05-24
The resume bug is probably an upstream issue, perhaps talk with the driver developers themselves.

---

### Post by witeshark17 on 2010-05-24
My laptop resumes essentially instantly, in fact it appears to leave the connection active in sleep. My wireless card:

Dell 1397 Wireless-G

---

### Post by seenthelite on 2010-05-24
Intel wifi link 5100 AGN from suspend 6 seconds with Network Manager
Broadcom BCM4328 a/b/g/n from suspend 10 seconds with WICD

Both on 5GHz N, they connect to the access point instantly and acquiring IP address takes the time.

---

### Post by witeshark17 on 2010-05-25
I looked more carefully, the wireless card is disconnected in sleep, but reconnects quickly with the last used WiFi

---

### Post by aysiu on 2010-05-25
> **witeshark17 said:**
> I looked more carefully, the wireless card is disconnected in sleep, but reconnects quickly with the last used WiFi
"[Q]uickly," meaning how many seconds?

I've found through this bug and its surrounding bug reports that people have differing ideas of what quickly means. Some people consider 30 seconds to be not long at all for wireless to resume after waking from sleep.

---

### Post by cariboo on 2010-05-25
I have two wireless access points, one in my house that is encrypted and one that is wide open in my shop, my Comapq Mini 110 with Broadcom 4312 chipset, will connect to the encrypted access point almost right away, within a couple of seconds after coming out of hibernate, but sometimes I need to restart it to connect to the one in my shop even though it's less than 10ft away.

---

### Post by aysiu on 2010-05-25
> **cariboo907 said:**
> I have two wireless access points, one in my house that is encrypted and one that is wide open in my shop, my Comapq Mini 110 with Broadcom 4312 chipset, will connect to the encrypted access point almost right away, within a couple of seconds after coming out of hibernate, but sometimes I need to restart it to connect to the one in my shop even though it's less than 10ft away.
Is that WPA2 encryption?

---

### Post by WinterRain on 2010-05-25
> **aysiu said:**
> Since upgrading my netbook to 10.04
When you say upgrade, do you mean overwriting files, or clean install? Btw, it works for me with the broadcom chipset.

---

### Post by aysiu on 2010-05-25
> **WinterRain said:**
> When you say upgrade, do you mean overwriting files, or clean install? Btw, it works for me with the broadcom chipset.
Clean install.

Can you be more specific about "works"? Are you using encryption? WPA2? The wl driver? How many seconds before it reconnects after resume?

---

### Post by witeshark17 on 2010-05-25
> **aysiu said:**
> "[Q]uickly," meaning how many seconds?

I've found through this bug and its surrounding bug reports that people have differing ideas of what quickly means. Some people consider 30 seconds to be not long at all for wireless to resume after waking from sleep. Oh, quickly means under a second. That's why a few times it was as though the connection was never off.

---

### Post by WinterRain on 2010-05-25
> **aysiu said:**
> Clean install.

Can you be more specific about "works"? Are you using encryption? WPA2? The wl driver? How many seconds before it reconnects after resume?

I'm using WEP (I'm not one of those overly paranoid people who needs NSA level encryption) I'm using the B43 driver I think. I didn't time it, but it's probably a few seconds or more.

---

### Post by aysiu on 2010-05-25
> **WinterRain said:**
> I'm using WEP (I'm not one of those overly paranoid people who needs NSA level encryption) I'm using the B43 driver I think. I didn't time it, but it's probably a few seconds or more.
Should I use the b43 driver? Is that better for 4312 than wl?

Hardware Drivers recommends only wl for my card.

---

### Post by oldsoundguy on 2010-05-25
No problems .. using D-Link 520x internal card with the Atheros chip in desktop(s) .... 4 of them.

---

### Post by cariboo on 2010-05-25
> **aysiu said:**
> Is that WPA2 encryption?

Yes it is.

---

### Post by themarker0 on 2010-05-25
Acer aspire timeline 581ot-8982

Loads old connection after sleep almost instantaneously.

---

### Post by steveneddy on 2010-05-25
I have the Intel wireless chip in my laptop.

---

### Post by screaminj3sus on 2010-05-25
no problems here with intel 4695

---

### Post by kspncr on 2010-05-26
> **aysiu said:**
> Should I use the b43 driver? Is that better for 4312 than wl?

Hardware Drivers recommends only wl for my card.

I think it would definitely be worth trying the B43 driver. It's what I use for my Broadcom 4311 wireless card (almost what you have) and I haven't had any trouble whatsoever. I just tested and it only takes ~5 seconds to wake up from sleep and be connected to the internet.

It's strange to me that it didn't recommend the B43 driver to you, since it really seems like it ought to work with a 4312 (according to its description).

---

### Post by Khakilang on 2010-05-26
I use an Aztech USB wireless adapter and its been working fine on my computer. But I am using a desktop and it also work well in my old notebook which does not come with a wifi built in.

---

### Post by Lucretius on 2010-05-26
I need to restart my laptop every time I resume from suspend, as  can not connect at all

This has happened with two different intel wireless cards

Drives me nuts >.<

---

### Post by NCLI on 2010-05-26
No problem here, using an "Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)"

---

### Post by aysiu on 2010-05-27
> **kspncr said:**
> I think it would definitely be worth trying the B43 driver. I install b43, and it was terrible. Basically didn't work at all: ```
[  433.948195] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  439.473148] b43-phy0: Controller restarted
[  439.484414] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  439.484436] b43-phy0: Controller RESET (DMA error) ...
[  439.717184] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  445.265159] b43-phy0 ERROR: 
[  445.265171] b43-phy0: Controller restarted
[  445.265190] Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  445.265206] b43-phy0: Controller RESET (DMA error) ...
[  445.477127] b43-pci-bridge 0000:01:00.0: PCI INT A disabled
```

I had to do some manual .deb downloads to get wl working again.

---

### Post by kspncr on 2010-05-27
> **aysiu said:**
> I install b43, and it was terrible. Basically didn't work at all: ```
[  433.948195] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  439.473148] b43-phy0: Controller restarted
[  439.484414] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  439.484436] b43-phy0: Controller RESET (DMA error) ...
[  439.717184] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  445.265159] b43-phy0 ERROR: 
[  445.265171] b43-phy0: Controller restarted
[  445.265190] Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  445.265206] b43-phy0: Controller RESET (DMA error) ...
[  445.477127] b43-pci-bridge 0000:01:00.0: PCI INT A disabled
```

I had to do some manual .deb downloads to get wl working again.

Hmm...must be why Hardware Drivers didn't recommend it for you. I can't imagine why it doesn't work for you though...

---

### Post by dragos240 on 2010-05-27
It's always done this on my tower. I think it's a RT61 card.

---

### Post by 23meg on 2010-05-27
Not affected, with ath9k. The connection is up within three seconds upon resuming.

---

