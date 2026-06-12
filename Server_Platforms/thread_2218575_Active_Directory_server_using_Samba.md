---
title: "Active Directory server using Samba"
date: 2014-04-21
forum: Server Platforms
---

### Post by Jacob_Tennant on 2014-04-21
I am trying to build a Ubuntu 14.04 based Active Directory server using Samba4 to work as a back-up to my primary Windows Server 2012R2 Active Directory server.

I have found many examples of using Samba4 as a primary domain controller but nothing about using it as a backup domain controller.

---

### Post by lingpanda on 2014-04-22
> **Jacob_Tennant said:**
> I am trying to build a Ubuntu 14.04 based Active Directory server using Samba4 to work as a back-up to my primary Windows Server 2012R2 Active Directory server.

I have found many examples of using Samba4 as a primary domain controller but nothing about using it as a backup domain controller.

See link [https://wiki.samba.org/index.php/Join_a_domain_as_a_DC](https://wiki.samba.org/index.php/Join_a_domain_as_a_DC)

---

### Post by JnPson on 2014-04-25
> **Jacob_Tennant said:**
> I am trying to build a Ubuntu 14.04 based Active Directory server using Samba4 to work as a back-up to my primary Windows Server 2012R2 Active Directory server.

I have found many examples of using Samba4 as a primary domain controller but nothing about using it as a backup domain controller.

In Active Directory there are no primary or backup domain controllers. All are equal. 

But the first AD DC is the one holding all the FSMO roles.

---

