---
title: "UBUNTU 22.04 as a AD Domain controller"
date: 2024-01-21
forum: Server Platforms
---

### Post by waendur on 2024-01-21
Good morning. I am studying IT and I have to make a project for one subject. I would like to create a Active Directory domain controller based on SAMBA and I have some doubts I want to share.

In the SAMBA documentation there is a procedure to create samba users and groups but if I need to join other products like NEXTCLOUD I will need to login with users stored in SAMBA AD DC, so Does SAMBA4 supports LDAP consults to get the organizational units where the users are stored?

Do I need to install openLDAP on the SAMBA AD DC controller?

How can I link samba users with openldap?

I didn't find any information about this.

Thanks in advance.

---

### Post by MAFoElffen on 2024-01-21
Here is some reading to answer your questions on what you need, and how to set it up: [https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller)

---

### Post by avidandrew on 2024-02-01
Yes, you can authenticate applications which want to authenticate with an LDAP server with Samba AD DC

---

### Post by stevehenderson710 on 2024-07-25
Do you us a GUI for user account management?

---

### Post by stephan4 on 2024-08-27
You don't need openLDAP ... yes LDAP as a protocol is used but that's the nature of ADDC.
Simply think of your SAMBA ADDC like an older Windows 2012r2 ADDC. 

Perhaps you take a look at the RSAT Tools too.

---

### Post by QIII on 2024-08-27
Closed.  RIP.

---

