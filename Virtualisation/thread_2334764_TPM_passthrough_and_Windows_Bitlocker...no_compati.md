---
title: "TPM passthrough and Windows Bitlocker...no compatible TPM found?"
date: 2016-08-22
forum: Virtualisation
---

### Post by KillerKelvUK on 2016-08-22
Another forum member posted a thread about TPM passthrough and its been something I've been meaning to do for a while.  Qemu 2.5 has a bug that prevents a Windows guest from loading the TPM driver, this is patched from qemu 2.6 onwards so I've got qemu 2.6.1 in my build chain and am running the guest on the cmd line.  Windows now reports my TPM in Device Manager under Security Devices but the Bitlocker app says no compatible TPM can be found :-/  The TPM is most definitely bitlocker compatible as if I boot Win10 on the same bare metal then everything works so this is a virt issue somewhere, and I'd hazard a guess to say its Windows guest specific as I believe passing the same device through to a linux guest works as I got output from tpm_nvinfo in my test linux guest.  

Has anyone seen this before?  Does anyone have a working TPM passthrough with Windows Bitlocker?  I've posted to the qemu mailing list but so far zip.

---

### Post by KillerKelvUK on 2016-08-22
Raised a bug ticket [https://bugs.launchpad.net/qemu/+bug/1615823](https://bugs.launchpad.net/qemu/+bug/1615823)

---

