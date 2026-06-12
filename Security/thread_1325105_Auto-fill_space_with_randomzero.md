---
title: "Auto-fill space with random/zero"
date: 2009-11-13
forum: Security
---

### Post by Grenage on 2009-11-13
Hi there,

This is really just an experiment, and experiments are fun.  I have been toying with the idea of writing a script which fills empty drive space with random data or zeros; the script would be very simple and along the lines of what many people do already:

dd if=/dev/urandom of=bigfile
sync
rm bigfile
sync

That would work fine, but take a long time on a big (but almost empty drive).  Does anyone know if there is a way to automatically fill space that has just been freed with random data?  For example, if I were to delete a file, the space used by that file would be filled with random data immediately after?

All I can come up with at the moment is having a script which accepts the file/folder name as an input, overwrites that file with random data, then removes it.  I would then reference this script rather than rm.

Does anyone else have any ideas?

---

### Post by cdenley on 2009-11-13
You would have to overwrite the data before deleting the file, because once a file is deleted, all data about the file except the file's data itself is zeroed out, so you won't be able to identify its data. By the way, utilities already exist to wipe free space, but they don't work too well with data journaling.
```

sudo apt-get install secure-delete
man sfill

```

---

### Post by Grenage on 2009-11-13
Wonderful, thanks a lot for the secure-delete reference; it pretty much negates the need for a custom script.

Cheers!

---

