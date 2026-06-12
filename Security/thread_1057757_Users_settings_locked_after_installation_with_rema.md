---
title: "Users settings locked after installation with remastersys"
date: 2009-02-02
forum: Security
---

### Post by gtlp on 2009-02-02
I installed Ubuntu 8.10 on my notebook using an installation DVD I created with the "Remastersys" from my desktop PC. This means that I installed in the notebook all the packages that were installed in the desktop PC. Everything seems OK apart from the fact that I cannot change the user settings from the System-Administration-Users and Groups menu. The "unlock" key does not respond.

I guess that something might be wrong in the /etc/group file but I cannot figure out. Any ideas?
thanks

---

### Post by cdenley on 2009-02-02
Is your user in the admin group?
```

id

```

Do you have a line like "%admin ALL=(ALL) ALL" in /etc/sudoers?
```

sudo cat /etc/sudoers

```

---

### Post by gtlp on 2009-02-03
> **cdenley said:**
> Is your user in the admin group?
```

id

```

Do you have a line like "%admin ALL=(ALL) ALL" in /etc/sudoers?
```

sudo cat /etc/sudoers

```

All the above seem to be OK (I compared to another PC that is working fine)

---

### Post by gtlp on 2009-02-03
> **gtlp said:**
> All the above seem to be OK (I compared to another PC that is working fine)

I changed the "<match user="root">" to <match user="root|username"> in /etc/PolicyKit.conf file and "users and group settings" are permanently unlocked now, so I can modify. But this is not the best solution.

---

