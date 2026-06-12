---
title: "exclamation mark vs asterisk in /etc/shadow"
date: 2012-07-15
forum: Security
---

### Post by brancalessio on 2012-07-15
Sorry for the weird question, but I could not find a satisfying one browsing the web.

I see that in the root password field in /etc/shadow there is an exclamation mark (!), while for other disabled users there is an asterisk (*).

Why this difference? I just found a discussion on a Debian forum saying that it is the same (that is they are not both an hash so login is disabled), but I could not find any "official" documentation.

Thanks for your answers!

---

### Post by bodhi.zazen on 2012-07-16
See : [http://linux.die.net/man/5/shadow](http://linux.die.net/man/5/shadow)

> If the password field contains some string that is not a valid result of crypt(3), for instance ! or *, the user will not be able to use a unix password to log in (but the user may log in the system by other means).

This field may be empty, in which case no passwords are required to authenticate as the specified login name. However, some applications which read the /etc/shadow file may decide not to permit any access at all if the password field is empty.

A password field which starts with a exclamation mark means that the password is locked. The remaining characters on the line represent the password field before the password was locked.

---

### Post by brancalessio on 2012-07-20
OK, thanks for the reference. It seems they are all equivalent.

---

### Post by bodhi.zazen on 2012-07-21
> **brancalessio said:**
> OK, thanks for the reference. It seems they are all equivalent.

They are not equivalent.

Both will prevent password authentication

> If the password field contains some string that is not a valid result of crypt(3), for instance ! or *, the user will not be able to use a unix password to log in (but the user may log in the system by other means).

But, in addition, ! indicates the account was locked

> A password field which starts with a exclamation mark means that the password is locked. The remaining characters on the line represent the password field before the password was locked.

To lock an account

```
usermod -L <user_name>
```

In addition, > The remaining characters on the line represent the password field before the password was locked.

so ! also includes the previous password hash.

So accounts which are locked with a * do NOT contain previous password hashes.

Notice the difference between

> www-data:*:14910:0:99999:7:::

and

> root:!$6$qS76BvWz$fsO.aIeunBw128BjSH0EvKjXnCJktkz50N0yis9oKmCRsMh0LAmcXYPEsDNtrWpAFO.vAXmgCOJ7U5fJaYCnV1:15542:0:99999:7:::

Neither account can log in via password authentication, however, the root account was locked and the entry in /etc/shadow includes the previous password hash.

subtle but important difference.

---

### Post by brancalessio on 2012-07-22
> **bodhi.zazen said:**
> They are not equivalent.

Both will prevent password authentication



But, in addition, ! indicates the account was locked



To lock an account

```
usermod -L <user_name>
```In addition, 

so ! also includes the previous password hash.

So accounts which are locked with a * do NOT contain previous password hashes.

Notice the difference between



and



Neither account can log in via password authentication, however, the root account was locked and the entry in /etc/shadow includes the previous password hash.

subtle but important difference.
Yes, it's quite subtle. Yet I cannot understand the difference between

> root:!:15044:0:99999:7:::and

> root:*:15044:0:99999:7:::There should be no difference with respect to sudo and in both cases one cannot login. The exclamation mark in front of the password hash just is useful to "remember" the old hash.

---

### Post by bodhi.zazen on 2012-07-22
> **brancalessio said:**
> Yes, it's quite subtle. Yet I cannot understand the difference between

and

There should be no difference with respect to sudo and in both cases one cannot login. The exclamation mark in front of the password hash just is useful to "remember" the old hash.

There is no difference in the examples you provided. But the examples you provided are not the default behavior or you edited out the password hash in the "!" example you gave.

See and understand the difference in the examples I gave or explore the default behavior for yourself (set a root password, then lock the account).

In /etc/shadow, by default, * is used on accounts where no password has ever been set. By default, !<password_hash> is used when you lock an account.

Also /etc/shadow is only used for password authentication. You can log in via other methods (ssh keys and kerberos are two that come to mind).

---

