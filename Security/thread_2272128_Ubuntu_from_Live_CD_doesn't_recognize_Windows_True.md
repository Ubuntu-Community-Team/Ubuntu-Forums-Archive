---
title: "Ubuntu from Live CD doesn't recognize Windows TrueCrypt volumes"
date: 2015-04-04
forum: Security
---

### Post by peter1897 on 2015-04-04
I am using Windows 7 on my laptop and i have some partitions encrypted with TrueCtypt, but when i try to use Ubuntu Live CD it doesn't see the encrypted partitions. Is there a way to decrypt and mount the truecrypt partitions, that are encrypted under Windows, using Ubuntu Live?

---

### Post by bardo2 on 2015-04-05
did you install and use tcplay?
its been long time since i used truecrypt, but i recall it used to work just fine years ago. maybe at the time i used a custom installed truecrypt (cannot remember)

---

### Post by SuperFreak on 2015-04-05
Veracrypts latest version will decrypt Truecrypt containers/partitions   [https://veracrypt.codeplex.com/]("https://veracrypt.codeplex.com/")
You could install that in a Live session and decrypt your partition

---

### Post by bardo2 on 2015-04-05
i have just tested inside a virtual machine: the linux version of truecrypt 7.1a just happens to work on trusty :)

you are aware that later versions should be considered insecure, right?

---

