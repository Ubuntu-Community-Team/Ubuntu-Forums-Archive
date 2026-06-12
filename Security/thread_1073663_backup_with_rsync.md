---
title: "backup with rsync"
date: 2009-02-18
forum: Security
---

### Post by cyberpirate on 2009-02-18
im trying to backup my pc with rsync and i keep getting this error

```

bugs@bunny:~$ rsync /home/bugs/Desktop/Thems /media/disk/ubuntu_2-18-09
skipping directory Thems
bugs@bunny:~$ 

```

i just settled 4 this folder on my desktop to test 4 now. y is it skipping my directory?

---

### Post by mikewu on 2009-02-18
Use the -r flag to copy directories recursively. It should go into the folder and copy it.

---

### Post by cyberpirate on 2009-02-18
thx that worked!

---

### Post by hyper_ch on 2009-02-20
I'd use the "-a" flag.

---

