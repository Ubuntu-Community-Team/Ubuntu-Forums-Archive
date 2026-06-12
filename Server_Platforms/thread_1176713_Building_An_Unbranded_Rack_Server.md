---
title: "Building An Unbranded Rack Server"
date: 2009-06-02
forum: Server Platforms
---

### Post by johnbradbury on 2009-06-02
Hi all,
I'm looking to build a home training lab consisting of a new 27U rack, two rack mount servers, and a third rack mount server acting as a NAS device.

I'm new to the linux community so this will be part of my training plan.

Can you advise if there are any hardware guides or compatability lists I could use?

Any other advise is most welcome.

---

### Post by alastair on 2009-06-02
Linux is compatible with most server hardware now, so there's not much to advise really. Unless you go for something exotic, there's no reason you won't manage to install and run Ubuntu on a server class system.

---

### Post by koenn on 2009-06-02
raid controllers have been know to be troublesome.
you might want to check if the one you have / are planning to buy is supported on the distro you're going to use, either by the vendor or by the community. If it is, you might want to search for known issues.

---

### Post by uupreti on 2009-06-02
I will say **NVIDIA** (for graphics) and **Broadcom** (if you are planning to have wireless station too). It will not give much pain in your butt to be installed.

---

### Post by Vegan on 2009-06-02
> **koenn said:**
> raid controllers have been know to be troublesome.
you might want to check if the one you have / are planning to buy is supported on the distro you're going to use, either by the vendor or by the community. If it is, you might want to search for known issues.

That is an understatement. I have found that none of the 16 channel SATA raid cards available work with Ubuntu according to manufacturers web sites.

Yo Canonical, can we get some RAID drivers pleeze.

---

### Post by koenn on 2009-06-02
> **Vegan said:**
> That is an understatement. I have found that none of the 16 channel SATA raid cards available work with Ubuntu according to manufacturers web sites.

Yo Canonical, can we get some RAID drivers pleeze.
If they support Linux at all, manufacturers usually support RedHat and Suse. Ubuntu isn't enough of a name yet. You'll occasionally find .deb packages that might work on both Debian and Ubuntu (and other Debian derivatives). 
Common server hardware usually has community developed drivers as well. Maybe SATA RAID controllers aren't common enough yet - SCSI is still the norm AFAIK, although SATA is beginning to show up as 'slow' storage (eg for backups)

---

### Post by y@w on 2009-06-02
I've used 3ware cards on Ubuntu and Red Hat with great success (never had an issue).

---

### Post by smileypaul on 2009-06-05
same, 3ware cards without issue!

---

