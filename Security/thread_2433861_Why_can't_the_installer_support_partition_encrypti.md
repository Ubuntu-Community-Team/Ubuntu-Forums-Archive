---
title: "Why can't the installer support partition encryption?"
date: 2019-12-26
forum: Security
---

### Post by mnealbarrett on 2019-12-26
My apologies if I am posting this to the wrong forum.

I am wondering why the Ubuntu installer can't support installing Ubuntu alongside another OS (such as Windows) and encrypting the Ubuntu partition with LUKS?  It is possible to make such a set up manually, but it is not easy. (I did it successfully once, but it was hard)  With LUKS having been around for quite a few years now, why hasn't this been done?  

With my desktop, I ended up using two separate hard drives for Ubuntu and Windows, but this isn't possible with laptops and Intel tablets.

---

### Post by TheFu on 2019-12-27
I don't know the answer, but any other OS on the same physical hardware would be a liability against security for both OSes.  According to Canonical surveys, less than 5% of all installs actually use any encrypted storage at all.  If 20% of the installs used encryption, it would probably get more work?

---

### Post by mnealbarrett on 2019-12-27
> **TheFu said:**
> I don't know the answer, but any other OS on the same physical hardware would be a liability against security for both OSes.  According to Canonical surveys, less than 5% of all installs actually use any encrypted storage at all.  If 20% of the installs used encryption, it would probably get more work?

Perhaps. I wonder what percentage of Ubuntu installs are installed with Ubuntu as the only OS?  I really have no idea, but I am guessing that a high percentage of Ubuntu installs on existing PCs are in a dual-boot configuration. So could it be that few people install with encryption because it would force them to destroy their Windows installations?

---

### Post by TheFu on 2019-12-27
> **mnealbarrett said:**
> Perhaps. I wonder what percentage of Ubuntu installs are installed with Ubuntu as the only OS?  I really have no idea, but I am guessing that a high percentage of Ubuntu installs on existing PCs are in a dual-boot configuration. So could it be that few people install with encryption because it would force them to destroy their Windows installations?

All this says is that we assume other people are mostly like us.  ;)  Lacking any other data, it is a reasonable guess.

I have a dedicated 9 yr old laptop with Win7 on it and a win7 virtual machine.  Neither are used on the internet for general uses, no web browsing, no email, no direct user internet use though stock data is pulled over the internet.   One is for video editing and the other is for financial software.

I seldom see multi/dual-boot setups in my LUG.  About 80% are Linux-only installs.

At installfest in the local Universities, we strongly push using virtual machines for the CS and Engineering students who want to run Linux. Still about 20% will want to wipe Windows completely and reinstall Windows into a VM under Linux.  That's usually about 75 total installs per University.

---

