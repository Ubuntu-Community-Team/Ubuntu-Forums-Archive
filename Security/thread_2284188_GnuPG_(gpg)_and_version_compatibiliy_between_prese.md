---
title: "GnuPG (gpg) and version compatibiliy between present and upcoming Ubuntu Releases."
date: 2015-06-27
forum: Security
---

### Post by mikodo on 2015-06-27
As part of my backup plans, I want to use gpg, for a symmetric cipher. Probably, just the Cast5 algorithm that comes installed with gpg by default now.

Background:

I was using the bcrypt encryption utility, for a small sensitive data file of 20 kb, in Xubuntu 12.04. After installing Xubuntu 14.04, the newer version of bcrypt with it, wouldn't open the older bcypt version encrypted file from my data, that Xubuntu 12.04 had used. I installed the 12.04 bcrypt version in 14.04 and opened it.

Question:

Might the same thing happen with gpg between Ubuntu releases, as happened with the bcrypt encryption utility?

[https://www.gnupg.org/documentation/manpage.html](https://www.gnupg.org/documentation/manpage.html)

---

### Post by matt_symes on 2015-06-29
Hi

It's always possible that gpg cyphers could change between versions or even break due to bugs in the implementation. This has happened a number of times over the years with different encrypted system.

Check the changelog from version to version and backup the ISO used to encrypt your files along with the encrypted files.

Kind regards

---

### Post by mikodo on 2015-06-29
> **matt_symes said:**
> Hi

It's always possible that gpg cyphers could change between versions or even break due to bugs in the implementation. This has happened a number of times over the years with different encrypted system.

Check the changelog from version to version and backup the ISO used to encrypt your files along with the encrypted files.

Kind regards

Good to know.

Thank you.

---

