---
title: "I think I've Screwed Up Big Time"
date: 2007-11-17
forum: The Cafe
---

### Post by regomodo on 2007-11-17
`

---

### Post by hanzomon4 on 2007-11-17
It shouldn't do anything

---

### Post by Brautigam on 2007-11-17
> **hanzomon4 said:**
> It shouldn't do anything
no it should not

---

### Post by regomodo on 2007-11-17
`

---

### Post by regomodo on 2007-11-17
`

---

### Post by bonzodog on 2007-11-18
if the sdb1 partition was ext3, then you should have run ext3.fsck --check on it. Only run the type of fsck that is appropriate to the FS type.

---

### Post by regomodo on 2007-11-18
`

---

### Post by corney91 on 2007-11-18
I use 'e2fsck' which should workon ext3 as well as ext2.

---

### Post by Herman on 2007-11-18
sudo e2fsck -C0 -p -f -v /dev/sdb1 should fix it for you.
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```The same command will work for ext2 or ext3, basically ext3 is ext2 file system with journalling added.

fsck is good too, but it will only run e2fsck for you with the general purpose options it considers safe. It doesn't have the ability to guess what specific e2fsck options we might need for a given situation, so it's not as powerful.

Regards., Herman :)

---

### Post by regomodo on 2007-11-18
`

---

