---
title: "New mysql user cant login"
date: 2008-04-25
forum: Server Platforms
---

### Post by uknowho008 on 2008-04-25
i installed a lamp setup with the following.

```
 sudo apt-get install apache2 php5 mysql-server php5-mysql
```

ive set this up before but dont remember exactly which packages i used. anyhow it seems to work accept i cant seem to loging with the new user account. i add a user with a password and select all priveleges but then i log out and try to log in with the new account and i get this error everytime. did i forget something? thanks.

```
#1045 - Access denied for user 'uknowho008'@'localhost' (using password: YES)
```

---

### Post by Monicker on 2008-04-25
Did you do "flush privileges;" after creating the new user?

---

### Post by uknowho008 on 2008-04-25
> **Monicker said:**
> Did you do "flush privileges;" after creating the new user?

yes, its still not working.

---

### Post by Monicker on 2008-04-25
I would verify that same uername was not created with different host specifications and passwords.

from the mysql cli:

```
use mysql;
select User,Host,Password from user where User='uknowho008';
```


I've accidentally done it myself before, where I had 'johndoe'@'localhost' with one password and 'johndoe'@'hostname' with a different password.

---

### Post by uknowho008 on 2008-04-25
> **Monicker said:**
> I would verify that same uername was not created with different host specifications and passwords.

from the mysql cli:

```
use mysql;
select User,Host,Password from user where User='uknowho008';
```


I've accidentally done it myself before, where I had 'johndoe'@'localhost' with one password and 'johndoe'@'hostname' with a different password.

what am i checking here? just that there is only one entry? there is only one entry and host is set to % for any i believe. the password is encrypted but the first character is a * and ive never seen that before. is that correct?

---

### Post by Monicker on 2008-04-25
Ahh. You mentioned earlier that the account had been created as a localhost account.  I have seen this before, where mysql will not let an account access directly from the local machine unless its account is specifically for 'user'@'localhost'.

Try to connect to that account from a machine other than the mysql server.  If that works, create the same username @ localhost with the same password.

---

### Post by uknowho008 on 2008-04-25
> **Monicker said:**
> Ahh. You mentioned earlier that the account had been created as a localhost account.  I have seen this before, where mysql will not let an account access directly from the local machine unless its account is specifically for 'user'@'localhost'.

Try to connect to that account from a machine other than the mysql server.  If that works, create the same username @ localhost with the same password.

hmmm... well i tried logging in with another machine and it didnt work. but then i changed the host to localhost anyways and it worked. so i guess thats all i need. thanks for helping me figure this out.

---

### Post by Sarteck on 2008-09-24
Thank you very much!

I was having this problem with every new user I created, and I was having to use "root" for a while instead of the usernames I created. XD

Adding the host 'localhost' solved it--those usernames finally work.  :)

---

