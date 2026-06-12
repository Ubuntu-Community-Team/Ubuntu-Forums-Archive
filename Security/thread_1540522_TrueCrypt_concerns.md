---
title: "TrueCrypt concerns"
date: 2010-07-27
forum: Security
---

### Post by PHANTOM X on 2010-07-27
I installed truecrypt, but it doesn't seem too work like it did on windows. Usually it asks for the password before the operating system is loaded. For whatever reason it didn't and let me login right away. Is it supposed to do this? Or is it just how it works on Linux?

---

### Post by byStanderone on 2010-07-27
...that depends on what you choosed during the truecrypt install, you might have chosen during its install not to prompt for a password but instead use your login password automatically....hence truecrypt function executes because you are login.

---

### Post by PHANTOM X on 2010-07-27
Nothing in the install asked for anything. Unless you mean the container setup.

---

### Post by bodhi.zazen on 2010-07-27
> **PHANTOM X said:**
> I installed truecrypt, but it doesn't seem too work like it did on windows. Usually it asks for the password before the operating system is loaded. For whatever reason it didn't and let me login right away. Is it supposed to do this? Or is it just how it works on Linux?

If you are wanting to install Ubuntu into an encrypted partition , use the alternate CD, which uses LUKS and not Truecrypt.

[http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml)

The tutorial is written fo r8.04, but the installer and installation process has not changed much.

---

### Post by PHANTOM X on 2010-07-27
Can I boot from a usb stick with this? My drive won't read burn discs.

---

### Post by earthpigg on 2010-07-28
> **PHANTOM X said:**
> Can I boot from a usb stick with this? My drive won't read burn discs.

skimming the article, i don't see any reason why you wouldn't be able to use a usb stick. give it a shot (after backing up your data like normal, of course) and let us know if it doesn't work.

---

### Post by PHANTOM X on 2010-07-28
Will do.:)

By the way, the article mentions the 8.04 LTS, but at [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download) it lists the 10.04 LTS alternative download. Is this similar to 8.04, but newer?

---

### Post by earthpigg on 2010-07-28
yup.

8.04 LTS came out in the _4_th month of 200_8_. 10.04 LTS came out in the _4_th month of 20_10_. Just a newer version.

---

### Post by PHANTOM X on 2010-07-28
Cool.:)

---

### Post by earthpigg on 2010-07-28
it's handy so you don't forget to update grandma's computer before support for the release of Ubuntu on her computer expires.

---

### Post by rookcifer on 2010-07-28
> **PHANTOM X said:**
> I installed truecrypt, but it doesn't seem too work like it did on windows. Usually it asks for the password before the operating system is loaded. For whatever reason it didn't and let me login right away. Is it supposed to do this? Or is it just how it works on Linux?

Truecrypt does not do full disk encryption on Linux. Therefore, what you are asking is impossible.  You should use dm-crypt/LUKS instead.

---

### Post by PHANTOM X on 2010-07-28
Installed and works good.:)

How long does it take to encrypt? Or does fully encrypt at install?

---

### Post by fargle on 2010-07-31
If you installed with LUKS/dm_crypt, then it encrypts as data is added.

---

