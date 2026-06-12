---
title: "forgot encryption hash"
date: 2010-10-22
forum: Security
---

### Post by frogotronic on 2010-10-22
Like an idiot I threw out my encryption hash that I wrote down when I installed my system.  Any way to recover it?  Nothing is wrong with my system, just thought I should write it down.

- CH    :guitar:

---

### Post by FuturePilot on 2010-10-22
```
ecryptfs-unwrap-passphrase /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase
```

---

### Post by frogotronic on 2010-10-23
Thanks!  Worked - marking as solved.

   :guitar:

---

### Post by karthick87 on 2010-10-26
I am using ubuntu 10.04,and i din get any encryption hash code during installation..What is the use of knowing that hash code..?

---

### Post by OpSecShellshock on 2010-10-26
> **getyourkarthick said:**
> I am using ubuntu 10.04,and i din get any encryption hash code during installation..What is the use of knowing that hash code..?

If you didn't select the option to encrypt your home directory when you installed, then you wouldn't have seen it. The purpose of displaying the hash code after installation is so it can be recorded for use in case something goes wrong later (like a forgotten or changed user password).

---

### Post by karthick87 on 2010-10-26
So is it possible to encrypt my home directory now,i mean after installing ubuntu..

---

### Post by FuturePilot on 2010-10-26
> **getyourkarthick said:**
> So is it possible to encrypt my home directory now,i mean after installing ubuntu..

The manual way [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

or the scripted way

```
ecryptfs-migrate-home
```

---

### Post by karthick87 on 2010-10-26
What is the need for encrypting home directory..?

---

### Post by frogotronic on 2011-01-20
> **karthick87 said:**
> What is the need for encrypting home directory..?

In case your laptop gets stolen and the thieves want your credit card #'s & personal info.

If they are crackers (good hackers) they'll bust it anyway, but if they're run-of-the-mill-thieves, your info will be safe.

- CH

---

### Post by frogotronic on 2011-01-20
deleted double post

---

### Post by DZ* on 2011-01-22
> **cement_head said:**
> If they are crackers (good hackers) they'll bust it anyway

I'd think the default encryption algorithm in ecryptfs ensures that a strong password should keep them busy for a very long time. NSA classifies AES-128 as appropriate for protection of "secret level" documents.

---

### Post by frogotronic on 2011-01-22
> **DZ* said:**
> I'd think the default encryption algorithm in ecryptfs ensures that a strong password should keep them busy for a very long time. NSA classifies AES-128 as appropriate for protection of "secret level" documents.

:popcorn:

---

