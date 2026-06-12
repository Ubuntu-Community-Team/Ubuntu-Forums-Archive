---
title: "Central User Management"
date: 2012-05-10
forum: Server Platforms
---

### Post by jagdipa on 2012-05-10
I must apologise for my simple question :(

I am looking for a method of having a central user database that is used to check credentials when logging in. I have come from a Windows environment where I am use to Active Directory. Is there something similar in Ubuntu Server? How do I go about installing and getting it to work?

---

### Post by 2F4U on 2012-05-10
Ubuntu is able to join an existing Active Directory, if you already have one:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

### Post by rubylaser on 2012-05-10
I'd suggest [OpenLDAP]("https://help.ubuntu.com/community/OpenLDAPServer") or continue to use AD as suggested above.

---

### Post by SeijiSensei on 2012-05-10
Other options include [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") and [RADIUS]("http://www.mydeveloperblog.com/linux-tutorial/radius/radius-servers-installation-guide-freeradius-ubuntu-mysql/").

---

### Post by ulfkosack on 2012-05-10
Hi jagdipa,

I'm looking a long time for a central user management for linux in conjunction with a existing Windows Active Directory. Until now the easyiest way for me is the login via PAM and Kerberos. You need only ntp for time synchronisation, krb5-user for Kerberos usertools and libpam-krb5 for the integration in the PAM configuration. After installation of this you only have to configure the /etc/krb5.conf with your domain settings an create local users. This local users will be checked against the Windows AD only for password.

If it is interesting for you, I will generalize my script from the office for you.:p

Ulf

---

