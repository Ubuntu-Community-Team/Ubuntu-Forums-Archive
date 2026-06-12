---
title: "Encrypted documents with the lost Private Key?"
date: 2009-10-06
forum: Security
---

### Post by Xsoldier2000 on 2009-10-06
Hello all, I have Seahorse working, and encrypting files. Of course I didn't correctly back up my Private Key when it was time to reformat my hard drive. I exported my public key to an .asc which I now know won't work.

My real question is, how can I decrypt the files I had encrypted using this now lost private key? I did back up my ~/.gnupg folder. I placed those backed up files in the new home directory and imported my private key (doesn't help, I know) and even re-created a new private key with the exact name email addy, and password as my lost private key. yet when I right click on a blah.pdf.pgp file and select 'Open with Decrypt Key' I get the Decryption Failed.

Have I lost all those documents that I encrypted with the lost Private Key?

---

### Post by kevdog on 2009-10-07
Bottom Line on this one:

If you lose the Private key = You are Screwed!

That's pretty much the end of the discussion!

---

### Post by Xsoldier2000 on 2009-10-07
> **kevdog said:**
> Bottom Line on this one:

If you lose the Private key = You are Screwed!

That's pretty much the end of the discussion!

I was really hoping you wouldn't say that. Even backing up my .gnupg folder won't help me?

Anyway to brute-force hack them open?

---

### Post by psusi on 2009-10-07
That's kind of the point of encrypting them in the first place isn't it?  To make sure that nobody can open them without your private key.  So if you don't have your private key... well, what does logic suggest?

This is why you always keep a backup of your private key on a different medium and stored in a different location.

---

### Post by kevdog on 2009-10-07
I'm not saying PGP/GPG is unbreakable, but unless you have a supercomputer and about 10 years of spare time, I think you are screwed. There are multiple ways to keep a backup key.  Transfer to another medium, print it out on paper -- paperkey.  Without these methods, you are kind of out of luck.  Unless you didn't happen to do any symmetric encryption option when you signed these did you?

---

### Post by Xsoldier2000 on 2009-10-07
Sigh...My next step would be to run recovery software on the external drive where I kept all my documents.

 I encrypted it with Jaunty's Seahorse (where it created a .pgp file next to the .pdf files, in essence creating an encrypted copy.) I then proceeded to delete the original .pdf documents.

,X..  <-- keeps fingers crossed


yayyyy for stupidity!

---

### Post by Sarmacid on 2009-10-07
I also had that problem when I backed up my .gnupg folder, however you can probably use the command line gpg.

As for me, luckily I also kept another backup of the keys I did using the passwords and encryption keys application and after opening it, everything was back to normal.

---

### Post by Xsoldier2000 on 2009-10-07
> **Sarmacid said:**
> I also had that problem when I backed up my .gnupg folder, however you can probably use the command line gpg.


Not sure what you mean by the command line .gpg... can you elaborate?

---

### Post by Sarmacid on 2009-10-08
Open up a terminal and type ```
gpg --help
```You will see the command's usage.

---

### Post by kkady32 on 2009-11-16
i played today with gpg
when u lose the secret key( ~/.gnupg/secring.gpg) u cann forgot to decrypt
for encrypt a file the best way is to use:
$ gpg --symmetric --cipher-algo TWOFISH file
required only a passphrase

---

