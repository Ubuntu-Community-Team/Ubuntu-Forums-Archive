---
title: "why encrypt the system partition?"
date: 2023-06-22
forum: Security
---

### Post by Skaperen on 2023-06-22
i was just reading a thread where someone wanted to encrypt the system partition.  is this to hide password files?  user lists?  guard against root kits?

when you boot up, you would enter your encryption pass phrase and bring your system up exposing your system partition to everyone on your system.  maybe all you really gain is the ability to obscure your data from hardware thieves.

i do not believe i am someone that world wide national intelligence agencies would have an interest in.  so i don't need to make my system so strong that it blocks even them.  not that i could really accomplish that.  my worry is hacker kid thieves.  of course certain kinds of data could be of interest to others, but this is generally worked on in databases which can have their own security.  of course, i don't put databases on system partitions.  maybe on /home/data or just /data.

i once wanted to do a full drive encryption.  then a system with 3 separate drives got me to rethink what i am doing and re-addressing the thought chain of what kind of encryption is needed, now on individual storage devices.

my latest idea is to have a clear system that can boot up all the way without any prompt for an encryption pass phrase.  thus, i'm not letting thieves get the idea there is any data of value to others (like bank account access) on it.  the first drive would be a complete system (Ubuntu Linux) that is fully usable.  the 2nd drive would be a rescue drive (because it is only 120G) and also not encrypted.  the 3rd drive is where the encryption will be.  after it is mounted (whole drive encryption) then it can be substituted for usual mounts to effectively be running on the encrypted storage device.  the evil maid would need to know how this work to take control.  but, like i said, above, i doubt i am that big of a target.  that, or i have my real "system" in my pocket at all times.

discussion?

---

### Post by aljames2 on 2023-06-23
Interesting approach.  Physical control is a valuable piece of the equation.  I wonder if hardware keys like a Yubikey would thwart an evil maid type of threat.  We use them at work for all logins.

LUKS alone should be fine of you have a good password.  I think auto unlocking at boot-up defeats the purpose if the goal is to protect sensitive data.  If someone breaks into your home and steals that laptop or desktop box, LUKS is useless if its configured to auto unlock with the power switch.

My LUKS unlock password is about 50 strange characters long, saved in an encrypted password manager (KeyPass).  Its more work but use it on the storage where the sensitive stuff is.  Perhaps not everyones computer in the house needs this, but there is likely a need somewhere.

---

### Post by CharlesA on 2023-06-23
My drives are encrypted because I'd rather have encrypted data on a drive in the event it needs to be RMA'd, gets damaged somehow, or gets stolen.

I also encrypt my offsite backups for the same reason.

It does nothing while the machine is running and the drives are mounted, but that isn't an attack vector I am concerned with.

With that said.. I don't see anything wrong with having an encrypted data drive, but it's trivial to tell if a drive is holding an encrypted file system or not, so if anything, it's security via obscurity.

---

### Post by Rubi1200 on 2023-06-23
General question:

does the average home user really need to encrypt either the drive or partitions?

If one is not working with sensitive data of any kind, is encryption really necessary?

Don't get me wrong, privacy is important to me and I certainly would not like to think that anyone can access my data freely.

Are there tools out there that can be used to encrypt, for example, certain folders only?

---

### Post by Dennis N on 2023-06-23
> Are there tools out there that can be used to encrypt, for example, certain folders only?
Sure. You could use **gpg** to encrypt files or folders, either by using the terminal or by installing the seahorse-nautilus extension for Files to automate the task.

```
[dmn@Kayleigh ~]$ gpg --version
gpg (GnuPG) 2.2.41
libgcrypt 1.10.2-unknown
Copyright (C) 2022 g10 Code GmbH
License GNU GPL-3.0-or-later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Supported algorithms:
Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```

---

### Post by oldfred on 2023-06-23
I believe in Pareto, better known as the 80/20 rule. 
[https://en.wikipedia.org/wiki/Pareto_principle](https://en.wikipedia.org/wiki/Pareto_principle)
Originally used to study economy of Italy. 
Used in Sales, manufacturing, inventory and many other places.

So i believe only 20% (approx) of my data is valuable enough to encrypt. So I have one encrypted partition. 
But this is for desktop system that is inside my home and not out & about where system could be stolen. 
I otherwise try to have good security on system, and do not put data into cloud.

---

### Post by TheFu on 2023-06-23
An unencrypted OS can be modified by pulling the SSD/HDD, connecting to another system and you'd likely never know.

If it is encrypted, any modification would likely be impossible or just be to wipe the storage, since they wouldn't be able to mount it for modification, assuming LUKS with a sufficiently random, long, unlock passphrase.

I think all portable computing devices should be using encrypted storage.  Tablets, phones, laptops, USB-storage, since the entire point of being portable is that it can be easily moved ... or lost or stolen while in transit.

For the same reason, using automatic logins on these devices is a no-no too.  Same for bio-metrics as the sole way to authenticate.  Not allowed.  When traveling to new cities, we ask people to lower the lockout period to 5 minutes. When they are at home, I think some use 30 minutes and some probably have a bluetooth device that prevents lockouts when they are home.  At work, if we found a phone or workstation unlocked without the owner nearby, we'd send a dumb email to the entire group from it. Embarrassment is a good habit-changing method, I've found.  Of course, I was on the receiving end a few times too. ;)

**Update:**
When someone says they have nothing to hide or nothing sensitive, I usually ask them for 20 minutes of access to their computer. After all, they have nothing to hide.  

Seems everyone has something they'd rather not be public and if you aren't, I suspect you aren't telling the truth.  

