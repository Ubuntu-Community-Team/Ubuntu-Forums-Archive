---
title: "Help with work hardrive encryption"
date: 2009-09-24
forum: Security
---

### Post by colinireland on 2009-09-24
Hello,

I have been given the job of looking into the encryption of a hard drive at work. Its a WD 1Tb. I am using Ubuntu 9.10 and True crypt was suggested to me as the software to use. If I was to encrypt this drive on ubuntu using true crypt will I be able to plug the hard drive into a windows machine and decrypt the data? Will the windows machine also have to have True Crypt or will I be presented with some sort of window to enter a password.
Once a hard drive is encrypted is it easy to completely decrypt it, as in to change back to its state when it first came out of the box.

Any help would be greatly appreciated.

Colin

---

### Post by Sarmacid on 2009-09-24
Check the documentation at [https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

Should answer most if not all of your questions.

---

### Post by XCan on 2009-09-24
From personal experience. I have create truecrypt volume in Windows and mounted them with no issues in Ubuntu. I have also done the reverse. However, you will need TrueCrypt on both systems, be it installed of a truecrypt in traveller mode. Once it's encrypted, I guess the easiest for you is to move the data to somewhere else, reformat and move it back.

---

### Post by HermanAB on 2009-09-25
Here you go - complete with wizards:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)
[http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

---

### Post by colinireland on 2009-09-25
thanks for the help lads. Everything i needed!!!

---

