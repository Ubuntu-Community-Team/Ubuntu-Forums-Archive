---
title: "encrypting existing LVM2"
date: 2011-08-24
forum: Security
---

### Post by [pl]ice on 2011-08-24
Hi,

I got 8TB of LVM2 (not full though). I was wondering if there is a way to encrypt it without wiping the partition and starting all over LVM.
I can make a backup of the data, but the spare media is a issue.

Any advise?

thanks

---

### Post by bodhi.zazen on 2011-08-24
> **'[pl]ice said:**
> Hi,

I got 8TB of LVM2 (not full though). I was wondering if there is a way to encrypt it without wiping the partition and starting all over LVM.
I can make a backup of the data, but the spare media is a issue.

Any advise?

thanks

No, the process of encrypting includes writing random data to the disk and will thus over write your data.

Your only other option would be to use ecryptfs ( cryptkeeper is a graphical front end) to set up a crypt and move your data.

---

### Post by [pl]ice on 2011-08-24
> **bodhi.zazen said:**
> No, the process of encrypting includes writing random data to the disk and will thus over write your data.

Your only other option would be to use ecryptfs ( cryptkeeper is a graphical front end) to set up a crypt and move your data.

Looks like i better start looking for some spare media . . .

thanks.

---

