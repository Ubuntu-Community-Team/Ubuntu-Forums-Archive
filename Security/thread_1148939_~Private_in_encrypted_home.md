---
title: "~/Private in encrypted home"
date: 2009-05-04
forum: Security
---

### Post by teddks on 2009-05-04
I have an encrypted $HOME directory, but I would like to have the same ~/Private capabilities I had in 8.10, preferably with a different algorithm than AES, like Serpent.

I understand I can modify the algorithm by modifying the ecryptfs-setup-private script, but I'm concerned about clobbering files in ~/.ecryptfs and with if pam_ecryptfs will mount both $HOME and ~/Private.

I would prefer if replies stayed pertinent to this help request and how to implement it, and were not about questioning my motivation for doing this.

---

### Post by bodhi.zazen on 2009-05-04
You should back up your files, on a separate encrypted file system if you wish (do not save the encrypted file), make a new crypt ( $HOME ) and then transfer the files back.

---

### Post by teddks on 2009-05-05
> **bodhi.zazen said:**
> You should back up your files, on a separate encrypted file system if you wish (do not save the encrypted file), make a new crypt ( $HOME ) and then transfer the files back.

I don't want to change the $HOME I currently have, I just want another encrypted ~/Private directory inside it, for the things I want "more" secure than the rest of my $HOME.

---

