---
title: "[SOLVED] how do i change password for user login thru terminal?"
date: 2008-09-20
forum: Security
---

### Post by bigdee973 on 2008-09-20
how do i go about changing the password for a user through a terminal? i need to change a password for a user at home and im in ssh...i tried sudo passwd but they were still able to use their password to gain access to the computer using their same username and password...how can i change it thru terminal

---

### Post by hyper_ch on 2008-09-20
```

sudo passwd USER

```

---

### Post by DouglasAWh on 2009-03-09
I get

```

passwd: Authentication token manipulation error
passwd: password unchanged

```

where I do 

```
passwd
```

or ```
passwd dwhitfie
```

dwhitfie's home still exists.  I can log in with a domain account, so I'm thinking somehow Likewise is associated with my problems.

---

### Post by thahir1986 on 2010-06-24
thanks..now i know how to change the password from terminal

---