If you've used the computer for online shopping, the credentials for that account could be cached in multiple places on the system.  Logged into your bank?  You have nothing to hide, right?

And your portable devices like smartphones, laptops, tablets are even worse.  People put all sorts of things on those devices and have automatic logins to external services enabled, because it is convenient.  So certainly, you wouldn't mind if someone took over your email account(s) and access everything they could using those, right?  Think about all the "I've forgotten my password" links that will send an email to the account on record.

We all have something to hide. Everyone.

---

### Post by CharlesA on 2023-06-24
> **Rubi1200 said:**
> General question:

does the average home user really need to encrypt either the drive or partitions?

If one is not working with sensitive data of any kind, is encryption really necessary?

Don't get me wrong, privacy is important to me and I certainly would not like to think that anyone can access my data freely.

Are there tools out there that can be used to encrypt, for example, certain folders only?

That all depends on what you are storing on your machine. Do you have tax records or other stuff that has PII on it? Either encrypt it or store it on an encrypted device.

There are tools out there to do per file encryption but it won't be transparent to the user like full disk encryption is, once the drive is unlocked.

> **oldfred said:**
> 
So i believe only 20% (approx) of my data is valuable enough to encrypt. So I have one encrypted partition. 
But this is for desktop system that is inside my home and not out & about where system could be stolen. 
I otherwise try to have good security on system, and do not put data into cloud.

You are probably right. I don't put much into the cloud outside of my offsite backups and those are encrypted by the application I use and sent via SSH to the cloud.

> **TheFu said:**
> An unencrypted OS can be modified by pulling the SSD/HDD, connecting to another system and you'd likely never know.

If it is encrypted, any modification would likely be impossible or just be to wipe the storage, since they wouldn't be able to mount it for modification, assuming LUKS with a sufficiently random, long, unlock passphrase.

I think all portable computing devices should be using encrypted storage.  Tablets, phones, laptops, USB-storage, since the entire point of being portable is that it can be easily moved ... or lost or stolen while in transit.

For the same reason, using automatic logins on these devices is a no-no too.  Same for bio-metrics as the sole way to authenticate.  Not allowed.  When traveling to new cities, we ask people to lower the lockout period to 5 minutes. When they are at home, I think some use 30 minutes and some probably have a bluetooth device that prevents lockouts when they are home.  At work, if we found a phone or workstation unlocked without the owner nearby, we'd send a dumb email to the entire group from it. Embarrassment is a good habit-changing method, I've found.  Of course, I was on the receiving end a few times too. ;)

My work has a policy where the machines lock after 10 minutes and they require the drives to be encrypted even when someone is using a desktop. This is just a layer of security. It does make it harder to recover if hardware fails, but that's why you have a recovery key or passphrase saved elsewhere.

---

### Post by C.S.Cameron on 2023-06-29
> **Rubi1200 said:**
> 

Are there tools out there that can be used to encrypt, for example, certain folders only?

**P7ZIP**, (7Zip) can be used to encrypt files and folders to &#8220;AES-256&#8221;.

---

### Post by Rubi1200 on 2023-06-29
> **C.S.Cameron said:**
> **P7ZIP**, (7Zip) can be used to encrypt files and folders.
Thanks!

---

### Post by TheFu on 2023-06-29
> **C.S.Cameron said:**
> **P7ZIP**, (7Zip) can be used to encrypt files and folders to “AES-256”.

If you need compatibility with other OS versions of ZIP, then PeaZIP is the only one on Linux that I know. It isn't in repos. Seems there isn't really a ZIP standard, so implementations can be incompatible, resulting in a .zip file that someone else cannot open.

---

### Post by donald187 on 2023-06-29
> **Rubi1200 said:**
> General question:

does the average home user really need to encrypt either the drive or partitions?

If one is not working with sensitive data of any kind, is encryption really necessary?

Don't get me wrong, privacy is important to me and I certainly would not like to think that anyone can access my data freely.

Are there tools out there that can be used to encrypt, for example, certain folders only?

I used gocryptfs once to create an encrypted folder.  Then one time I lost my head :) and went back to Windows.  I transferred my Documents including that encrypted folder.  And of course the encrypted folder disappeared!

```
$ apt show gocryptfs
Package: gocryptfs
Version: 1.8.0-1build1
Built-Using: golang-1.17 (= 1.17.3-1ubuntu1), golang-github-hanwen-go-fuse (= 2.0.3-1), golang-github-jacobsa-crypto (= 0.0~git20190317.9f44e2d+dfsg1-4), golang-github-rfjakob-eme (= 1.1.1-1), golang-github-sabhiram-go-gitignore (= 1.0.2-2), golang-go.crypto (= 1:0.0~git20210817.32db794-1), golang-golang-x-sync (= 0.0~git20210220.036812b-1), golang-golang-x-sys (= 0.0~git20211117.dee7805-1), golang-golang-x-term (= 0.0~git20210615.6886f2d-1)
Priority: extra
Section: universe/devel
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Go Packaging Team <pkg-go-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 9,142 kB
Depends: libfuse2, libc6 (>= 2.34), libssl3 (>= 3.0.0~~alpha1)
Homepage: https://github.com/rfjakob/gocryptfs
Download-Size: 1,927 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: Encrypted overlay filesystem written in Go
 gocryptfs is built on top of the excellent go-fuse
 (https://github.com/hanwen/go-fuse) FUSE library and its
 LoopbackFileSystem API.
 .
 This project was inspired by EncFS and strives to fix its
 security issues while providing good performance (benchmarks
 (https://nuetzlich.net/gocryptfs/comparison/#performance)).
 .
 For details on the security of gocryptfs see the Security
 (https://nuetzlich.net/gocryptfs/security/) design document.

```

---

