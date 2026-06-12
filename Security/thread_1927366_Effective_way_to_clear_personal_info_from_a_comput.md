---
title: "Effective way to clear personal info from a computer"
date: 2012-02-17
forum: Security
---

### Post by SoylentSteak on 2012-02-17
*Without* reformatting.

I'm selling my old computer and I'd like to make sure there are no traces of passwords, bank account numbers, etc. left on the hard drive. I'd really like to be able to do this without a re-install, if possible.

---

### Post by CryptAck on 2012-02-17
I personally would never risk it. I always reformat and reinstall.

---

### Post by Bucky Ball on 2012-02-17
> **CryptAck said:**
> I personally would never risk it. I always reformat and reinstall.

+1. There is an option with the alternate install CD (from memory) that when first booted by the new user it will ask for a new password and user. An OEM install, if you like. ;)

---

### Post by SoylentSteak on 2012-02-17
I'll reformat if I must. I was just thinking that there might be some package or command to accomplish this, as selling used computers is such a common thing these days.

---

### Post by Bucky Ball on 2012-02-17
Computers pre-installed with Windows are sold with the OEM install so the new user can add their own user/pw. Wipe everything and give that a try. I would. ;)

Here's some clues:

[http://au.search.yahoo.com/yhs/search?p=ubuntu%20oem%20installation&fr=altavista&fr2=sa-gp](http://au.search.yahoo.com/yhs/search?p=ubuntu%20oem%20installation&fr=altavista&fr2=sa-gp)

---

### Post by CharlesA on 2012-02-17
> **Bucky Ball said:**
> Computers pre-installed with Windows are sold with the OEM install so the new user can add their own user/pw. Wipe everything and give that a try. I would. ;)

Here's some clues:

[http://au.search.yahoo.com/yhs/search?p=ubuntu%20oem%20installation&fr=altavista&fr2=sa-gp](http://au.search.yahoo.com/yhs/search?p=ubuntu%20oem%20installation&fr=altavista&fr2=sa-gp)
This.

I wouldn't even bother trying to clean a machine before selling it. I would just wipe the drive and reinstall.

---

### Post by Bucky Ball on 2012-02-17
Here is a good guide/walkthrough from that link and it appears you don't need to use the alternate install CD:

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

---

### Post by HermanAB on 2012-02-18
Effective way? Twelve bore shotgun, 20 lb sledge hammer...

Boot with a CDROM and do this:
$ sudo dd if=/dev/urandom of=/dev/sda

This may be more secure:
$ sudo hdparm --security-set-pass PWD /dev/sda
$ sudo hdparm --security-erase-enhanced PWD /dev/sda

---

