---
title: "samba incompatibility between Breezy and Dapper"
date: 2006-09-04
forum: Server Platforms
---

### Post by anindya_m on 2006-09-04
I am sure someone has noticed this before: you cannot change password on a Breezy samba PDC with smbpasswd running from Dapper. This is apparently due to the different versions behaving in a different way. I have such a setup, and as a workaround I copied the Breezy version of smbpasswd to my Dapper system and it works properly.

Does anyone know of a way to accomplish password change on a Breezy PDC using the Dapper version of samba. Is there any "compatibility mode" ?

FYI: Breezy samba is 3.0.14a-6ubuntu1.1, Dapper samba is 3.0.22-1ubuntu3.1

Anindya

---

