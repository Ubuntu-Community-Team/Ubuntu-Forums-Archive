---
title: "Ubuntu pro package status"
date: 2024-10-16
forum: Security
---

### Post by ajulian on 2024-10-16
I'm interested in a vulnerability fix for a certain package in a version under ESM. Is there any way to track what the status or priority is for this package release?

Thanks!

---

### Post by 0f4d0335 on 2024-10-17
Is this a known vulnerability?

You can check here: [https://ubuntu.com/security/notices](https://ubuntu.com/security/notices)

And then search for the CVE. They list the packages impacted.

---

### Post by ajulian on 2024-10-17
Yeah, it's known and fixed everywhere except bionic: [https://ubuntu.com/security/CVE-2024-21147](https://ubuntu.com/security/CVE-2024-21147)

Since it only says 'Vulnerable' it's hard to know if and when it will be uploaded

---

### Post by 0f4d0335 on 2024-10-17
> **ajulian said:**
> Since it only says 'Vulnerable' it's hard to know if and when it will be uploaded

It appears that multiple versions are supported on later LTS versions besides 18.04. I couldn't find any further information on the package itself as it seems that references to it were removed from the package site. Therefore I don't think there will be a fix for 18.04 LTS.

If you have a contract with Ubuntu for extended security, you should reach out to your vendor because they can confirm to you specifically what is supported. You can also check with 

[https://wiki.ubuntu.com/SecurityTeam/ESM/18.04](https://wiki.ubuntu.com/SecurityTeam/ESM/18.04)

[https://ubuntu.com/18-04](https://ubuntu.com/18-04)

It doesn't appear to me that Java has been selected as an application to receive extended security support.

---

