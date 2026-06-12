---
title: "Copy-on-write filesystems"
date: 2020-04-03
forum: Ubuntu, Linux and OS Chat
---

### Post by Brinstar on 2020-04-03
I'm thankful to the developers for finally including a copy-on-write filesystem in a LTS version of Ubuntu.
Could someone from Canonical please let me know if there is an official push to switch to a copy-on-write filesystem as the default, at least by the next LTS (22.04)? 
Having actually used ZFS today for the 1st time, it's clear that this is the way forward. Maybe add btrfs as another option for auto-partitioning?

And its also excellent having the option to use a different filesystem at install time. I wish we had an auto-partitioning option for any alternative fs, but this is good.

---

### Post by SeijiSensei on 2020-04-03
How is that different from RAID1?

---

### Post by Brinstar on 2020-04-03
I don't know enough about RAID1 to comment.

---

### Post by TheFu on 2020-04-03
First, nobody here works for Canonical. i have no ideal what they may or may not do.

btrfs probably won't be a default any time soon.  Some light reading:   [https://wiki.debian.org/Btrfs#Warnings](https://wiki.debian.org/Btrfs#Warnings)
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/7.4_release_notes](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/7.4_release_notes)
/chap-red_hat_enterprise_linux-7.4_release_notes-deprecated_functionality_in_rhel7

i have nothing against users having choices, but not all choices are good just because they are available.  There are almost always caveats for any choices, including the defaults.

---

