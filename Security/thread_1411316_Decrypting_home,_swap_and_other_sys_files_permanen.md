---
title: "Decrypting home, swap and other sys files permanently after installing"
date: 2010-02-19
forum: Security
---

### Post by karolinger on 2010-02-19
Hello, I don't know if this is the correct forum category as I'm a beginner. Anyway...

According to [this document]("https://help.ubuntu.com/community/EncryptedHome") when ones selects the option to "require a password to log in and decrypt your home directory" while running the installation many parts of ubuntu are encrypted as home and swap. Is there a way to decrypt these permanently? In other words, is there a way to undo this setup option?

Thanks,
Carlos

PS: I didn't forget my username and password or something like that. I just wasn't aware of the caveats of using this option.

---

### Post by Agent ME on 2010-02-20
> **karolinger said:**
> PS: I didn't forget my username and password or something like that. I just wasn't aware of the caveats of using this option.
What caveats are those? The only one I've heard of people running into is that for ssh passwordless logins, the public key has to be placed outside of home or as a passthrough unencrypted file instead of simply in ~/.ssh2.

---

### Post by adam814 on 2010-02-21
I can't think of too many good ways to go about it personally.  Probably the best is to back up your data to external media of some sort and re-format any encrypted partition(s) and copy your files back from the backup.

---

### Post by karolinger on 2010-02-24
> **Agent ME said:**
> What caveats are those? The only one I've heard of people running into is that for ssh passwordless logins, the public key has to be placed outside of home or as a passthrough unencrypted file instead of simply in ~/.ssh2.

They are included in the document linked on my first post

---

### Post by karolinger on 2010-02-24
> **adam814 said:**
> I can't think of too many good ways to go about it personally.  Probably the best is to back up your data to external media of some sort and re-format any encrypted partition(s) and copy your files back from the backup.

I reinstalled ubuntu without the option to encrypt home

Thanks,
Carlos

---

### Post by Kangarooo on 2010-08-14
So how to decrypt home? i now want to use autologin witch doesnt work if home is encrypted.
Is decryption different in 10.10 then in other versions?

---

### Post by eyerouge on 2011-01-03
[http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reinst](http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reinst)

---

