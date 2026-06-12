---
title: "Is it possible to take back my decision to encrypt my home folder?"
date: 2011-05-20
forum: Security
---

### Post by MelodiesonMusic on 2011-05-20
When I reinstalled ubuntu I chose to encrypt my home folder (something that i've never done before) but now that I know it doesn't really make a difference i'd like to decrypt it because the .encryptfs folder is taking up so much space i'm getting notifications every time I log in.

---

### Post by CharlesA on 2011-05-20
IIRC, you'd have to reinstall without choosing to encrypt your home directory.

---

### Post by MelodiesonMusic on 2011-05-21
Sheesh =\ now for my next question: before I reinstall are there any specific files I can move to a usb that hold my settings (background, installed programs etc.) or do I have to reset them after the install.

---

### Post by CharlesA on 2011-05-21
You'd just need to copy your home directory and restore it after reinstalling.

---

### Post by Dave_L on 2011-05-21
After installation, I encrypted my home directory. I think it is useful, since it protects my data in case the computer were lost or stolen.

If I wanted to reverse the process, I might try the following:

---

### Post by MelodiesonMusic on 2011-05-21
@CharlesA thank you :)

@Dave_L Can you explain that in more detail, i'm a little lost. How would i edit /etc/fstab?

---

### Post by FuturePilot on 2011-05-21
No, you don't need to reinstall to get rid of ecryptfs. See here [https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup")

---

### Post by CharlesA on 2011-05-22
> **FuturePilot said:**
> No, you don't need to reinstall to get rid of ecryptfs. See here [https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup")

Awesome. I did not know that! :)

---

