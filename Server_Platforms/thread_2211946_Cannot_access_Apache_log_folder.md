---
title: "Cannot access Apache log folder"
date: 2014-03-18
forum: Server Platforms
---

### Post by as2000 on 2014-03-18
I get an error: Permission Denied when trying to go to the /var/log/apache2 directory so I can read my log. Here is my permissions for the folder and my user is part of adm group: drwxr-x--- 2 root      adm    4096 Mar 15 20:36 apache2

Any ideas? I am a little new to this and my test server does not have the same problem. Root, I can access, but not with my user account.

---

### Post by Lars Noodén on 2014-03-18
The users that you want to read the logs need to be in the group *adm*.  So if you can add your user to that group, it can then read the logs.  You'll have to log out and then back in again for the permissions to take full effect.

---

### Post by Lars Noodén on 2014-03-18
Can you check to be sure you are in adm?

```

groups as2000

```

---

### Post by as2000 on 2014-03-18
I thought my user account was adm, it was not. Getting that taken care of now...

---

