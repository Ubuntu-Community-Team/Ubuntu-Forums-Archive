---
title: "PGP and Truecrypt"
date: 2009-08-17
forum: Security
---

### Post by NoctisCaelum on 2009-08-17
Hi, I already had done some searches about.. something like "PGP vs TrueCrypt", but I can't see anything clear.. and like here in ubuntu foruns the people is "more wise" I would like to hear what you think, I'm using truecrypt but I want to know what is it better, and why ?

thanks in advance

---

### Post by rookcifer on 2009-08-17
> **NoctisCaelum said:**
> Hi, I already had done some searches about.. something like "PGP vs TrueCrypt", but I can't see anything clear.. and like here in ubuntu foruns the people is "more wise" I would like to hear what you think, I'm using truecrypt but I want to know what is it better, and why ?

thanks in advance

Use Dm-Crypt/LUKS.

---

### Post by credobyte on 2009-08-17
PGP - file encryption
TrueCrypt - partition encryption

---

### Post by Agent ME on 2009-08-17
Each has different uses.

Truecrypt creates a transparently encrypted filesystem.
*You save your file directly into the encrypted filesystem. The file is automatically encrypted and unaccessible when the encrypted filesystem hasn't had the password entered and mounted.*
(There are several similar systems. I prefer using EcryptFS.)

GPG is for encrypting specific files. It's great for email. (It can also do signatures.)
[i][list][*]You save your file. You then use gpg to make an encrypted copy of the file. Then you can transfer or store this file however you want.
[*]You type up an email, and encrypt it to the recipient's public key so that only the intended recipient can decrypt it.
[*]You type up an email, and (maybe after encrypting it as above) digitally sign it, to prove that it was you (the owner of the corresponding private key) who wrote it.[/list][/i]

---

### Post by HermanAB on 2009-08-17
Howdy,

If you need to encrypt a disk partition, then you can use Truecrypt or LUKS.  If you want to encrypt files and email, then use GPG or PGP.

LUKS has more features than Truecrypt, for example multiple passwords, but the Truecrypt wizards are more polished.  Truecrypt works on both Linux and Windows.  LUKS works on Linux and can work with FreeOTFE on Windows.

Since the LUKS documentation is a bit lacking, I made my own wizards here:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)
[http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

In terms of security, they all seem to be good.

---

### Post by sasho_zl on 2009-08-18
Also Truecrypt has a very bad license. The Fedora project issued a statement while back that this software should not be used at all costs.
You have GPG installed on your system. To encrypt a file or archive just type in the terminal: **gpg --symmetric --cipher-algo TWOFISH filename** 
This will encrypt a file with a password of your choice.

---

### Post by kevdog on 2009-08-18
Why do you recommend the TWOFISH cipher algorithm?  Even Bruce Scheiner -- the creator of twocrypt -- suggests AES should be utilized. (AES256).  According to Bruce, its more battle tested. (Unless you believe in conspiracy)!:confused:

---

### Post by rookcifer on 2009-08-18
> **kevdog said:**
> Why do you recommend the TWOFISH cipher algorithm?  Even Bruce Scheiner -- the creator of twocrypt -- suggests AES should be utilized. (AES256).  According to Bruce, its more battle tested. (Unless you believe in conspiracy)!:confused:

It doesn't matter -- they are all about the same (AES, Twofish, Serpent, etc.).  In fact, AES-256 just had a major round of attacks performed against it.  You can read about it on Bruce's blog.

---

### Post by sasho_zl on 2009-08-18
> **rookcifer said:**
> It doesn't matter -- they are all about the same (AES, Twofish, Serpent, etc.).  In fact, AES-256 just had a major round of attacks performed against it.  You can read about it on Bruce's blog.
The attacks are still far away from practical use braking of the AES cipher but as Mr. Schneier sais "Attacks can only get better and not worse.".
Just to add to my previous post - all the supported algorithms can be seen by typing [B]
gpg --version[/B] in the terminal.

---

### Post by Agent ME on 2009-08-18
Oh, there's also a difference between Truecrypt/EcryptFS and LUKS.

LUKS and a few similar things encrypt the whole harddrive (or partition). On bootup, your system will ask for the encryption password in order to decrypt itself. This isn't very useful for a multi-user system (unless it's left on the entire time) as every user would need to know the password to turn it on. The encryption wouldn't stop anyone who knew the password from peaking at the files.

EcryptFS and Truecrypt are better for per-user encryption. Each user can have their own private encrypted area, which no one else needs to know the key to.

I prefer using EcryptFS, as it's nicely integrated with Ubuntu. Once I log on, it uses my account password to decrypt the key so it can immediately and automatically make my encrypted files available to me. I can make nearly all of my user's hidden config directories symlinks to point to folders in my Private/ directory to keep everything encrypted.

---

### Post by kevdog on 2009-08-19
> **rookcifer said:**
> It doesn't matter -- they are all about the same (AES, Twofish, Serpent, etc.).  In fact, AES-256 just had a major round of attacks performed against it.  You can read about it on Bruce's blog.

Interesting read, however the recommendations from the article were not to switch to Twofish but use AES128 and not 256.  Others suggested switching to Serpent, however this algorithm isn't included within the OpenGPG standard and thus not part of the software.

---

### Post by rookcifer on 2009-08-19
> **kevdog said:**
> Interesting read, however the recommendations from the article were not to switch to Twofish but use AES128 and not 256.  Others suggested switching to Serpent, however this algorithm isn't included within the OpenGPG standard and thus not part of the software.

You can utilize serpent via dm-crypt/LUKS (alternate install CD).

---

### Post by NoctisCaelum on 2009-08-19
ok, thanks for the help.. but I have another question =/ what is the difference between using AES or AES-Twofish-Serpent ? the last one is more secure ? 3 keys at the same time ? how it works ? I tried to find info with truecrypt foruns and google but I didn't get anywhere =/

---

### Post by kevdog on 2009-08-19
AES-Twofish-Serpent -- The data is encypted with one of the algorithms, and then the encrypted data is further encrypted with another algorithm.  AES is the gold standard or most studied symmetric cipher in the world.  Twofish is known for speed, but even its author Bruce Scheiner admits it hasn't been as rigorously tested.  I don't have as much experience as Serpent, but it was a finalist for the AES competition.  Its known to be very secure but computationally slow.

---

### Post by NoctisCaelum on 2009-08-22
ok, thanks for the help everyone =)

---

