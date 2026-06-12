---
title: "Looking for help setting up encryption - after the fact"
date: 2013-12-23
forum: Security
---

### Post by Hungry Man on 2013-12-23
I would like to know what options I have for encryption on Ubuntu.I'm using Ubuntu 13.04 and Windows 8.1 in dual boot.I want to encrypt *as much* of Ubuntu 13.04 as possible.What are the options for this?

---

### Post by bashiergui on 2013-12-23
Do you want it all to be encrypted at rest and then decrypted at login? Or keep parts encrypted all the time and only decrypt when you mount what you need?

---

### Post by Hungry Man on 2013-12-23
I would like it to be decrypted at login. Similar to how Bitlocker on Windows works.

---

### Post by Dave_L on 2013-12-24
Here are some options.

If you only want to encrypt your home directory, you can do that with ecryptfs-migrate-home:

[http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html](http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html)
[http://manpages.ubuntu.com/manpages/raring/en/man8/ecryptfs-migrate-home.8.html](http://manpages.ubuntu.com/manpages/raring/en/man8/ecryptfs-migrate-home.8.html)

If you want to encrypt everything, I think that would require reinstallation:

[http://askubuntu.com/questions/61617/migration-from-ecryptfs-to-full-disk-encryption](http://askubuntu.com/questions/61617/migration-from-ecryptfs-to-full-disk-encryption)

---

