---
title: "sudo-ldap: stop sudo searching after the first match"
date: 2014-09-01
forum: Server Platforms
---

### Post by richard51 on 2014-09-01
I am using **sudo-ldap** to control which ldap users have sudo privileges. In my **nsswitch.conf** file I have the following line:

```
sudoers: files ldap
```
If the user is found in files (*/etc/sudoers*), it still searches ldap afterwards. This causes a delay for local users that are not connected to the ldap server and wish to run sudo commands (*because it cannot find the ldap server*). I use **nss_initgroups_ignoreusers** (*in /etc/ldap.conf*) to prevent searching ldap for local users, but this has no effect on **sudo-ldap**, and I don't want to add **sudo** to the  **nss_initgroups_ignoreusers **list as I am not sure what effect this would have on my **sudo ldap users**.

Is there a way to prevent the additional search of ldap after the first match in files is found?

---

