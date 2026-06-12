---
title: "KVM - The Emulator May Not Have Search Permisions"
date: 2013-03-29
forum: Virtualisation
---

### Post by daz1uk on 2013-03-29
As in the title, KVM doesn;t seem to have permission to access the hard disk with my image on, can anyone help me fix this please?

Thanks

---

### Post by daz1uk on 2013-03-29
Anybody?

I've tried this:

I had to uncomment these two out:

# The user ID for QEMU processes run by the system instance
user = "root"

# The group ID for QEMU processes run by the system instance
group = "root"

with no joy :(

---

### Post by JJJJNR on 2013-05-12
Hi daz1uk, just wondering did you have any joy in resolving this, I'm having the same issue after adding a 2TB drive to my system in hope of getting some VM's running for tests

---

### Post by heiko_s on 2013-05-13
Perhaps check the ownership/group of the root folder on the target drive? When logged in with your user name, do you have read/write access when this drive/partition is mounted?

Just a thought.

---

