---
title: "how can i join linux ubuntu machine to windows active directory"
date: 2022-06-22
forum: Security
---

### Post by golden02yadav on 2022-06-22
please help me join ubuntu machine 20.04 to windows active directory server 
I have followed some online article but I am not able to connect my ubuntu machine to active directory 
please help me !! i getting error called : -
kinit: cannot find KDC for realm  "DOMAIN" while getting initial credentials

---

### Post by TheFu on 2022-06-22
I cannot help (haven't seen or touched MS-AD since 2008), but I know that error is a Kerberos init problem. Check your Kerberos setup.

---

### Post by cyberkingdom on 2022-06-27
It seems that Canonical has a whitepaper on how to do this [https://ubuntu.com/engage/microsoft-active-directory](https://ubuntu.com/engage/microsoft-active-directory). Hope this helps.

---

### Post by ActionParsnip on 2022-07-31
Did you get this sorted? I do tjis pretty much daily...?

---

### Post by mIk3_08 on 2022-08-01
> **cyberkingdom said:**
> It seems that Canonical has a whitepaper on how to do this [https://ubuntu.com/engage/microsoft-active-directory](https://ubuntu.com/engage/microsoft-active-directory). Hope this helps.
I think this link is an active enterprise application for Active Directory (AD) Integration. If you want to apply this is one of the convenient way for you to set up Active Directory with MS Windows. Regards and cheers.

---

