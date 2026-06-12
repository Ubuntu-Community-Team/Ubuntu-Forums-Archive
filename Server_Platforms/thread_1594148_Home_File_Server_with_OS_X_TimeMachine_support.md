---
title: "Home File Server with OS X TimeMachine support"
date: 2010-10-12
forum: Server Platforms
---

### Post by birdd on 2010-10-12
I'm wanting to setup a file server for home.

I'll probably use the following: Ebox, Firefly Media Server, TorrentFlux

I'm still not sure about how to go about redundancy for the store, possibly software RAID 5. ZFS would be cool but the linux support through FUSE and large memory requirements are a bit of turn-off...

I'm also not sure how to go about supporting TimeMachine on my new Macbook Pro. I've seen a couple of old guides on the web discussing Netatalk and Avahi but noting new...

I'm thinking I'll probably use a spare 2.5" 80GB SATA drive for the OS drive, and then probably 4x2TB HDD (for 6TB of useable storage in RAID 5)

I'm not sure about what mobo and cpu to use yet... I was originally thinking to go with an atom based Mini-ITX mobo but to get one with 4x SATA ports is hard enough, let alone trying to get one with 5-6x (1 for OS and 4 for data) so I'm thinking maybe I should get a low power Intel or AMD based Micro-ATX mobo with 6x SATA...

I'm also thinking I'll setup CrashPlan for online backup from the server (plus directly from my Macbook Pro and my Desktop)

Anyone done this before? any thoughts, comments or suggestions?

---

### Post by BobVila on 2010-10-12
I set up an ubuntu server to support TimeMachine for my wife's macbook pro. It was a major PITA...

I'm not at home, so I don't have my bookmark with the walkthrough, but this one seems close:

[http://sidikahawa.blogspot.com/2010/03/setting-up-time-machine-server-on-my.html]("http://sidikahawa.blogspot.com/2010/03/setting-up-time-machine-server-on-my.html")

---

