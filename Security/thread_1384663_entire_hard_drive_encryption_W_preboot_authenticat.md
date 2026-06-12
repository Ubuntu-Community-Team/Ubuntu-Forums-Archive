---
title: "entire hard drive encryption W/ preboot authentication"
date: 2010-01-18
forum: Security
---

### Post by shadow120 on 2010-01-18
looking for a program that will let me encrypt everything so that you need preboot authentication like you can do with truecrypt in windows thanks

---

### Post by michaelzap on 2010-01-18
> **shadow120 said:**
> looking for a program that will let me encrypt everything so that you need preboot authentication like you can do with truecrypt in windows thanks

The easiest way is to use LUKS encryption, which you can choose when you install Ubuntu if you use the alternate (not Live) CD. It's considerably more difficult to setup after installation. I prefer LUKS to using encrypted home directories for single-user systems, but each method has its advantages and disadvantages.

---

### Post by adam814 on 2010-01-18
If you're familiar with and like TrueCrypt it is available for Linux as well.  I haven't actually used it for whole disk/partition encryption, but I have for files and it works for that.

LUKS is definitely the more standard/integrated Ubuntu way to encrypt, but I'll agree it's not the easiest thing to set up post-install.

---

### Post by shadow120 on 2010-01-18
the TrueCrypt for linux cant encrypt the entire hard drive just the home folder because it dosent have the preboot authentication

---

### Post by bodhi.zazen on 2010-01-18
> **shadow120 said:**
> the TrueCrypt for linux cant encrypt the entire hard drive just the home folder because it dosent have the preboot authentication

Your question was answered in the second post of this thread by michaelzap.

> **michaelzap said:**
> The easiest way is to use LUKS encryption, which you can choose when you install Ubuntu if you use the alternate (not Live) CD. It's considerably more difficult to setup after installation. I prefer LUKS to using encrypted home directories for single-user systems, but each method has its advantages and disadvantages.

If you need instructions, see this link :

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

yes it is written for 8.04 but it is the same with 8.10 , 9.04, and 9.10

=)

---

