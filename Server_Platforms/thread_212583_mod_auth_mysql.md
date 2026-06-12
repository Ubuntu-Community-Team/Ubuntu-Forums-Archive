---
title: "mod auth mysql"
date: 2006-07-10
forum: Server Platforms
---

### Post by langals on 2006-07-10
Hi

I installed mod auth mysql for apache 2 on dapper. I set up an .htaccess file in a folder in the following way:

AuthMySQL On
AuthName "Awstats"
AuthType Basic
AuthMySQL_Host localhost
AuthMySQL_DB vhcs2
AuthMySQL_Password_Table admin
AuthMySQL_User <<user>>
AuthMySQL_Password <<password>>
AuthMySQL_Username_Field admin_name
AuthMySQL_Password_Field admin_pass
AuthMySQL_Empty_Passwords Off
AuthMySQL_Encryption_Types Crypt_DES Crypt_MD5 Crypt MySQL PHP_MD5
require valid-user

One of the passwords seems to be stored in a different format to the others (Crypt I think), and I can log in with this user. However, with the other passwords, which I think are PHP_MD5, I cannot log in. I read somewhere that there might be a problem with auth mod mysql and PHP MD5 passwords? Is this true?

Would anyone be able to provide any assistance with this?

Many thanks

langals

---

