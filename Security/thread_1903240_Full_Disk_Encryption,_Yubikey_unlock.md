---
title: "Full Disk Encryption, Yubikey unlock"
date: 2012-01-02
forum: Security
---

### Post by Legeril on 2012-01-02
I am in a position now where I need more security for my computer, starting a business and certain data needs to be protected. I would like to try a method of security that seems to me to be top notch.

Namely I would like to fully encrypt my disk so that it requires an OTP from a yubikey to start-up, I have tried google searches for this but havn't found very much information. The info I have found seems to require a very indepth knowledge that I haven't gained yet.

Does anybody have any experience with this?

---

### Post by jerrrys on 2012-01-03
Maybe you should start with something less complex.  Maybe just start with encrypting your home folder.  After all, that is where your personal data should be.

good luck

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=encrypt+home&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=encrypt+home&sa=Search&cof=FORID:9)

---

### Post by emiller12345 on 2012-01-03
You may want to start here ([https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)). I thought at one time it was possible to setup LUKS from the alternate CD desktop install, which is a full disk encrypt, but I'm not 100%.

---

### Post by mattxhand on 2012-01-03
If you are concerned with encrypting your computer (and depending on the kind of data you are storing) I would consider starting at encrypting your home directory as the first measure, then full disk encrypting with TrueCrypt or something of the sort, and anything past that (anything involving HIPPA or PCI) will require certain environmental add-ins like 2FA, firewalls, proxies, and IPS.

Since I don't know what kind of business you are in, I can't give you solid input.

---

