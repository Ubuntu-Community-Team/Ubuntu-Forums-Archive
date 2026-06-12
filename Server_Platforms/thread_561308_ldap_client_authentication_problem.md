---
title: "ldap client authentication problem"
date: 2007-09-27
forum: Server Platforms
---

### Post by zoffmann on 2007-09-27
Hello,

I have a ldap server installed on skolelinux machine (debian-edu), and I would like to be able to log in from my edubuntu machine.

I have followed  the following manual

[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

when I issue** getent passwd *myldapuser* **

- no response.

But when I do like this:

**openssl s_client -connect MY_LDAP_SERVER:636 -showcerts **

it works.

How to solve this ?

thanks in advance:KS

---

### Post by blackjackchik on 2007-10-14
Hello
I have the same prolem. I can't login from login screen in client machine.
Any ideas???:confused:

---

### Post by zoffmann on 2007-10-14
check your configuration files

---

