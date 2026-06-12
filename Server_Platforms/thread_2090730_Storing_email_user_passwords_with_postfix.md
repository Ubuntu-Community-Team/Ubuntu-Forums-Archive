---
title: "Storing email user passwords with postfix"
date: 2012-12-03
forum: Server Platforms
---

### Post by AugustinMa on 2012-12-03
Hello,

I use a mysql backend for postfix: domains, email addresses, etc. 

[http://flurdy.com/docs/postfix/#data](http://flurdy.com/docs/postfix/#data) => Following this tutorial, the users' passwords are stored with the mysql encrypt() function which only takes into account the first 8 characters. It does not appear to be a very secure/strong way to store passwords.

How to set up postcript so that it can work with a mysql backend using a much stronger hashing algorithm. Especially, what solution exists for postfix to use passwords longer than 8 characters?

Thanks.

---

### Post by AugustinMa on 2012-12-03
The official courier documentation is very lacking. I document what I find here: [http://linux.overshoot.tv/wiki/server/courier](http://linux.overshoot.tv/wiki/server/courier) 

Anyway, I just found this:
[http://www.courier-mta.org/authlib/README.authmysql.html](http://www.courier-mta.org/authlib/README.authmysql.html)
> MYSQL_CRYPT_PWFIELD - name of the field containing the crypt-ed password (either MYSQL_CRYPT_PWFIELD or MYSQL_CLEAR_PWFIELD is required). NOTE: this password must be crypt-ed using the operating system's crypt function, NOT MySQL's crypt function. MySQL's crypt() function is non-standard and is not generally compatible with the operating system's crypt function.

The tutorial previously mentioned clearly uses mysql's crypt() function. Besides, the system does no seem to come with any function named 'crypt'. So, which is it? 

Is MySQL's crypt() function ok?
Do we have any other alternative?

---

