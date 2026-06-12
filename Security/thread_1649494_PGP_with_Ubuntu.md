---
title: "PGP with Ubuntu"
date: 2010-12-20
forum: Security
---

### Post by tio_charlie on 2010-12-20
Got PGP 6.5.8 for Linux working with Ubuntu 10.10.  Have not seen any discussion about it on the Internet.

It involved converting two .rpm files to .deb with the **alien **utility and then installing by simply double clicking on the .deb files in the file browser invoking the Ubuntu Software Manager.

I put the two .deb files in a tarball (tar.gz) and would like suggestions as to how to make the tarball available for other Ubuntu users to download.

Thanks for your ideas.

---

### Post by rookcifer on 2010-12-20
My question is why use PGP at all?  GPG already comes with Ubuntu and is fully compliant with the Open-PGP standard.

---

### Post by kevdog on 2010-12-21
PGP 6.5.8 is the last non-paid version of PGP -- I believe you might be referring to the CKT (or cyberknight templates -- or something like this).  The CKT version is not an official PGP version or recognized by PGP.   There is some proprietary code.  According to the discussions on the OpenGPG forum, they suggest not using PGP 6.5.8 since the hash and encryption types have changed greatly since this release -- meaning I dont think 6.5.8 recognizes sha256 or aes256.  At a minimum if you are planning to use encryption, I would think you would want to use these standards since right now there are vulnerabilities with other defaults (I believe the default hash with 6.5.8 is CAST5 if memory serves me right).  Anyway, I would recommend upgrading to openpgp.  Messages encrypted encrypted with pgp should be compatible with gpg so I don't think you lose anything.

---

### Post by tio_charlie on 2010-12-22
Thanks for your ideas and suggestions.

PGP .deb tarball available on request (38KB) inox7 (at) yahoo.com as e-mail attachment.

---

