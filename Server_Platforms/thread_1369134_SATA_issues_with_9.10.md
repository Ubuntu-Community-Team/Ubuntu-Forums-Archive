---
title: "SATA issues with 9.10"
date: 2009-12-31
forum: Server Platforms
---

### Post by Deathcon_1 on 2009-12-31
I've posted before with a similar topic and gotten no response; although I know this is an Ubuntu-specific issue (these cards work fine on Gentoo.)  Right now Ubuntu will start complaining about SATA channel errors, specifically and instruction could not be understood.  At first this was localized to the Silicon Image PCI-based SATA controllers but has recently migraded to the onboard SATA controllers that came with the motherboard which were previously working.  Googling the issues give me no results, apparently nobody is having issues with SATA and Ubuntu Server 9.10.

My question is, since I'm still new to Ubuntu having converted from Gentoo, is there anything special that needs to be done to get SATA working flawlessly without these bogus errors?  I know both cards work; the drives are all brand new 1TB or 1.5TB mix of Western Digital Green and Seagate Barracuda's.  

The setup consist of LVM2 running on top of LUKS (so LVM data is protected within the LUKS encryption scheme.)  Each drive has 512MB of SWAP using cryptswap + random keys.  

Help! This is a key fileserver and these errors are killing it!

---

### Post by inclusivedisjunction on 2010-01-01
Do you have an exact copy of the error message? Also, at what point were you using Gentoo on the machine (and what kernel version). Are there any SMART errors being reported in the BIOS?

---

