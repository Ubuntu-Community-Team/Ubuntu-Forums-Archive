---
title: "Ubuntu 7.04 - E450"
date: 2007-04-24
forum: Sun Sparc Users
---

### Post by stuartbh on 2007-04-24
Dear fellow Ubuntu Community Members:

It is of particular interest to me to effectuate the installation of Ubuntu 7.04 onto a Sun E450 (something I have never tried before), using the CD-ROM drive currently in the E450.

(1) If I get a DVD Drive for the E450, which are recommended to be compatible with Ubuntu 7.04?

(2) What "gotchas" much I look out for or prepare for precedent to such an installation as such?

(3) While the idea of running ZFS (under Solaris 10) is inviting, I prefer Linux. However, are there any step by step guides I can get that will be easily instructive to asserting a RAID 5 environment on the E450 using Linux to assert the RAID 5? Does LVM or any other such RAID environment on Linux currently have GUI based configuration utility?

Thank you for your time and consideration regarding the instant matter, and do have a most wonderful and blessed day!


V/R,

Stuart B. Tener, N3GWG
Beverly Hills, CA / Las Vegas, NV / Philadelphia, PA / Washington, DC

---

### Post by rufius on 2007-04-24
For question 1) Any should work assuming it will interface with the e450.

For question 2) There aren't any that I can think of. I recently put Feisty on an e220r.

For question 3) No idea.

---

### Post by stuartbh on 2007-04-25
> **rufius said:**
> For question 1) Any should work assuming it will interface with the e450.

Excellent to hear this!

> **rufius said:**
> For question 2) There aren't any that I can think of. I recently put Feisty on an e220r.

As well, this is particularly good to hear.

> **rufius said:**
> For question 3) No idea.

Perhaps someone on the list will be familiarized with the GUIs available under Ubuntu 7.04 pursuant to the assertion of a RAID 5 environment or LVM (or alternative) under Ubuntu 7.04, and said person will be interested to compound your reply with a deeper perspective.

Thank you for your time and consideration regarding the instant matter, and do have a most wonderful and blessed day!


V/R,

Stuart B. Tener, N3GWG
Beverly Hills, CA / Las Vegas, NV / Philadelphia, PA / Washington, DC

---

### Post by erm67 on 2007-04-25
> **stuartbh said:**
> Perhaps someone on the list will be familiarized with the GUIs available under Ubuntu 7.04 pursuant to the assertion of a RAID 5 environment or LVM (or alternative) under Ubuntu 7.04, and said person will be interested to compound your reply with a deeper perspective.

If you're searching for a metatool alternative there isn't.
gparted can do some partitioning, but is more like partition magic.
It isn't that difficult to set up a raid with vi and raidtools, even you can do it :), if you prefer something more graphical use gedit instead of vi.

---

