---
title: "Kworker 0:1 and gpe00"
date: 2017-02-23
forum: Server Platforms
---

### Post by arlenn2 on 2017-02-23
Hello,

I have been having some trouble with kworker consuming 100% of a CPU core.  I have googled the snot out of this and seems somewhat widespread without a lot of resolution.  Many of the guides provide a work around by disabling the offending gpe.  Is this wise?

All of the articles are a little slim on advice on ways to diagnose the exact cause of issue.  Running "perf", it looks like much of the interrupt activity is caused from ACPI events.  Is there a way to narrow this down a bit?

The system is a fairly bare-bones Atom based Intel motherboard that has been converted into a NAS/file-server.  Headless 16.04 server install.  The only weird piece of equipment is a PCI raid card (Silicon Image 3114) running a single hard drive.  I don't know this is the offending device, it is just the only thing that isn't "normal".

Thanks in advance.

---

