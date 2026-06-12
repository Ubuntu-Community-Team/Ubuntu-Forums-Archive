---
title: "Recommendations for luks encryption"
date: 2010-01-08
forum: Security
---

### Post by Jordanwb on 2010-01-08
When 10.04 is released I'll encrypt my /home partition using luks. I've read that xts is good for hard drive encryption and aes is good for cipher encryption. What do you guys use?

I'm looking for something that is fairly secure without sacrificing a lot of speed.

---

### Post by euler_fan on 2010-01-09
> **Jordanwb said:**
> When 10.04 is released I'll encrypt my /home partition using luks. I've read that xts is good for hard drive encryption and aes is good for cipher encryption. What do you guys use?

I'm looking for something that is fairly secure without sacrificing a lot of speed.

AES is a fine block cipher. So are twofish and blowfish. Feel free to do any reading you need to about this to decide. Hashes to avoid are anything in the MD family, whereas SHA256 is a fine choice until someone finds a way to break it badly in this context.

XTS describes a way of implementing block encryption of blocks of your harddrive using a specified algorithm (e.g. AES). XTS-AES is an IEEE standard.

---

### Post by HermanAB on 2010-01-09
The military commonly use AES256, CBC, ESSIV, SHA256 for mitigation of accidental release of classified information.  That also happens to be the default LUKS encryption setup.  There are some wizards here: [http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

