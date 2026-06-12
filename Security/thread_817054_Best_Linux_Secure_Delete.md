---
title: "Best Linux Secure Delete?"
date: 2008-06-03
forum: Security
---

### Post by Nullack on 2008-06-03
What is the best secure delete program I can get for Linux? Dont mind if it is command line or GUI. Im after a robust and secure way to shred files, without actually shredding the disc into little bits on the floor :)

---

### Post by barnex on 2008-06-03
You can just use the standard shred program for this.
```

$ shred file

```
cheers.

---

### Post by cdenley on 2008-06-03
You can use the shred command, which simply overwrites the file with random data repeatedly. The secure-delete package has tools that use a better algorithm. However, the built-in erase function on modern hard drives does a better job than simple data overwrites, but this erases the entire disk. This can be done with the "--security-erase-enhanced" option when using hdparm.

I think many people go too far trying to erase data. Probably the only people who might be able to recover data that has been overwritten with a few passes of random data is a government intelligence agency.

---

### Post by ajgreeny on 2008-06-03
Though if you read the shred manual you will see that it is not guaranteed to do the job as well as you might have hoped.

QUOTE
 In the case of ext3 file systems, the  above  disclaimer  applies  (and
       shred  is  thus  of  limited  effectiveness) only in data=journal mode,
       which journals file data in addition to just  metadata.   In  both  the
       data=ordered  (default) and data=writeback modes, shred works as usual.
       Ext3 journaling modes can  be  changed  by  adding  the  data=something
       option  to  the  mount  options  for  a  particular  file system in the
       /etc/fstab file, as documented in the mount man page (man mount).

       In addition, file system backups and remote mirrors may contain  copies
       of the file that cannot be removed, and that will allow a shredded file
       to be recovered later.

---

### Post by HermanAB on 2008-06-03
The best way to do secure delete is to encrypt the partition and forget the key. Any other way is insecure.

---

### Post by cdenley on 2008-06-03
> 
In both the data=ordered (default) and data=writeback modes, shred works as usual.


data=ordered is the default. Unless the user adds data=journal to their /etc/fstab file, "shred works as usual".

---

### Post by ajgreeny on 2008-06-03
Thanks for that info, not that I use shred, but it's good to learn more.

---

### Post by Biochem on 2008-06-03
Unfortunately, I suggest you have a look at this:
[http://ubuntuforums.org/showpost.php?p=4407671&postcount=10](http://ubuntuforums.org/showpost.php?p=4407671&postcount=10)

I followed those instructions with shred on a default ext3 (so data=ordered) and managed to acces the shreded data.

---

### Post by aysiu on 2008-06-03
> **HermanAB said:**
> The best way to do secure delete is to encrypt the partition and forget the key. Any other way is insecure.
That's precisely why I don't encrypt my drive!

My general understanding of how deletions work is that "deleted" files aren't deleted *per se*, just allocated as "available to be overwritten." Is that understanding correct?

If it is, would it be possible to securely delete all your files by deleting them and then filling up all the free space on your drive with multiple copies of some binary file (not a text file)?

---

### Post by cdenley on 2008-06-03
> **aysiu said:**
> That's precisely why I don't encrypt my drive!

My general understanding of how deletions work is that "deleted" files aren't deleted *per se*, just allocated as "available to be overwritten." Is that understanding correct?

If it is, would it be possible to securely delete all your files by deleting them and then filling up all the free space on your drive with multiple copies of some binary file (not a text file)?

How the deletion actually works depends on the filesystem. With ext3, I believe all the meta-data containing stuff like file path/name and permissions are zeroed out. The data from the file is left intact, because it would be a waste of resources/time to overwrite unused data with nulls or random bytes. I think all filesystems will leave the file's actual data. Even if you delete the file, it can still be recovered using photorec from the testdisk package. You can prevent this by simply overwriting the entire file with nulls (zeros).
```

shred -z -u -n 0 /path/to/file

```
This is a fast way to make it impossible for almost anyone to recover it. However, if someone were to actually open your hard drive, and examine it's platters with an electron microscope or something, it is theoretically possible to determine or guess what the data used to be since a 0 bit isn't physically a true zero, just close to zero. The bits closest to 0 used to be a 0, and the rest were 1's. This is why sensitive data should be overwritten with random data multiple times.

The built-in erase function I mentioned earlier is better because it erases the edges of the tracks. The edges could be more vulnerable to data recovery because the drives' heads may have shifted slightly since the data was written.

---

### Post by HalPomeranz on 2008-06-03
> **cdenley said:**
> With ext3, I believe all the meta-data containing stuff like file path/name and permissions are zeroed out. The data from the file is left intact, because it would be a waste of resources/time to overwrite unused data with nulls or random bytes.

This is correct.  ext3 zeroes the inode information before returning the inode to the free list.  ext2 does not.  Neither file system overwrites the data blocks on delete, so you have to use something like shred or srm to clobber the data *before* you delete the file.

---

### Post by Darris on 2011-06-22
> **cdenley said:**
> How the deletion actually works depends on the filesystem. With ext3, I believe all the meta-data containing stuff like file path/name and permissions are zeroed out. The data from the file is left intact, because it would be a waste of resources/time to overwrite unused data with nulls or random bytes. I think all filesystems will leave the file's actual data. Even if you delete the file, it can still be recovered using photorec from the testdisk package. You can prevent this by simply overwriting the entire file with nulls (zeros).
```

shred -z -u -n 0 /path/to/file

```This is a fast way to make it impossible for almost anyone to recover it. However, if someone were to actually open your hard drive, and examine it's platters with an electron microscope or something, it is theoretically possible to determine or guess what the data used to be since a 0 bit isn't physically a true zero, just close to zero. The bits closest to 0 used to be a 0, and the rest were 1's. This is why sensitive data should be overwritten with random data multiple times.

The built-in erase function I mentioned earlier is better because it erases the edges of the tracks. The edges could be more vulnerable to data recovery because the drives' heads may have shifted slightly since the data was written.

 Doing that would take so long that after a couple days they might have a single megabyte of information.  That method of data retrieval was made way back in the 90's. Most hard drives write more precisely now, so it would be incredibly hard to exploit the edge of an overwritten byte.

---

