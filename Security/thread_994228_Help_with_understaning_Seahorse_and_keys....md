---
title: "Help with understaning Seahorse and keys..."
date: 2008-11-26
forum: Security
---

### Post by samwisefoxburr on 2008-11-26
Hello, I've started to mess around with Seahorse to encrypt some of my files that I am planning on backing up onto a DVD and need some help with how this all works so I don't end up not being able to access my data.  To start off, I'm not planning on sharing any of my data with friends or anything like that, I'm just using it to encrypt files that are stored locally.

Anyway, I'm a bit confused as to how the decryption works.  I tested out decrypting one of my files on another computer of mine running Ubuntu, but it says it doesn't have the decryption key.  I tried importing the public key and that didn't work, either.  How would I go about backing the key up when I upgrade or reinstall Ubuntu so I don't end up with files I can't decrypt?.  Do I just back up the .gnupg folder and and copy it back over after reinstalling, or is it more complicated than that?

Thanks!

---

### Post by twisted_steel on 2008-11-27
Yes, backing up your .gnupg folder should be sufficient.  If you want to decrypt any files encrypted with that key on another computer, you will need your private key.  It is important that the files are backed up somewhere safe because you will be out of luck if you completely lose the keys.  There is a quick overview on protecting your private key here: [http://www.gnupg.org/gph/en/manual.html#AEN513](http://www.gnupg.org/gph/en/manual.html#AEN513)

---

### Post by Sarmacid on 2008-11-28
The public key can be shared with anyone and it's used to encrypt. The private key is for yourself only and is used to decrypt.

I know seahorse has an option to backup your keyring, so you might rather want to do that instead of manually backing up the folder, and also if you'd rather not deal with the keys, gpg has also an option to just encrypt using password.

---

### Post by lobner on 2008-12-11
> **Sarmacid said:**
> and also if you'd rather not deal with the keys, gpg has also an option to just encrypt using password.

How and where do I do that?

Because I was hoping I might encrypt the .gnupg folder with a password just, and then back it up somewhere safe. Then I could go on with my key-encryption.

---

### Post by Sarmacid on 2008-12-11
To encrypt
```
pgp -c file
```
You should get a .pgp file after that

To decrypt
```
gpg -d file.gpg > file
```

This method doesn't work with folders though. I'm not sure if there's a command to do it directly with gpg, or you could just tar the folder.

---

