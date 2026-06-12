---
title: "Truecrypt encryption broken?"
date: 2010-03-30
forum: Security
---

### Post by dogdo on 2010-03-30
Does this require physical access to carry out successfully? [http://www.net-security.org/secworld.php?id=9077](http://www.net-security.org/secworld.php?id=9077)

---

### Post by mkvnmtr on 2010-03-30
From reading their links it looks like it provides a password brute force attack for True Crypt. Those are already available. TrueCrypt is only as good as your password. It looks like the package needs to be connected to the target it says nothing about remote access. Other brute force attacks could be used remotely. It does seem to be $795 that Iwill never need to spend.

---

### Post by OpSecShellshock on 2010-03-30
They have to retrieve the keys from memory, so I'd think physical access would be required. Using IEEE-1394 to access memory has been a known issue for a couple years at least, but I didn't know it could be done with USB. In any case, the keys would still have to be in memory at the time the forensic device is attached, so it would have to still be on since the last time the real user accessed the drive.

---

### Post by HandsOfBlue on 2010-03-31
This isn't news, and the encryption isn't broken.

IEE1394 (Firewire) uses DMA which is designed to allow memory access without the OS (or CPU) being involved.  That an encrypted file system can be accessed when it's unlocked isn't news either - it has to work that way or you can't access it yourself.

Allowing an attacker physical access to your computer provides them with a number of options, of which this is just one.  All that's happened here is that somebody has built a tool to speed up one attack.  This attack will work against all forms of encryption or against any information held in memory.

---

### Post by Nisal on 2010-03-31
it's possible to crack..not the encryption but the password is crackable

---

### Post by tubbygweilo on 2010-03-31
Nisal, I am so pleased that the cracking relates to having physical access to the kit and from what I can see using suboptimal length or strength passphrases. It was always thus.

---

### Post by Nisal on 2010-03-31
> **tubbygweilo said:**
> Nisal, I am so pleased that the cracking relates to having physical access to the kit and from what I can see using suboptimal length or strength passphrases. It was always thus.

yeah it is .. it not only at true crypt , for everthng it matters,just make complex passwords

---

