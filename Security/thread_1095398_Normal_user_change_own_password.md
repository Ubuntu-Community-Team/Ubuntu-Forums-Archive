---
title: "Normal user change own password"
date: 2009-03-13
forum: Security
---

### Post by Dijk on 2009-03-13
As 'super user' I can run 'users and groups' and change my own password, and after 'unlock' I can even change other users properties like his password.
When a normal user logs on, access to 'users and groups' is totally blocked and he can't change his password himself.
Is there a way to make this possible ?

---

### Post by brian_p on 2009-03-13
> **Dijk said:**
> 

. . . . . and he can't change his password himself.
Is there a way to make this possible ?

```
man login.defs
```

PASS_MIN_DAYS

---

### Post by bodhi.zazen on 2009-03-14
> **Dijk said:**
> As 'super user' I can run 'users and groups' and change my own password, and after 'unlock' I can even change other users properties like his password.
When a normal user logs on, access to 'users and groups' is totally blocked and he can't change his password himself.
Is there a way to make this possible ?

If you wish to change a password , you can use the gui apps or the command line.

Have your user log in , open a terminal, and enter :

```
passwd
```

---

### Post by Dijk on 2009-03-14
Thanx, the command line 'passwd' works.
I'm a newbie to ubuntu and I don't know what you mean with 'you can use the gui apps.
The application 'users and groups' (users-admin) is disabled for normal users (non-administrators), at startup it says something like 'system configuration cannot be loaded - you have no access to the system configuration'. (explanations are in dutch)

I have never set pass-min-days and when I read man login.defs I read pass-min-days is a setting only for newly created users. I don't want to remove and re-create the user.

---

### Post by brian_p on 2009-03-14
> **Dijk said:**
> 

I have never set pass-min-days and when I read man login.defs I read pass-min-days is a setting only for newly created users. I don't want to remove and re-create the user.

My fault. I misunderstood what you wanted to do. What I wrote will not help you.

---

### Post by Dijk on 2009-03-15
I found it myself, more luck than wishdom:
The graphical application 'about me', found in 'system' - 'preferences', allows users to change their own password.

---

