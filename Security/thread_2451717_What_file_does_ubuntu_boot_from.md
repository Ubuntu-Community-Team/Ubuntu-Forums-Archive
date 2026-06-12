---
title: "What file does ubuntu boot from?"
date: 2020-10-09
forum: Security
---

### Post by nommalebag on 2020-10-09
I'm following this guide
[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)
and I finished every step but now when I go into my bios and boot from UEFI there's no files to boot from. I'm wondering if anyone knows what files I might need to get my computer to start up or if I should just do the normal disk encryption that ubuntu offers with the installer.

---

### Post by CelticWarrior on 2020-10-09
Welcome.

Have you installed in UEFI mode?

---

### Post by guiverc on 2020-10-09
You haven't mentioned which release you're asking about.

The reason I ask this is many changes have been occurring in the *groovy* cycle, esp. with ISOs, but it's also impacted booting systems from disk too.  The aim is to have all boxes & architectures more alike.

It might help if you're specific as to what release, and/or flavor (Lubuntu using `calamares` differs slightly too when explored from *live* post-install unless I'm fuzzy in memory).


*Note:  I'm no expert, others here are. I'm heavily involved with testing so regularly do QA-test installs, which includes booting a live media to validate the install is encrypted as expected. Once I see what I'm looking for I then boot & so it's only a quick glance without full understanding..*

---

### Post by nommalebag on 2020-10-10
I'm using ubuntu 20.04 and just normal ubuntu.

---

### Post by EuclideanCoffee on 2020-10-12
This guide is advanced. You would likely be safe without encrypting your /boot folder, which I think this goes to great lengths to cover. The automation itself doesn't require you to go into the BIOS at all regardless if you're using UEFI. I suggest you use the full disk encryption option in the installer. You'll need to check a box early in the setup.

---

