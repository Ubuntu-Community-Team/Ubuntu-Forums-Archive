---
title: "How to disable SSD hardware encryption"
date: 2021-01-04
forum: Security
---

### Post by Drenriza on 2021-01-04
Hi all!

I have installed Ubuntu 20.04 with full disk software encryption.

My question is: How do i figure out if my SSD have hardware encryption enabled and if such, disable it so only the Ubuntu OS handle all the encryption needed?

Thanks in advance
Best regards

---

### Post by CelticWarrior on 2021-01-04
If a drive has hardware encryption you're supposed to provide a password/passphrase even before Grub.

---

### Post by Drenriza on 2021-01-04
Thanks for your reply CelticWarrior!

So it's rather safe to assume, that if i do not provide such a password before the decryption password used by Linux than i dont have SSD hardware encryption running?

Thanks in advance
Best regards

---

### Post by TheFu on 2021-01-04
> **Drenriza said:**
> Thanks for your reply CelticWarrior!

So it's rather safe to assume, that if i do not provide such a password before the decryption password used by Linux than i dont have SSD hardware encryption running? 

Yes.  Or the encryption is tied to the TPM chip of the system.  Look up the model ssd. That will tell o whether there is hw encryption or not.

Regardless, wen sing any sort of encryption, excellent backups are mandatory. Should anything bad happen, the backups will be the only way to recover.  This applies to all SD failures. It isn't like there is a separate controller or platter to be replaced for $3000. Good backups solve all sorts of problems.

---

