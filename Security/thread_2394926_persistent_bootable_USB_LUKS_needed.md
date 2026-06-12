---
title: "persistent bootable USB LUKS needed"
date: 2018-06-23
forum: Security
---

### Post by pjmlmas on 2018-06-23
I want to create a bootable persistent USB. This will be used for financial, tax, and medical records.
I gathered from online sites that I am able to create a USB drive that could be encrypted and store these records using LUKS.
However, I also read that a bootable persistent USB drive could also be made encrypted. The os system as well as the data.
What reasons would one need the os system to be encrypted in use case listed above?
Is my understanding that one can create mountable USB drive that encrypts the data using LUKS?

---

### Post by C.S.Cameron on 2018-06-24
I have never had any luck with full disk encryption of a bootable flash drive. 16.04 and prior have the option to encrypt home during a Full install to USB.
Home folder can be encrypted after install, I will try to find the post where @sudodus shows me how.

Sudodus shows us how in this thread:

[https://askubuntu.com/questions/869874/password-in-persistent-live-usb-is-it-possible/870048#870048](https://askubuntu.com/questions/869874/password-in-persistent-live-usb-is-it-possible/870048#870048)

---

