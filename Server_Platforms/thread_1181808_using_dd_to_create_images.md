---
title: "using dd to create images"
date: 2009-06-08
forum: Server Platforms
---

### Post by druca on 2009-06-08
Hi, 

I have a raid 10 linux server with about 6 hard disks. Can I use dd to throw it all into one image file, then restore it back to all six hard disks? 

thanks,
drew

---

### Post by ian dobson on 2009-06-08
Hi,

Yes. For example if your array is called md0 then the following command will copy the entire array:-

dd if=/dev/md0 of=output.file bs=1k

This will just create an exact copy of the array to the file "output.file" in your current directory. Only try this when booted in safe mode/when the array is not mounted.

I've used dd afew times to copy a harddisk to another one then expand the partition/file system to fill the new disk.

Regards
Ian Dobson

---

### Post by druca on 2009-06-08
ok, what if say, I wanted to do that, and then restore it. Could I boot from a live cd and then use nc to capture the restore from the network off another computer and put it back on? If I were to copy the entire md0 array, there needs to be a md0 array to catch it right? Both systems need the exact same configuration in order to restore it or could the configuration be different?

thank you kindly,
drew

---

### Post by ian dobson on 2009-06-08
Hi,

You can do this to pipe the output to nc using :-

dd if=/dev/md0 | nc on the sender and
nc | dd of=/dev/md0  on the receiver

maybe use gzip to compress the output of dd before passing it on to nc.

the option if is input file and of is the output file.

YES the "new" md array needs to be exactly the same as the source.

Regards
Ian Dobson

---

### Post by druca on 2009-06-08
thank you very much, works like a charm!

---

### Post by Polaris96 on 2009-06-08
one question:  RAID 10 is redundant.  why make an entire image?  Not that you necessarily shouldn't but it seems like overkill...

---

### Post by druca on 2009-06-09
Im just following orders lol... :)

---

### Post by windependence on 2009-06-09
It would be faster to use a larger block size, like 4096.

```
bs=4096
```

-Tim

---

### Post by Polaris96 on 2009-06-09
druca - ;)

---

