---
title: "rsync - Backup only changed blocks?"
date: 2010-08-10
forum: Server Platforms
---

### Post by qrwe on 2010-08-10
Hello,

I'm going to make a nightly backup copy from one server to another, using rsync. If I have a sufficiently large file, say 4+ GB or so, I'm not interested in copying the whole file if only a small change has been made.
Can rsync detect small changes on block level and backup only those if needed? Thanks for any help!

---

### Post by andrewc6l on 2010-08-10
Yes, it does what you want by default. The rsync algorithm is documented here:
[http://www.samba.org/rsync/tech_report/](http://www.samba.org/rsync/tech_report/)

It breaks the file into sections (not necessarily disk blocks) and sends only the changes based on cryptographic hashes of the sections.

---

### Post by qrwe on 2010-08-12
Pretty cool, I say. Huge thanks for the link!
Cheers.

---

