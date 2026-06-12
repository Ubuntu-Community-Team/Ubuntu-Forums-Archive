---
title: "Apache with MySQL &amp; etc/shadow authentication"
date: 2008-08-15
forum: Security
---

### Post by ishtanzar on 2008-08-15
Hello people !

I'm setting up my server with as a basic LAMP/Proftpd/Svn server. Currently, I'm trying to lock my SVN with both a system users (/etc/shadow) and virtual users (stored in MySQL) authentication.

I tried libapache2-mod-auth-shadow & libapache2-mod-auth-mysql which separatelly works great but there's no way to get them working together:

```

AuthShadow on

AuthMYSQL on
AuthMySQL_Authoritative on
AuthMySQL_Host 127.0.0.1
AuthMySQL_User proftpd
AuthMySQL_Password proftpd
AuthMySQL_DB ftp
AuthMySQL_Password_Table ftpuser
AuthMySQL_Empty_Passwords off
AuthMySQL_Encrypted_Passwords On
AuthMySQL_Encryption_Types MySQL Crypt_MD5 Plaintext Crypt_DES PHP_MD5
AuthMySQL_Username_Field userid
AuthMySQL_Password_Field passwd

AuthName "Restricted Area"
AuthType Basic
require valid-user

```

Only the mysql auth works...

I also tried libapache2-mod-authnz-external but I didn't find compiled programs to authenticate via the shadow file for ubuntu (I'd like to avoid compiling programs on the server).

I saw that SASL can authenticate via the shadow file but didn't find how to use it with apache.

Maybe someone could suggest me a way to manage my system and virtual users authentication as I'll probably install a mail server later.

Thanks for the help.

---

