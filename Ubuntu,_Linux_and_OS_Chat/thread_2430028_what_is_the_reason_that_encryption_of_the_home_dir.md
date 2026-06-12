---
title: "what is the reason that encryption of the home directory or the whole disk is..."
date: 2019-10-26
forum: Ubuntu, Linux and OS Chat
---

### Post by ronjjjg8885 on 2019-10-26
not relible on linux

thanks!!!

---

### Post by deadflowr on 2019-10-26
Thread moved to chat

---

### Post by uRock on 2019-10-26
How is it not reliable? I used full disk encryption for over a year on my current machine without issue. I decided to remove encryption when I realized I live somewhere where people feel safe leaving their doors unlocked, tools and bikes in front yards without them growing legs, and I like my system booting super fast.

---

### Post by zimbuf on 2019-10-26
Did it recently with a btrfs drive. Didn't have any issues on my end.

---

### Post by TheFu on 2019-10-26
> **ronjjjg8885 said:**
> not relible on linux

thanks!!!

Please explain "not relible"?

I've been using LUKS encryption for at least 5, maybe 8 yrs.  No issues that weren't due to hardware failures.  Whenever using whole partition encryption, like LUKS, having great backups is mandatory as any HW fault will lead to complete data loss.  That is sorta the point for encryption of that type.

The only slight trouble I had was in trying to resize a LUKS container that was holding PV, VG, and multiple LVs. It was always reliable, however.

HOME directory encryption is deprecated for a number of reasons. The option was removed.  It was stable, just slow and leaked metadata about the encrypted files.

I've been using LUKS encryption on Android since v4 was released. Never had any issues with it either.

Modern CPUs have built-in support for AES encryption so while there is a tiny performance hit with using encryption, if the defaults are used for LUKS, then that overhead is about 3%.

---

