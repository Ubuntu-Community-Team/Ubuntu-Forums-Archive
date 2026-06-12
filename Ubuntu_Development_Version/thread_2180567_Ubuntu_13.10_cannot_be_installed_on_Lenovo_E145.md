---
title: "Ubuntu 13.10 cannot be installed on Lenovo E145"
date: 2013-10-13
forum: Ubuntu Development Version
---

### Post by application on 2013-10-13
Today I tried installing the 64 Bit version of Ubuntu 13.10 on my new Lenovo E145 laptop, but the installation crashes soon after the Live Media boot screen. I just wanted to let you know, so that you can fix this issued before 13.10 gets released.

---

### Post by tajreed on 2013-10-13
I've installed 13.1 on new Lenovo g500s Touch. Works perfectly. Give more details on the failure.
Are you trying install over/along side W8?

---

### Post by ping-wu on 2013-10-14
For a laptop such as Lenovo E145 with AMD graphic card, my experience is that I need to boot with the NOMODESET kernel parameter turned on.  Install Ubuntu, boot into the install system, again with the NOMODESET parameter.   Then install the fglrx driver.

---

### Post by application on 2013-10-14
The installation routine of Ubuntu 13.10 simply quit without an error message. I was using the latest built last night. 

Then I dediced to try Ubuntu 13.04 (64 bit) and it simply worked out of the box. So it seems that something is wrong with the new version. At least when you try to install it on a Lenovo E145. 

> **ping-wu said:**
> For a laptop such as Lenovo E145 with AMD graphic card, my experience is that I need to boot with the NOMODESET kernel parameter turned on.  Install Ubuntu, boot into the install system, again with the NOMODESET parameter.   Then install the fglrx driver.

---

### Post by william-d-kopsaftis on 2013-10-17
I have tried 12.04, 13.04 with now luck, just black screen, what were your BIOS settings (UEFI en, Secure Boot, dis)? Need to be able to dual-boot?

---

