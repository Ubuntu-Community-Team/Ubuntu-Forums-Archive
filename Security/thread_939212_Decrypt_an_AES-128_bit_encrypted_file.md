---
title: "Decrypt an AES-128 bit encrypted file"
date: 2008-10-05
forum: Security
---

### Post by flouran on 2008-10-05
Hi,
I have an AES-128 bit encrypted file, and I was wondering how I could decrypt it (I have the password for it) under Ubuntu 8.04 LTS.

Basically, are there any packages to help me decrypt the encrypted file (in either AES-128 bit or AES-256 bit, etc)?

Any help would be greatly appreciated,
Flouran

---

### Post by snova on 2008-10-05
It depends. What program did you use to encrypt it? Different programs will use different file formats, and not necessarily flat binary encrypted data.

---

### Post by flouran on 2008-10-05
I used Disk Utility to encrypt it.

---

### Post by snova on 2008-10-05
Well then, use Disk Utility to decrypt it. Chances are no other program will understand its file format.

I've never heard of that program (I haven't heard of many), but if it's a Windows program, use Wine. If it's a Mac OS X program, I have no idea what to do.

---

### Post by kevdog on 2008-10-05
It might be possible to decrypt this with gpg using the symmetric option but I doubt it since the password you undoubtedly chosen was salted and then probably hashed a number of times.  If this process isn't repeated exactly during the decryption phase (for example hash the password 8 times instead of 9) the process is going to fail.

FYI -- gnupg (available on all platforms) is able to encrypt a file with a number of algorithms.  Here is the algorithms currently available:

Cipher: IDEA (S1), 3DES (S2), CAST5 (S3), BLOWFISH (S4), AES (S7), AES192 (S8), AES256 (S9), TWOFISH (S10), CAMELLIA128 (S11), CAMELLIA192 (S12),CAMELLIA256 (S13)

Note that AES(S7) is AES-128 -- but just not explicitly specified.

---

### Post by flouran on 2008-10-05
Kevdog,
What command can I use for your proposed method using gpg?

---

### Post by kevdog on 2008-10-05
Here is a summary of terminal commands I used to decrypt a file named letter:

$ more letter
Test Message

admin@bjpdr10 ~
$ gpg --symmetric --armor --cipher-algo AES256 letter
gpg: WARNING: This version has been built with support for the Camellia cipher.
gpg:          It is for testing only and is NOT for production use!
gpg: WARNING: using insecure memory!
gpg: please see [http://www.gnupg.org/faq.html](http://www.gnupg.org/faq.html) for more information

Note for the above that --armor is only needed if you want the file to be in ASCII format.  Without this, a binary file will be produced.  You can use what ever parameter you want for --cipher-algo

$ more letter.asc
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.10-svn4847 (Cygwin)

jA0ECQMI3HZhXuWaGABg0k4Bbcy0MhSq877goNsqz3Sw4nNRbkyOH2jDAw++8+Fz
7nVur6QDTEMvKUS8XSzHj6XMG+NA0EDGdfzAosMP9CzyCHgqB0WfW01lrwWQfW8=
=qgjs
-----END PGP MESSAGE-----


$ gpg -v -d letter.asc
gpg: WARNING: This version has been built with support for the Camellia cipher.
gpg:          It is for testing only and is NOT for production use!
gpg: WARNING: using insecure memory!
gpg: please see [http://www.gnupg.org/faq.html](http://www.gnupg.org/faq.html) for more information
gpg: armor header: Version: GnuPG v1.4.10-svn4847 (Cygwin)
gpg: AES256 encrypted data
gpg: encrypted with 1 passphrase
gpg: original file name='letter'

If you dont need a verbose output you can do the following:
gpg -d letter.asc

Hopefully that helps.

---

