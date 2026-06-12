---
title: "Truecrypt: Invalid argument"
date: 2009-05-15
forum: Security
---

### Post by omax on 2009-05-15
I created a truecrypt file a while ago, and it always mounted perfect. But now all of a sudden it won't. Why is this?

```
$ truecrypt volume.tc vol/
Enter password for /path/to/volume.tc:
Enter keyfile [none]:
Protect hidden volume? (y=Yes/n=No) [No]:
Error: Invalid argument:
/path/to/volume.tc

```

```
$ file volume.tc
volume.tc: ISO-8859 text, with very long lines, with CRLF line terminators

```

---

### Post by pauna on 2009-05-16
> **omax said:**
> I created a truecrypt file a while ago, and it always mounted perfect. But now all of a sudden it won't. Why is this?
```
$ file volume.tc
volume.tc: ISO-8859 text, with very long lines, with CRLF line terminators

```


Weird... My truecrypt containers are identified by file as "data", not "ISO-8859 text" files. Maybe the volume got somehow corrupted?

---

### Post by omax on 2009-05-17
That's probably the case. Damn, I have some important files in there. Might be some way to recover?

---

### Post by irregardlessly on 2009-05-17
If it is on a spinning drive it may be a drive error... you could try one of the disk recovery tools out there.  The only one I know of is spinrite (grc.com) but there are free tools as well though I have no experience with them.

---

