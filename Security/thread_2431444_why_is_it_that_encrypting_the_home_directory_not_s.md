---
title: "why is it that encrypting the home directory not straightforward"
date: 2019-11-16
forum: Security
---

### Post by ronjjjg8885 on 2019-11-16
i know it isn't stable but want to know why?

thanks!!!

---

### Post by TheFu on 2019-11-19
A beginning Unix book will explain the login process step-by-step.  There are specific steps that need to happen and at a certain point, specific files in the login userid's HOME must be accessible.  There are many different ways to "login", so ensuring that all of those work when each of those projects know nothing about any specific Ubuntu encryption implementation is a non-trivial problem.

I was never able to figure out a good network backup method for systems that had individual HOME directory encryption.  Also, the encrypted filenames were leaking metadata about their contents, so while the encryption was good-enough for keeping your little brother from seeing stuff, it wasn't sufficient for preventing an organized attacker.

Now add in all the issues with OS release upgrades and ensuring post-upgrade that an encrypted HOME still worked ...  that's a receipt for problems with millions of unhappy end-users locked out of their files.

I'm amazed they pulled it off for as many years as they did.

---

