---
title: "How to retrieve content of tape drive"
date: 2009-03-27
forum: Server Platforms
---

### Post by tensai_999 on 2009-03-27
we have a backup tape from our old unix server (SCO 5), the backup was done using the dbdump command... what am i trying to do is to retrieve this content into a server currently running ubuntu server 8.04... some suggested to use mt and tar, but in my case the drive is recognized and mt can be executed but the tar could not be executed... the error is that its not a tar or gzip file...
in the terminal it display something like the "the child has died"

Any infos or link that could help me out to retrieve this tape.
the tape drive is a sony-250V.

---

### Post by Anthon on 2009-03-27
To save wear and tear on the tape and if you have the discspace to restore the full tape I would first do something like:
  dd if=/dev/mt0 of=/var/tmp/tape.img
After that use:
  file /var/tmp/tape.img
to see if that can make sense of the file format and go from there.
If the tape doesn't fit you can still copy the first few hundred bytes using dd and a bytecount.

---

