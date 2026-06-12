---
title: "How can I find out if Ubuntu 15.10 comes with TPM enabled?"
date: 2016-02-21
forum: Security
---

### Post by shahin on 2016-02-21
I want to interface with a TPM card connected to my Ubuntu 15.10 via USB. How can I know if the kernel supports TPM? And if not, how can I get a version which does? How can I activate the Trusted Platform Module support on my machine please?

---

### Post by oldos2er on 2016-02-21
Just FYI, 15.04 is now end-of-life and no longer supported.

---

### Post by shahin on 2016-02-21
My bad; I meant 15.10. Thanks for catching that.

---

### Post by oldfred on 2016-02-21
I know nothing about TPM, but saved some links, now many older.

 TPM 2.0
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-3.20-TPM-2.0-Security](http://www.phoronix.com/scan.php?page=news_item&px=Linux-3.20-TPM-2.0-Security)
[http://en.wikipedia.org/wiki/Trusted_Platform_Module#TPM_1.2_vs_TPM_2.0](http://en.wikipedia.org/wiki/Trusted_Platform_Module#TPM_1.2_vs_TPM_2.0)
Some UEFI also have TPM 
[http://technet.microsoft.com/en-us/windows/dn168169.aspx](http://technet.microsoft.com/en-us/windows/dn168169.aspx)
UEFI secure boot doesn't have anything to do with a TPM.
[https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en](https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en)
Microsoft has announced that from January 1, 2015 all computers will have to be equipped with a TPM 2.0 module in order to pass Windows 8.1 hardware certification.
[https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module)
Re: certificate to verify signature of Ubuntu kernel 
[http://ubuntuforums.org/showthread.php?t=2259248](http://ubuntuforums.org/showthread.php?t=2259248)
Older computer without TPM
GRUB_CMDLINE_LINUX_DEFAULT="tpm_tis.force=1"

---

