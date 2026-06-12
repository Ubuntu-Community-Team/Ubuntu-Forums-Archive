---
title: "batch user creation problems"
date: 2011-11-02
forum: Server Platforms
---

### Post by fouadk on 2011-11-02
hi everyone...

first of all i have edited /etc/bashrc in order to set the oraclehome in order to be able to use sqlplus without the absolute path

second of all i have created users using useradd because i want to create batch users and to provide passwords for these newly created users.
the useradd command i issed is the following:
```
useradd -m -k /etc/skel/. -p password newusername
```

my first problem is that if i login locally to one of those created users it seems im getting i trimmed down profile as i only see the $ symbol...plus i cant use the sqlplus tool without providing the absolute path to it.

plus it seems that i cant connect via SSH using those newly created usernames.

please help

thanks in advance

---

### Post by aeiah on 2011-11-02
is the home dir being created properly? i dont think you should have that dot in there, so:
```

useradd -m -k /etc/skel/ -p password newusername

```

if that does nothing, perhaps your newly created users aren't using the global /etc/bashrc for some reason. perhaps you could copy it to the desired location in /etc/skel (probably /etc/skel/.bashrc ) so oraclehome is specified in every new users own bashrc and not just the global one

---

### Post by fouadk on 2011-11-03
to whom might be interested i found out what i was doing wrong.

first of all i couldnt get SSH access because my users didnt have passwords because the p flag of useradd expect a crypted password.

second of all my users werent using their local .bashrc neither /etc/bash.bashrc becuase useradd by default sets the default shell to /bin/sh

so the proper way that solved it in my situation was the following usage of useradd:

```

sudo useradd -m -k /etc/skel -s /bin/bash -p $(perl -e 'print crypt("password", "aa")') username

```

hope this helps someone

---

