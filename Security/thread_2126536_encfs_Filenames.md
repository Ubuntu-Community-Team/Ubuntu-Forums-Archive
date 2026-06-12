---
title: "encfs Filenames"
date: 2013-03-17
forum: Security
---

### Post by kvdbreem on 2013-03-17
Good morning,
I've been wondering about this for quite some time and had little luck googling it, so maybe someone here knows the answer.  My question is this.  If the files stored in a file system encrypted using encfs each correspond to a file that can be decrypted on the decrypted view (mountpoint) then doesn't that mean that just knowing the file name or even some portion of the contents of a single file in the encrypted file system would render the encryption virtually useless since an attacker could just work out the encryption key from that bit of plaintext?

---

### Post by kevdog on 2013-03-17
Your correct.  Having knowledge of whatever is in the encrypted container in no way renders the container itself less penetrable.

---

### Post by Stonecold1995 on 2013-03-19
Knowing the plaintext and encrypted result does not impact the effectiveness of the encryption much.  Even if an attacker knows the original plaintext and the encrypted file, he has no way of knowing the original key used.  Of course, knowing the plaintext DOES defeat encryption for that file, obviously.

Also, how would knowing the filenames allow someone to get the encryption key?  He may be able to infer what is contained in the file, but couldn't know for sure.

If you are planning on encrypting a partition, I suggest you instead use LUKS or TrueCrypt.  Those two encrypt *everything*, including the filenames.

---

