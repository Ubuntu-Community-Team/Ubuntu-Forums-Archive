---
title: "SFILL on NTFS"
date: 2010-02-19
forum: Security
---

### Post by zerofool2005 on 2010-02-19
I want to boot a livecd and use fill to fill my HDD with random data to do secure deletion of files.

But im wondering. Does SFILL work on NTFS partitions?

---

### Post by rookcifer on 2010-02-19
Boot from any Linux live CD, open a root terminal and run:
```

dd if=/dev/zero of=/dev/sda conv=notrunc
```

This will write zeroes to the whole drive.  If you want to use a pseudorandom pattern, use this instead:

```
dd if=/dev/urandom of=/dev/sda conv=notrunc
```

One pass is enough to completely wipe any modern hard disk.  And be sure to substitute "/dev/sda" with the correct HD.

The shred utility can also be used if you prefer (it does the same thing):
```

shred -vf -n 1 /dev/sda
```

This will fill the disk with a "random" pattern.  If you want to add a pass of zeroes, simply add the "-z" flag to the above command.

---

