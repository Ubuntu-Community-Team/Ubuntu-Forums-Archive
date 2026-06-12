---
title: "backing up encrypted /Private directory"
date: 2010-03-16
forum: Security
---

### Post by m4lte on 2010-03-16
hi,

I just started using ecryptfs to maintain an encrypted /Private directory.

I regularly back up my data to an external hard drive. I'm wondering how to handle the encrypted data. Obviously I also want it to be encrypted on my external HDD. Is it possible to back up the encrypted data? Or do I have to decrypt it, move it and encrypt it again? (I'm new to the topic of encryption)

What do you suggest?

---

### Post by uRock on 2010-03-17
If you are just copying and pasting, I would think that the copy would be encrypted also. This is only theoretical. I don't know for sure.

---

### Post by Agent ME on 2010-03-17
If you access files in the Private folder, you'll get the decrypted versions. If you access the .Private folder, you'll the encrypted files.

---

### Post by m4lte on 2010-03-18
So if I backup the encrypted version from the folder /.Private, could I also decrypt the files on another machine (given the passphrase of course) or do I need to have the files in their original location?

And if I can decrypt them from at another location, how exactly do I do that? I want to make sure that I know how to recover my backup on another machine if my computer breaks.

thanks!

---

### Post by ushills on 2010-03-19
I tried this and for some reason could not access .Private while logged in.  Fine when not logged in, i think this is a known issue but someone will confirm.

---

