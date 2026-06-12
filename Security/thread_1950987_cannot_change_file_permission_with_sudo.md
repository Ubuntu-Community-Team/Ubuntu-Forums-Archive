---
title: "cannot change file permission with sudo"
date: 2012-04-01
forum: Security
---

### Post by syed.rakib.al.hasan on 2012-04-01
```

# cd my_project
# ls -l
-rwxr-xr-x 1 rakib root   421 2012-04-02 03:28 setup.py
# sudo chmod 777 setup.py
-rwxr-xr-x 1 rakib root   421 2012-04-02 03:28 setup.py
# sudo chmod 666 setup.py
-rwxr-xr-x 1 rakib root   421 2012-04-02 03:28 setup.py
```

no matter what chmod i perform, the permission of setup.py are not changing

---

### Post by dfreer on 2012-04-01
Is it immutable?
```
lsattr ./setup.py
```

---

### Post by modorf on 2012-04-02
please try:

```

sudo chmod 0777 setup.py

```

---

### Post by dfreer on 2012-04-02
> **modorf said:**
> please try:

```

sudo chmod 0777 setup.py

```

That would be the same command that the OP has already tried. Based on the output, no suid or guid bits have been set.

---

### Post by Karlchen on 2012-04-02
Is it imaginable that the folder* my_project* and as a consequence the file *setup.py* in it have been stored on a filesystem which does not support Linux access rights, like e.g. FAT32 or NTFS?

Karl

---

### Post by kevdog on 2012-04-02
If you login in as root, you should then be able to change the file properties:

sudo su

---

### Post by dfreer on 2012-04-02
> **Karlchen said:**
> Is it imaginable that the folder* my_project* and as a consequence the file *setup.py* in it have been stored on a filesystem which does not support Linux access rights, like e.g. FAT32 or NTFS?

Karl

It could also be that the filesystem has been mounted read only, will have to wait for OP to confirm.

---

