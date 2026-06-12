---
title: "Package kept back ubuntu-minimal"
date: 2008-11-09
forum: Server Platforms
---

### Post by Philio on 2008-11-09
I've upgraded a couple of my servers to 8.10 wondering why this package is being kept back and what it's for?

TIA.

---

### Post by cariboo on 2008-11-09
From Synaptic:
> Minimal core of Ubuntu
This package depends on all of the packages in the Ubuntu minimal system,
that is a functional command-line system with the following capabilities:

 - Boot
 - Detect hardware
 - Connect to a network
 - Install packages
 - Perform basic diagnostics

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

Jim

---

### Post by cariboo on 2008-11-09
From Synaptic:
> Minimal core of Ubuntu
This package depends on all of the packages in the Ubuntu minimal system,
that is a functional command-line system with the following capabilities:

 - Boot
 - Detect hardware
 - Connect to a network
 - Install packages
 - Perform basic diagnostics

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

It is a metapackage that install a group of other files

Jim

---

### Post by Philio on 2008-11-09
Thanks Jim, I had read that already actually.
Wondering why it has not upgraded it!

---

### Post by Philio on 2008-11-09
I've just upgraded another server this evening and noticed that apt was not showing the same afterwards as on the first 2 servers.

It seams that console-tools is esentially a repackaged version of kbd:

> `console-tools' was developed from version 0.94 of the standard `kbd' package, and integrates many fixes and enhancements, including new kbd features up to 0.99.

It looks like 8.10 uses kbd rather than console-tools, I've forced the update now.

---

