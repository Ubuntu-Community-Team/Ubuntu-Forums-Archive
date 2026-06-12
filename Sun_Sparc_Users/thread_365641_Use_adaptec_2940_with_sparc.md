---
title: "Use adaptec 2940 with sparc?"
date: 2007-02-19
forum: Sun Sparc Users
---

### Post by mvdw on 2007-02-19
Hi all:

I have a blade 100 which I've successfully installed with edgy, however I'd like to reuse a couple of external SCSI drives that were originally connected to my now dead ultra 1/E. I have an adaptec 2940 PCI scsi card; is there any chance of getting ubuntu to recognise this card? It doesn't seem to want to recognise it when I put it in the machine post-installation; is it worth reinstalling and trying to get the installer to pick it up for configuration, or should I compile a new kernel, or should I just give up and use the disks another way?

Cheers,
mvdw

---

### Post by netztier on 2007-02-20
> **mvdw said:**
> 
I have a blade 100 which I've successfully installed with edgy, however I'd like to reuse a couple of external SCSI drives that were originally connected to my now dead ultra 1/E. I have an adaptec 2940 PCI scsi card; is there any chance of getting ubuntu to recognise this card? 

There is a much-read (german) article about SCSI Upgrade for IDE-based SUN Systems - especially about the Ultra 5: [SCSI Aufrüstung von SUN-IDE-Systemen]("http://www.belwue.de/projekte/SUN-IDE-2-SUN-SCSI.html"). Translating with [babelfish]("http://babelfish.altavista.com/") or similar might reveal the essentials of the article in english.

In a nutshell: find a PCI SCSI host adapter with the NEC/Symbios/LSI Logic **53c875** chipset. It should work instantly - you should be able to find low-cost controllers on the market. I tried with a 53c825 in my Ultra 5, but it was a failure.

best regards

Marc

---

