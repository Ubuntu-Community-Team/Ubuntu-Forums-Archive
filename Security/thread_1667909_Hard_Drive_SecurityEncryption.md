---
title: "Hard Drive Security/Encryption"
date: 2011-01-15
forum: Security
---

### Post by r0llingthund on 2011-01-15
Hello all
I was recently given an external hard drive (500 gigs) and was planning to set off 100 gigs as a encrypted, password protected partition and well I was wondering the best way of going about this process. I am thinking about using TrueCrypt, But before I did I wanted some opinions about it. Thanks

p.s. I run Ubuntu 10.04

---

### Post by kn0w-b1nary on 2011-01-15
you can also use disk utility to do that (so i hear, i haven't tried it)
TrueCrypt is nice, but i personally just use an encrypted LVM, though installation is a lot slower. If you really have sensitive data, don't just use encrypted home, as you can hack root, change pass, and then get in to your files.

Hope this helps!

---

### Post by Dave_L on 2011-01-15
> **kn0w-b1nary said:**
> don't just use encrypted home, as you can hack root, change pass, and then get in to your files

Assuming you're talking about ecryptfs, that is not correct.  Logging in as root will not enable the files to be decrypted.

---

### Post by r0llingthund on 2011-01-15
Sorry should of been more specific:

I use both Windows 7 and Ubuntu (>.> I know i should drop windows)

I am looking for some way to encrypt part of the hard drive so that before anyone can access the data (Admin, Root, or some regular user) they have to have a password. Also i would like to be able to use it freely between Ubuntu and Windows. 

I have really never done anything with encryption before, so your talking to some one with only the information  he has been able to find via Google.

---

### Post by kn0w-b1nary on 2011-01-15
> **Dave_L said:**
> Assuming you're talking about ecryptfs, that is not correct.  Logging in as root will not enable the files to be decrypted.

I'm talking about the option in the installer to encrypt the home directory.
The encryption there is based on the users password, if root changes that users password, then he would be able to log in as that user and view their data.

---

### Post by rookcifer on 2011-01-15
> **r0llingthund said:**
> Hello all
I was recently given an external hard drive (500 gigs) and was planning to set off 100 gigs as a encrypted, password protected partition and well I was wondering the best way of going about this process. I am thinking about using TrueCrypt, But before I did I wanted some opinions about it. Thanks

p.s. I run Ubuntu 10.04

Two options:

1) Truecrypt

2) Dm-crypt/LUKS

Truecrypt is what I use for "container" encryption or back-up drive encryption.  For whole disk encryption, the only option on Linux is dm-crypt/LUKS, but WDE is not your concern here, so that's a moot point.

The benefits of Truecrypt is the headers are encrypted, thus not revealing to an attacker what algorithm/hash, etc. the drive is encrypted with.  They can't really even prove it's an encrypted container/drive (unless they assume all random data is encryption, which is a fair assumption).  Plus TC has the hidden volume feature and an easy to use GUI.  It also has AES-NI support and multi-cpu support (LUKS doesn't have threading support).

My vote is TC, but either should work well and be secure.  TC is easier to setup, especially for someone not comfortable with the command line.

EDIT:  Just saw you need to access this on Windows 7 too.  In that case, you should definitely got with TC.  DM-crypt/LUKS can be accessed on Windows via FreeOFTE, but when I tried to set that up on my Windows 7 partition, it wouldn't work due to the driver signing feature in Windows 7.  You can work around it, but it is a major PITA.  Just use TC.

---

### Post by FuturePilot on 2011-01-15
> **kn0w-b1nary said:**
> I'm talking about the option in the installer to encrypt the home directory.
The encryption there is based on the users password, if root changes that users password, then he would be able to log in as that user and view their data.

This is not true at all.
Please read
[http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html]("http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html")


Changing the user's password as root might allow you to log in as them but you won't be able to access their data since it will still be encrypted using the fekek from the original password.

---

### Post by bodhi.zazen on 2011-01-16
> **kn0w-b1nary said:**
> I'm talking about the option in the installer to encrypt the home directory.
The encryption there is based on the users password, if root changes that users password, then he would be able to log in as that user and view their data.

As has been pointed out , this is incorrect information.

root can change a users password, but if so, the new password would not decrypt the encrypted data.

root could, however, possible crack the password (john the ripper style) depending on the quality of the password.

---

### Post by kn0w-b1nary on 2011-01-16
to all who showed me my mistake, thank you.

I'll double check nxt time b4 i post.

my apologies for posting incorrect information](*,)

---

