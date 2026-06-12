---
title: "Whole Drive Encryption for Dual-Boot"
date: 2007-10-01
forum: Server Platforms
---

### Post by Catsworth on 2007-10-01
Hey Guys,

I have a dual-boot setup (Windows XP and Ubuntu) and I'd like to encrypt the whole hard-drive.  Preferably with a product that uses some sort of dual-factor authentication at boot (token + password for example).

I've found a couple of products that are able to do this, but they only seem to work in Windows.  Can anybody suggest a product that I can use that will be equally happy in Linux and Windows?  

Failing that, is there a product available just for Linux, and would I be able to use that and then run XP as a VMWare (or similar) from within the Linux install?

Thanks.

---

### Post by Yoooder on 2007-10-01
I am forced to use PointSec for my WinXP work laptop, which provides a 100% disk encryption solution.

They offer a linux version, but I don't know how it would act in a dual-boot environment--or if they sell single licenses of the software.  It's probably worth checking out at least

The other option is to run the bare minimum from an unencrypted drive, and setup truecrypt or an encrypted device to store all your personal files.  This would have the added benefit of allowing the system to run access its core components without having to go through the encryption layer--which should make the machine quite a bit faster.  My $3k work laptop runs like its 5 years old with PointSec due to the nature of whole-disk encryption.

A third option to explore is purchasing a drive that natively does encryption transparently.  I don't have any experience with these so I can't say how good they or or how compatible--but I presume they would be the easiest to setup.

---

### Post by psusi on 2007-10-01
There are a number of howtos on the wiki describing how to set up full disk encryption.

---

### Post by Yoooder on 2007-10-01
> **psusi said:**
> There are a number of howtos on the wiki describing how to set up full disk encryption.

Good call!  Here's the first one I found:
[https://help.ubuntu.com/community/FullDiskEncryptionHowto]("https://help.ubuntu.com/community/FullDiskEncryptionHowto")

---

### Post by Catsworth on 2007-10-02
Hi Guys,

Yeah, I'd considered only encrypting the bare minimum that I have to, unfortunately Windows has a nasty habit of depositing files just about anywhere it sees fit and normally maintains copies of your open files elsewhere on the disk (which it then doesn't shred properly).

I'd looked at the Wiki, but only seen that one article on full disk encryption that Yoooder linked to.  I'm not sure that's going to help me out too much with the dual-boot situation as it doesn't seem to take Windows into account.

Thanks for the help so far though guys, much appreciated.

---

### Post by psusi on 2007-10-02
Well yea, you will need a separate product to encrypt your windows partition.

---

### Post by Yoooder on 2007-10-04
For your needs would running Windows in a Virtual Machine be feasible?  The VM could live in an encrypted Linux partition transparently.

---

### Post by psusi on 2007-10-07
That would work.

---

### Post by Niniel on 2007-10-09
There's a free product that does what you want, but it's not Open Source and it only works with Suse and to some extent, Red Hat.

[http://www.ce-infosys.com/english/downloads/free_compusec/]("http://www.ce-infosys.com/english/downloads/free_compusec/")

---

