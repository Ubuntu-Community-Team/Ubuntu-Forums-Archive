---
title: "Installing Windows parallel to encrypted Ubuntu"
date: 2011-11-02
forum: Security
---

### Post by ACBC_ on 2011-11-02
Hi,

I have Ubuntu 11.10 installed on my IBM Laptop. It is encrypted with the full disk encryption of the Alternate installer CD of Ubuntu. No manual partitioning was applied, I used the automatic LVM full disk encryption.

Now I want to install Windows (XP) parallel to Ubuntu. 

It was not possible for me to find a tutorial for this. Can you help me with this?

I found lots of tutorials how to install Windows parallel to Ubuntu but none dealt with an fully encrypted Ubuntu system. Thank you.


PS: Once Windows is installed I'd like to encrypt it with TrueCrypt.

---

### Post by 2F4U on 2011-11-02
You would need to shrink a partition to make room for Windows. However, if you install Windows after Ubuntu, it will overwrite the boot boot loader of Ubuntu.

---

### Post by ACBC_ on 2011-11-02
Hi 2F4U, do the usual tutorials for installing Windows after Ubuntu which back up the boot loader and reinstall it after Windows was installed also apply to a encrypted Ubuntu system? No changes needed?

---

### Post by HermanAB on 2011-11-02
The better solution is to use Virtualbox.  Then you can run Windows in a window.

---

### Post by ACBC_ on 2011-11-03
VirtualBox is in general a very good idea and cool tool but unfortunately doesn't work for me since my laptop is too slow for it. But thank you for the hint.

---

