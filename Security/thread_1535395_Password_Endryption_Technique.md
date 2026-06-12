---
title: "Password Endryption Technique"
date: 2010-07-20
forum: Security
---

### Post by sajalagarwal on 2010-07-20
Can any one tell me about ubuntu password encryption methods?

I have read that it uses DES and MD5 algos to encrypt.
But DES algo requires a message and a key to encrypt.
key is our password but what is the message?

I donot know about MD5.

Give me links or a small bit of descryption to the encryption techniques used in any of the Linux and the shadowing of password hashes.

if possible the source codes of algos in java,c,c++ may help.

Thanks in advance!

---

### Post by cariboo on 2010-07-20
Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1475892&highlight=password+hash"), it may help.

---

### Post by rookcifer on 2010-07-20
> **sajalagarwal said:**
> Can any one tell me about ubuntu password encryption methods?

I have read that it uses DES and MD5 algos to encrypt.
But DES algo requires a message and a key to encrypt.
key is our password but what is the message?

I donot know about MD5.

Give me links or a small bit of descryption to the encryption techniques used in any of the Linux and the shadowing of password hashes.

if possible the source codes of algos in java,c,c++ may help.

Thanks in advance!

I am not aware of any Linux distros that still use MD5 for password hashing.  MD5 is essentially broken (collisions have been found and demonstrated).  I know that Ubuntu uses a *salted* SHA-512 for its password hashes.  SHA-512 is one of the strongest cryptographically secure hashing functions available today.

As for encryption of the password file, I don't think this actually occurs.  A long time ago DES was used (DES is a block cipher, not a hash function) because there was really not many other options.  What it did was take the password and use it (and the salt) as a key to encrypt 0's.  This is an old-fashioned way of doing things and has been obsoleted by the highly secure hashing functions we have today.

You can read about how to determine which password hashing function is being used by [reading this short explanation.]("https://lists.ubuntu.com/archives/ubuntu-devel/2008-August/026204.html")

---

### Post by anomie on 2010-07-20
[QUOTE=rookcifer]I am not aware of any Linux distros that still use MD5 for password hashing.[/QUOTE]

You'd be surprised. RHEL4 & 5 still use it by default. (I'm sure there are others.) Of course, it can be changed to use sha512.

---

### Post by sajalagarwal on 2010-07-22
I am using ubuntu 10.04.
I have a root account whose hash starts with 
$6$ which means sha512 hashing.
and my another account starts with $1$
which means md5 hashing.
The above two hashes I got by john the ripper software.

The second thing i want to ask is that how these hashes are generated.
Whether they are first encrypted by DES or any algorithm and then hashes are generated or directly the hashes are generated .

If possible supply the **source code** file or link to encryption as well as to hashing algorithm.
If possible give something about blowfish also being used by recent versions opensuse os.

---

### Post by anomie on 2010-07-22
Nothing in your reply indicates that you've read any of the advice already given. 

You're asking questions (I mean making demands) about locating FOSS source code and for advice about publicly documented details.

---

### Post by Bachstelze on 2010-07-22
Never mind.

---

