---
title: "Network dropping due to &quot;heavy&quot; network traffic on Dell Mini 10n"
date: 2010-07-10
forum: Ubuntu Moblin Remix
---

### Post by Cavin on 2010-07-10
Hello,

I just purchased my mom this laptop for her birthday. I'm still trying to work out everything to make it perfect for her when she gets it...

I have an issue with the wireless though. If I have any kind of heavy traffic, the wireless simply drops. Heavy traffic could include downloading updates from the repo, downloading a new program with any package manager (including apt-get using the shell), or transferring files over the network. 

I'm using an Apple Time Capsule for the router (yes, I myself am a Mac person. But I do love Ubuntu!). It's set to use WPA2 encryption, using 802.11n/g/b. 

I have had no problems with other devices connecting to the network (Macs, Ubuntu computers, Windows computers, iPod Touches), so I don't think it's the router, or a compatibility issue solely with Ubuntu. 

If it's relevant, when I say it drops, I mean:

- I download a file, it goes for a few seconds
- I see a dialogue stating my wireless had disconnected.
-- Most of the time it re-connects after a few seconds.
-- Sometimes it doesn't reconnect at all until I manually reconnect the first drop.
-- Every time, even after it's automatically reconnected a few times, it ends up with me having to manually reconnect. This takes up to five minutes sometimes.

Any ideas?

---

### Post by cariboo on 2010-07-10
What driver does you wireless device use.

---

### Post by Cavin on 2010-07-10
When I do lchw -C network I get a lot of output, but the relevant output for wireless is this:

```
 
description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:4d:82:f1:8b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=10.0.1.7 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff

```

Does that help? :)

---

### Post by Cavin on 2010-07-13
Anyone?

**Edit:**

Found [the solution here]("http://ubuntuforums.org/showthread.php?p=9586066"). 

Simply run the following command:

```
sudo apt-get install linux-backports-modules-karmic-generic
```

And the issue is fixed!

[COLOR="Red"]Great success![/COLOR]

**Edit:**
I hated Moblin as soon as I saw it, and my mom was even more inclined to complain about it. I installed Ubuntu Netbook edition instead. It's so much more user-friendly.

---

