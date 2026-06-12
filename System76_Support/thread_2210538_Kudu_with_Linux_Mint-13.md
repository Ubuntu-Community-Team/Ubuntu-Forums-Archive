---
title: "Kudu with Linux Mint-13"
date: 2014-03-11
forum: System76 Support
---

### Post by wagb278 on 2014-03-11
EDIT - Linux Mint-13 did not work on Kudu, needed to use Linux Mint version 16. 
I installed Linux Mint-16 as a dual boot with Ubuntu 13.10 as the other OS on a new Kudu Professional.  It appears the screen brightness (Fn+F8 & Fn+F9) keys do not function when running Linux Mint; they do work in Ubuntu. Those are the only Fn keys I tried, there may be others that don't work.  I guess that is due to the System 76 drivers need to be installed on Linux Mint, but will those drivers work in Linux Mint and if so, how do I perform the fetch and install?  Which drivers do I need for Fn key functions?  The fact that these drivers on the System 76 site say they are for MS Windows scares me a little. 

Thanks

---

### Post by tlroche on 2014-03-16
> **wagb278 said:**
> I guess that is due to the System 76 drivers need to be installed on Linux Mint, but will those drivers work in Linux Mint

I'm not familiar with the Kudu, but I have used [the System76 Debian driver]("http://planet76.com/repositories/") (note the singular!) on S76 hardware with Mint in the past (and have run LMDE on a PanP5 for a few years now). Note that the S76 driver is Debian, and Debian is "upstream" of both Mint and Ubuntu [(et al)]("http://en.wikipedia.org/wiki/Debian_family#Debian-based").

> **wagb278 said:**
> Which drivers do I need for Fn key functions?  The fact that these drivers on the System 76 site say they are for MS Windows scares me a little.

**Do not use Windows drivers!** Just download the latest S76 Debian driver from [here]("http://planet76.com/repositories/").

> **wagb278 said:**
> if so, how do I perform the fetch and install?

You'll be downloading a [.deb file]("http://en.wikipedia.org/wiki/Deb_%28file_format%29"), which you'll install (or remove) in the [usual (APT) ways]("http://en.wikipedia.org/wiki/Dpkg#Example_use").

---

