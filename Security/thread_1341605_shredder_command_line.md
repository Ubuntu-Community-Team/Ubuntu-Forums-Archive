---
title: "shredder command line"
date: 2009-11-29
forum: Security
---

### Post by jonno2009 on 2009-11-29
Hi ... just new here ... I use to have the linux command line to shred files ... can anyone please give me the command line to shred files?
Many thanks ... Jonno

---

### Post by Barriehie on 2009-11-29
> **jonno2009 said:**
> Hi ... just new here ... I use to have the linux command line to shred files ... can anyone please give me the command line to shred files?
Many thanks ... Jonno

You're looking for shred?  Try 'man shred' in the terminal.

Barrie

---

### Post by Agent ME on 2009-11-29
"shred -u somefile" will shred and delete the file. Leaving off the "-u" will cause it to shred the file, but not delete it, causing a file full of random data to be left over.

---

