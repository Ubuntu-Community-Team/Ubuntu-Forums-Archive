---
title: "Minimising hard disk writes"
date: 2007-08-11
forum: Server Platforms
---

### Post by cookfromfrozen on 2007-08-11
Hi
I am running an old machine in my bedroom  with Ubuntu 6.06 as a server.

The HDD is quite noisy when it writes (the "grinding" type noise), so until I am able to afford a big compact flash to create a noiseless setup, I'm stuck with trying to keep hdd writes to a minimum.

I have used the "commit=" option in fstab and set it to 7200 ( 2 hours).  I know this increases the risk of data loss, but it seems to reduce how often stuff is pushed out to the hdd.

I have also got rid as far as possible any of the default cronjobs, such as updatedb (which I never use, and can update manually anyhow).

Is there anything else I can do to help minimum hdd writes?

thank you!

---

### Post by olejorgen on 2007-08-11
Use **noatime** (at least if you use ext3 (or ext2 (?)) under options in /etc/fstab.

This turns off recoding of last file access time. (which normally forces a write each time a file is openened, even if the file only is read)

---

