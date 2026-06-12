---
title: "Backing up .ecryptfs vs recording mount passphrase"
date: 2011-12-10
forum: Security
---

### Post by graeme_p on 2011-12-10
If I understand how Ubuntu sets up encrypted home directories (i.e. when you add a user), then the mount passphrase is stored wrapped inside /home/.ecryptfs/username/.ecryptfs, and the actual data in /home/.ecryptfs/username/.Private

To unwrap all I need is the login password.

Therefore:

1) If I backup /home/.ecryptfs/username/.ecryptfs I can recover the mount passphrase from there if needed, provided I know the login password. There is no need to record the mount passphrase.

2) If I backup all of /home/.ecryptfs, I will have a complete encrypted backup of all encrypted home directories.

Presumably, I can restore these even after a reinstall, or to move user to another machine. Would that be difficult?

---

### Post by movieman on 2011-12-14
Should work. 

When I had to replace the hard drive in my laptop I just reinstalled on the new drive, put the old drive in an external enclosure, then copied the .ecryptfs directory over to the new drive and fixed up the links. Then I logged in with the same password and all the files were there.

---

### Post by graeme_p on 2011-12-19
Thanks for confirming that. Its what I expected, but uts reassuring to know I understood it correctly.

---

