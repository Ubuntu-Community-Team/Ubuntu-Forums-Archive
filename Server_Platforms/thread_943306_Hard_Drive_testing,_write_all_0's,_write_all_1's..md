---
title: "Hard Drive testing, write all 0's, write all 1's."
date: 2008-10-10
forum: Server Platforms
---

### Post by promodus on 2008-10-10
Maybe you're like me and you want to test a block device.

If you're wanting to fill a hard drive with only 0's and only 1's.
First, install dcfldd, it's just better than dd.
```
sudo apt-get install dcfldd
```

Now, lets say we are using the second SATA drive, being /dev/sdb

to fill a drive with 0's
```
dcfldd if=/dev/zero of=/dev/sdb
```

to fill a drive with 1's
```
tr '\0' '\377' </dev/zero | dcfldd of=/dev/sdb
```

---

### Post by MJN on 2008-10-10
Whilst you haven't defined exactly what you mean by 'test' I think you would be better off using badblocks (or similar) which can 'test' the drive in terms of identifying blocks which don't read the same value as written. It can also use random values to eliminate false positive results.
 
Mathew

---

### Post by promodus on 2008-10-10
```
 if [ $? -eq  0 ]; then echo pass; else echo fail; fi
```


If you have an IO error, your exit status will not be zero!

---

### Post by MJN on 2008-10-10
What if you wrote a '1' but the drive actually stored a '0'?
 
If that's not an IO error...
 
Mathew

---

### Post by promodus on 2008-10-10
> **MJN said:**
> What if you wrote a '1' but the drive actually stored a '0'?
 
If that's not an IO error...
 
Mathew

UDMA should should be doing CRC on the BUS.
SMART should warn you if the disk is having issuse.
SCSI and SAS, I believe will verify the bit is written correctly.

Well if you wrote all '0's, then you'd search for '1's.
```
dcfldd if=/dev/sdb | tr '\377' 'B'
```

If you wrote all '1's you'd look for '0's...
```
dcfldd if=/dev/sdb | tr '\0' 'B'
```

If you see a B, it's a bit flip. 

You could use it test performance, recently I wanted to quickly measure performance over ATAoE, iSCSI and local disks. I am not entirely familiar with boniee++ so i used dd instead.

---

### Post by MJN on 2008-10-10
> **promodus said:**
> SCSI and SAS, I believe will verify the bit is written correctly.
 
Whilst they (and SATA) might have the capability to do so the implementation does not (yet) provide end-to-end assurance. The latest version of the kernel (2.6.27 - released today as it happens!) now supports integrity at the block layer but there is still no support for monitoring it in any current userland application (or filesystem but this isn't applicable with dd) so you're still none the wiser - until you come to read and compare the stored bit which you weren't doing.
 
I think you're missing my underlying point though... perhaps it's my fault for not making it clear enough. Notwithstanding the fact that you haven't defined what your 'test' actually is I am recommending that you use the purpose-built tools that already exist, particularly when you have something like badblocks available which does the job very, very, well. Sure, roll your own solution for kicks but you need to make yourself aware of the shortcomings of whatever you come up with - the results of a test mean nothing if you don't know what is, and isn't, actually being tested.
 
Mathew

---

### Post by caljohnsmith on 2008-10-10
> **promodus said:**
> 
to fill a drive with 1's
```
tr '\0' '\377' </dev/zero | dcfldd of=/dev/sdb
```
How about more simply:
```
sudo dcfldd [COLOR="Blue"]pattern=FF[/COLOR] of=/dev/sdb
```
That will also write all ones to drive sdb. :)

---

### Post by promodus on 2008-10-10
> **caljohnsmith said:**
> How about more simply:
```
sudo dcfldd [COLOR="Blue"]pattern=FF[/COLOR] of=/dev/sdb
```
That will also write all ones to drive sdb. :)

Awesome!

---

### Post by Krupski on 2008-10-11
> **promodus said:**
> Maybe you're like me and you want to test a block device.

If I wanted to test a hard drive, I would use a manufacturer's utility.

One thing in drive testing is that you want native error correction turned off (which drive test utilities do).

"Testing" a drive that's correcting itself on the fly doesn't give you an accurate picture.  :)

---

### Post by Krupski on 2008-10-11
> **promodus said:**
> 
If you're wanting to fill a hard drive with only 0's and only 1's.
First, install dcfldd, it's just better than dd.


Thanks! That's an awesome version of dd.

After I installed it, I made a copy of the file and named it "ddd" and also copied the man page with the name "ddd" because the original name is SO hard to remember! :)

---

### Post by promodus on 2008-10-11
The manufacturers utility is best for testing a single drive; be it warranty or whatever.

If you have tens, hundreds or even thousands of machines... :-\"

---

