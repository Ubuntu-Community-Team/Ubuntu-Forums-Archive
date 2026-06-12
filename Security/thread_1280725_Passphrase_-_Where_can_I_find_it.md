---
title: "Passphrase - Where can I find it?"
date: 2009-10-02
forum: Security
---

### Post by ID_ on 2009-10-02
Hey guys ubuntu 9.04 freaked out on me. I am trying to get my data off my home folder. Long story short the folder is encrypted. Where can i find my passphrase so i can access the drive?

---

### Post by undecim on 2009-10-02
With ecryptfs, your encryption key is encrypted with your login password and stored in ~/.ecryptfs/wrapped-passphrase

use the command "ecryptfs-unwrap-passphrase /path/to/wrapped/passphrase" to get your encryption key

---

### Post by ID_ on 2009-10-02
can i do this in recovery mode in root. and what would be /path/to/wrapped/passphrase i am locked out of the system. xorg crashed and i cannot recover.

---

