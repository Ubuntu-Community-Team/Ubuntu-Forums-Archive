---
title: "pubring.gpg vs. pubring.gpg~"
date: 2011-04-12
forum: Security
---

### Post by hazelnusse on 2011-04-12
I am following the GnuPG MiniHowTo here:
[http://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html](http://www.dewinter.com/gnupg_howto/english/GPGMiniHowto.html)

After running gpg --gen-key, I get these files in my ~/.gnupg directory:
-rw-------  1 luke luke 2232 2011-04-12 10:33 pubring.gpg
-rw-------  1 luke luke 2232 2011-04-12 10:27 pubring.gpg~
-rw-------  1 luke luke  600 2011-04-12 10:27 random_seed
-rw-------  1 luke luke 4890 2011-04-12 10:27 secring.gpg
-rw-------  1 luke luke 1280 2011-04-12 10:33 trustdb.gpg

What is the "pubring.gpg~" file?  I cannot find any documentation on it anywhere.   Also, according to all the documentation I read, the result of the gpg --gen-key command should result in a "pubring.gpg.lock" file, but as you can see, this doesn't happen for me.

If anybody could shed light on this, it would be great.

---

### Post by rookcifer on 2011-04-12
Any file with ~ after it is a backup.  Ubuntu/Gnome automatically makes backups of of certain files if they have changed.

---

