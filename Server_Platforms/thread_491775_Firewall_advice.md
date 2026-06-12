---
title: "Firewall advice"
date: 2007-07-04
forum: Server Platforms
---

### Post by drhiii on 2007-07-04
Am looking for recommendations for where/how-to build a bridged firewall that provides for not just setting policies, but traffic monitoring and if possible, traffic shaping.

Recommendation anyone?  Can Smoothwall do this?

---

### Post by droberts on 2007-07-04
I recommend [Endian]("http://endian.com/"). I believe it does everything you are looking to do.

---

### Post by bapoumba on 2007-07-04
*Ahem*
Can someone please provide a non-commercial advice (Shorewall ?). I'm not enough into this to answer the OP.

---

### Post by darkog on 2007-07-04
apparently smoothwall 3 can.

> Quality-of-Service (QoS) support for traffic-shaping and management - nice and easy to use but powerful, can traffic shape Peer-to-Peer traffic

read the [release notes]("http://www.smoothwall.org/about/release/3.0-beta.html").

---

### Post by az on 2007-07-04
There are a number of individual tools.  Wondershaper is a simple and great traffic-shaping app.  Firestarter can the rest of what you ask...

---

### Post by droberts on 2007-07-04
Yer...for the record Endian is *ahem* a free product. Download the community edition. I installed 2 firewalls yesterday and only paid for my hardware.

---

### Post by darkog on 2007-07-04
> **droberts said:**
> Yer...for the record Endian is *ahem* a free product. Download the community edition. I installed 2 firewalls yesterday and only paid for my hardware.

have you used smoothwall or monowall? is endian better? just wondering.

---

### Post by drhiii on 2007-07-04
Thank you everyone for this advice.  Especially for re-pointing to open source solutions.  I'd looked at some of these, but it always helps to have validation of sorts.  Will look into Smoothwall and Firestarter, for starters.

This is a great community of people.  FInally, a place to come come after officially jettison-ing Windows!

drhiii

---

### Post by droberts on 2007-07-06
I have used Monowall, but only for a couple of days. I've also used IPCOP.

I really like Endian. They have a number of groups and forums that are helpful. The dev team contributes regularly to the threads as well.

I am not affiliated with Endian in any way, just a happy user and I've deployed a number of boxes running Endian and will be switching more over as time (cough) becomes available.

---

### Post by nix4me on 2007-07-06
ipcop, monowall or pfsense.

They are all great firewall/router distros.

Ipcop is linux.  monowall and pfsense are freebsd based.

nix4me

---

