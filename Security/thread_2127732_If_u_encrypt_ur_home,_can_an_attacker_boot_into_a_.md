---
title: "If u encrypt ur home, can an attacker boot into a root console &amp; get ur data"
date: 2013-03-20
forum: Security
---

### Post by MechaMechanism on 2013-03-20
Let's say that durring install, I selected the encrypt your home dir.  Can an attacker boot the system into a root console or single user console or recovery console and change your password and then boot normally and log into your encrypted home.  I know that on Ubuntu systems one can just edit grub to boot to recovery/root console and change passwords, I know because I did this years ago back in the 9.10 or earlier days.  So what's the point of encrypting the home dir.

Hopefully someone will tell me that even if root changed the user password they would still need the decryption passphrase to decrypt home.  Kinda like 2 factor authentication.

---

### Post by Cheesemill on 2013-03-21
Don't worry, your safe.

There is no way an attacker can decrypt your home directory by booting into single-user mode.

---

### Post by tancrackers on 2013-03-21
I mean, a guy from the CIA can probably do that. But Ubuntu encompasses a good amount of servers, so I'd say you'll be just fine.

---

### Post by MechaMechanism on 2013-03-21
Cool, thanks for the replys.

---

### Post by thnewguy on 2013-03-23
I used to wonder about this too, but the user account password is separate from the encryption password. Without your encryption password the attacker cannot read your data. There is a nice explanation here: [https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

---

### Post by haqking on 2013-03-23
Hard Drive encryption is not uncrackable.

If the attacker has physcial access as implied in the OP then it is a matter of time and tools that the attacker has an/or knowledge.  It will still depend on your passpharse key and type of encryption.

Physcial access is root access for all intents and purposes.

There are many tools to allow this, HDD encryption is not much different to anything else if using a passphrase in that it is still only as strong or as weak as the attackers dictionary ;)

For example [https://code.google.com/p/luks-volume-cracker/](https://code.google.com/p/luks-volume-cracker/)

---

### Post by Stonecold1995 on 2013-03-23
> **haqking said:**
> Hard Drive encryption is not uncrackable.

If the attacker has physcial access as implied in the OP then it is a matter of time and tools that the attacker has an/or knowledge.  It will still depend on your passpharse key and type of encryption.

Physcial access is root access for all intents and purposes.

There are many tools to allow this, HDD encryption is not much different to anything else if using a passphrase in that it is still only as strong or as weak as the attackers dictionary ;)

For example [https://code.google.com/p/luks-volume-cracker/](https://code.google.com/p/luks-volume-cracker/)
^This.  And even if you use a password which is uncrackable with today's technology (or even technology in the forseable future), remember that there are other ways to gain entry.  For example, an encrypted home directory leaves all the inner workings of the computer in / unencrypted, so an attacker could simply turn your normal GNU utilities into a keylogger, recording your passkey as you enter it.  To defend against this, you should use disk encryption.  If you do that, only /boot is left unencrypted, and /boot is much easier to protect and discover tampering.

---

