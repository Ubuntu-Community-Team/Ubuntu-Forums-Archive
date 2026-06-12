---
title: "Security of /tmp and GPG encrypted files"
date: 2013-08-04
forum: Security
---

### Post by MadsRC on 2013-08-04
I've recently moved to GPG for encrpyting my personal password database.  What I do is I copy my encrypted file to my filesystem (It resides on my fileserver, which does do snapshots == I could end up with a snapshot of my unencrypted file If I decrypt it on the fileserver/NFS share) and decrypt it. When I'm done with it I delete it using "shred -u filename" to securely delete it.  Now, I was thinking that instead of putting it on my local filesystem (With the risk of forgetting to delete the decrypted file and the encrypted file before powering down the machine), I could put the encrypted file in the /tmp directory and decrypt it there. This way the file is never written to disk and if I forget to shred it, it isn't the end of the world as it would be gone 10 seconds after powering down. From what I understand sticky-bit is set on files in /tmp so only the owner can read them (Besides I'm the only user of this machine) - I'm not terribly afraid of root being ableto read it, as he wold be able to do so also in my home directory.  Anyone see any caveats in storing the encrypted and decrypted file in my /tmp directory? - Cause I can't really find any...

---

### Post by kevdog on 2013-08-04
I'm no expert here, however couldn't /tmp also refer to swap space?  Swap could also be a partition on your drive.  And aren't the contents of /tmp maintained between reboots?

---

### Post by MadsRC on 2013-08-04
Actually, my bad. Doesn't seem like /tmp is tmpfs in my system.  What I did instead was to create a folder named "ram" in my home directory and mounted that through fstab as a tmpfs. That would be in the RAM. - But you are right, It could be written to SWAP...

---

### Post by calltheninja on 2013-08-04
It might be worth checking out Keepass or TrueCrypt as a way to solve this problem.

---

