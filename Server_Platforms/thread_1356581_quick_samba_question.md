---
title: "quick samba question"
date: 2009-12-16
forum: Server Platforms
---

### Post by mendo on 2009-12-16
i have setup an ubuntu server on my home network to share files and a printer.  the main shared disk is FAT formatted.

my question is this:

can i use samba to share one folder to user1 and user2, allowing user1 to write and user2 to only read?  if so, how?

thanks.

---

### Post by KeLa on 2009-12-16
Try to thinker with "Valid users" and "Write list" parameters.

---

### Post by mendo on 2009-12-18
write list did the trick.  thanks.

---

