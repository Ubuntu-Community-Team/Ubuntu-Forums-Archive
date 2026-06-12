---
title: "absolute beginner: manually creating encrypted swap to overcome install bug"
date: 2008-07-21
forum: Security
---

### Post by addison3 on 2008-07-21
Okay, so apparently there's a bug in the linux installer that causes everything to freeze when trying to create an encrypted swap partition with a random key (as detailed at [https://bugs.launchpad.net/ubuntu/+bug/231451](https://bugs.launchpad.net/ubuntu/+bug/231451)). I'm new to linux and everything, but that something significant like this hasn't been fixed yet surprised me, it seems like creating an encrypted swap would be a commonly used feature.

Anyway, does anyone know what the best way is to get around this if I eventually want to get full filesystem encryption, including my swap? What I've gathered is that the only way to go is to skip making the encrypted swap during the install and create it manually later, not something I'm looking forward to being a complete newbie to linux.

Would anyone like to explain how to go about the process of manually creating the encrypted swap after the install, or could someone post a walkthrough to this for absolute beginners? Keep in mind I have no prior experience in linux and having to do command line type stuff kinda scares me.

Thanks in advance

---

### Post by addison3 on 2008-07-21
^bump

---

### Post by Titan8990 on 2008-07-21
Why do you see a need to encrypt an area that doesn't store files?

---

### Post by addison3 on 2008-07-22
I was under the impression encrypting the swap was just part of full filesystem encryption. If my laptop gets swiped, I wouldn't want to have to worry about whether there was anything senstive leftover on the swap partition.

---

### Post by hyper_ch on 2008-07-22
> **Titan8990 said:**
> Why do you see a need to encrypt an area that doesn't store files?
It does store files ;)

> **addison3 said:**
> I'm new to linux and everything, but that something significant like this hasn't been fixed yet surprised me,
Why significant?

> **addison3 said:**
> it seems like creating an encrypted swap would be a commonly used feature.
Only among those who encrypt their whole system for which you require the altenate or server install cd - which is done by many people...


> **addison3 said:**
> Anyway, does anyone know what the best way is to get around this if I eventually want to get full filesystem encryption, including my swap? What I've gathered is that the only way to go is to skip making the encrypted swap during the install and create it manually later, not something I'm looking forward to being a complete newbie to linux.
That's the way... I wrote a little howto... I'm sure you can find it.

---

### Post by addison3 on 2008-07-22
I think I found it right here: [http://ubuntuforums.org/showthread.php?t=848691](http://ubuntuforums.org/showthread.php?t=848691). Thanks a lot, that looks like a big help, and I'm sure all the screengrabs will help me out.

---

