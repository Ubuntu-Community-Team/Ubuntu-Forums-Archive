---
title: "[SOLVED] compressing data before backing up to tape?"
date: 2007-12-04
forum: Server Platforms
---

### Post by tr333 on 2007-12-04
I have a backup script that writes a folder to the tape drive, and it's running from a cronjob.  Should i compress the data with bzip2 (tar 'j' option) while writing to the tape, or would that just take more time than is necessary?

Also, i noticed both /dev/st0 and /dev/nst0 as device nodes for the tape drive.  Which is the correct one to use?

---

### Post by HermanAB on 2007-12-04
Most all tape drives have compression built in - read the manual.

However, in the odd event that it doesn't, you can use gzip:
# tar -zcvf /dev/tape /whatever

The 'z' switch enables gzip.

Cheers,

Herman

---

### Post by tr333 on 2007-12-06
Thanks for the tip.  I found the answer to the st0/nst0 question at [http://www.redhat.com/archives/rhl-list/2005-February/msg04563.html](http://www.redhat.com/archives/rhl-list/2005-February/msg04563.html).

---

