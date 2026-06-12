---
title: "IDEA: Permanent Deletion"
date: 2009-07-13
forum: Security
---

### Post by kevdog on 2009-07-13
I can remember many threads in this section addressing the idea of permanent deletions or the use of shred or other such commands in attempts to permanently delete items from the hard disk or other media.  Others have commented that these methods don't really work to well, and in most cases the original data can be recovered.  I'm not sure how feasible these recovery attempts are, however many have sworn to their effectiveness.

Anyway an idea for permanent deletion -- although somewhat more involved -- would be encrypt the data first, making a key that was kept in memory, shred or delete or do whatever you want to delete the data, and then throw away the key.  

Im not sure if this could physically be done however with the actual bits on the disc.  I would want to avoid making temporary files and such as this would pretty much avoid the whole point of the exercise. I'm not even sure if this process is even feasible.

Any ideas.

---

### Post by HermanAB on 2009-07-13
This problem has been solved.  Encrypt your /home and /swap with LUKS.

---

### Post by bodhi.zazen on 2009-07-13
> **kevdog said:**
> I can remember many threads in this section addressing the idea of permanent deletions or the use of shred or other such commands in attempts to permanently delete items from the hard disk or other media.  Others have commented that these methods don't really work to well, and in most cases the original data can be recovered.  I'm not sure how feasible these recovery attempts are, however many have sworn to their effectiveness.

Anyway an idea for permanent deletion -- although somewhat more involved -- would be encrypt the data first, making a key that was kept in memory, shred or delete or do whatever you want to delete the data, and then throw away the key.  

Im not sure if this could physically be done however with the actual bits on the disc.  I would want to avoid making temporary files and such as this would pretty much avoid the whole point of the exercise. I'm not even sure if this process is even feasible.

Any ideas.

Most of those theories have been debunked.

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html") 

[Overwriting Hard Drive Data « SANS Computer Forensics, Investigation, and Response]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/")

---

### Post by cdenley on 2009-07-13
[http://ubuntuforums.org/showpost.php?p=7405704&postcount=3](http://ubuntuforums.org/showpost.php?p=7405704&postcount=3)

---

