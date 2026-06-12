---
title: "[SOLVED] Jailed SSH Users"
date: 2008-10-10
forum: Server Platforms
---

### Post by Sid1980 on 2008-10-10
I m running SSH server and for security reason i want to restrict local users to access all other directories except  their home directory. can anyone suggest me simple and fast way ?? apart from jailkit.

---

### Post by hyper_ch on 2008-10-10
MySecureShell - makes it easy

---

### Post by Sid1980 on 2008-10-11
> **hyper_ch said:**
> MySecureShell - makes it easy

Can u elaborate bit

---

### Post by hyper_ch on 2008-10-12
Can you say me what part of MySecureShell you have not understood from their homepage?

---

### Post by Sid1980 on 2008-10-12
> **hyper_ch said:**
> Can you say me what part of MySecureShell you have not understood from their homepage?


lol i did.... thxx

---

### Post by dperfors on 2008-10-14
> **Sid1980 said:**
> I m running SSH server and for security reason i want to restrict local users to access all other directories except  their home directory. can anyone suggest me simple and fast way ?? apart from jailkit.

Ubuntu 8.10 ships with OpenSSH 1.5.1 which comes with the option ChrootDirectory. That is what you are looking for I think :) (except that 8.10 is not yet available...)

---

