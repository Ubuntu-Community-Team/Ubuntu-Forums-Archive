---
title: "finding SUID and SGID files"
date: 2011-05-14
forum: Security
---

### Post by desire.linux on 2011-05-14
I've seen some really complex commands to find such files on your system.

Like these:
```

# find / -perm -4000 -o -perm -2000 -exec ls -ldb {} \; >> SUID_files.txt
# find / -type f \( -perm -004000 -o -perm -002000 \) -exec ls -lg {} \; 2>/dev/null >suidfiles.txt

```But what about these:
```

$ cd /
$ sudo find . -perm 2000 > ~/output_SGID.txt
$ sudo find . -perm 4000 > ~/output_SUID.txt
$ sudo find . -perm 6000 > ~/output_SGUID.txt

```The latter are much easier to understand and remember, but are they doing the same job?

---

### Post by Lars Noodén on 2011-05-15
These will work:

```

 find / -type f \( -perm +4000 -o -perm +2000 \) -exec ls -l {} \; 2>/dev/null

 find / -type f \( -perm +4000 -o -perm +2000 \) -print 2>/dev/null


```

---

### Post by desire.linux on 2011-05-15
Are you saying that my second samples doesn't work? They seem to work anyway.

---

### Post by Lars Noodén on 2011-05-16
I expect all three should work.

---

