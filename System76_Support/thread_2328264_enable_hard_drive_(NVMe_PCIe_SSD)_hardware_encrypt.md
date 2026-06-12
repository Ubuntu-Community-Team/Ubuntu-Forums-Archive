---
title: "enable hard drive (NVMe PCIe SSD) hardware encryption on Lemur lemu6"
date: 2016-06-19
forum: System76 Support
---

### Post by donald-a-pellegrino on 2016-06-19
I have a System76 Lemur lemu6 with the "256 GB NVMe PCIe M.2 SSD" option. I hit F7 during boot to access BIOS but I could not find an option to set an ATA password.

How do I make use of the hard drive's built-in hardware encryption?

---

### Post by DuckHook on 2016-06-19
As far as I know, the only way to use SSD HW encryption is to define an ATA password in the BIOS. Otherwise, there are hybrid solutions as per [this]("http://askubuntu.com/questions/506556/how-to-enable-hardware-encryption-on-ssds-like-samsung-840-evo") thread. You can always use Ubuntu's native disk encryption. This has the advantage on not relying on closed technology. As stated in the referred thread, one of the disadvantages of HW-based encryption is that if the HW breaks, your data is lost forever, whereas with SW-based encryption, it is retrievable so long as you know your encryption password/passphrase.

---

### Post by donald-a-pellegrino on 2016-06-20
Thanks @DuckHook. It does seem that setting an ATA password in BIOS is the way to go. Unfortunately, I am unable to find where the ATA password is set in the BIOS on the System76 Lemur lemu6.

---

### Post by DuckHook on 2016-06-20
> **donald-a-pellegrino said:**
> ...I am unable to find where the ATA password is set in the BIOS on the System76 Lemur lemu6.Can't help you with that one, I'm afraid, as I don't own such a system. Try contacting System76 for help.

---

