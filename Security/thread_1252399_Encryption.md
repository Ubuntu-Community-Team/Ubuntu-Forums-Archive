---
title: "Encryption"
date: 2009-08-28
forum: Security
---

### Post by Sin@Sin-Sacrifice on 2009-08-28
So I have some personal docs that I want to keep to myself and I decided to encrypt them with a password using ubuntu´s built in encryption tools. I did that on another kernel of which escapes me but anyway... decided to do some house cleaning since I got my new system. I used my old hdd for backups and such for both linux and windows so fat32 fs was used. Well when I transfered my files from ext3 to the fat32 drive it became ¨unencrypted?¨ I could access the files no matter the privileges of the user and also from windows theres no sign of the encryption I performed. It worked when I was using the original OS with the other OSs access but now that I moved it... no good. I want to encrypt them for a reason and if I can just move them to another drive to access them then there´s no point to encryption. What´s the deal here?

---

### Post by Moop on 2009-08-28
I don't know what the deal is with Ubuntu built in encryption but you can use Truecrypt to create a container to hold all your private docs. The container can be moved and even renamed and still remain encrypted until you use your password to see the contents. 

Truecrypt has a deb for Ubuntu on their download page.

---

### Post by Sin@Sin-Sacrifice on 2009-08-28
Hey, thanks Moop. I´ll give that a shot. I was thinking it had something to do with the key or keyring but none of it made sense in my head. Moving on to another enabler.

---

### Post by Agent ME on 2009-08-29
In a terminal, enter "sudo apt-get install ecryptfs-utils; ecryptfs-setup-private". Leave settings at default (blank line) if you don't understand what they are - the only important thing is to enter your password as instructed.

You will then have a folder under your home folder called "Private". Anything placed in there is encrypted automatically and private to your user account.

---

### Post by sasho_zl on 2009-08-29
You can encrypt the documents one by one or as a archive with the command:
```
gpg --symmetric --cipher-algo TWOFISH filename
```

---

### Post by HermanAB on 2009-08-29
Uhmmm, so you opened (decrypted) the encrypted drive, then copied its contents to another (plain text) disk and now you are wondering why the copies are not encrypted anymore?  Just stop and think about that for a moment...
:)

---

### Post by shaneh on 2009-08-30
I'm with Herman on this one. It sounds like you decrypted it when you backed it up. If you give more details someone might be able to help you determine where it went wrong.

If you copied over encrypted files, it shouldn't be readable without decrypting. I was just playing with it on my system and the default right click->Encrypt... dialog creates a file with the .pgp extension which can't be read without the key. However, this process doesn't delete the original file which sits in the same place, unencrypted. So if you copy the original, you're still copying an unencrypted file around. 

The same is true of TrueCrypt container files, but maybe you'll find that easier to use. I'd read up on it more, ask questions, figure out exactly what's going on. Encryption is one of those things where the best programs in the world aren't going to help with a flawed implementation. Also, you don't want to get stuck with encrypted files that you can't decrypt yourself, either.

---

### Post by hackertarget on 2009-08-30
I would also recommend having a look at TrueCrypt.

If you are then using both windows and ubuntu you can move the encrypted container between Operating systems - just have TrueCrypt installed on both systems.

** AFAIK - I have not tried TrueCrypt under Windows.

---

### Post by grashdur on 2009-08-30
With regard to hackertarget's comment on Truecrypt: I've used it a lot both in Ubuntu and Windows, and it works great both ways, with the encrypted vaults totally interoperable between the OS's. Truecrypt is wonderful and easy to use.

My only real gripe with Truecrypt is that it won't let you access an encrypted volume elsewhere on a network, at least in Linux.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
Not sure why you guys would think I "decrypted" it before transfer. It's not the drive that was encrypted... just packs of folders. I moved those packs that were still encrypted. Truecrypt worked... thanks to all for the other helpful replies.

---

