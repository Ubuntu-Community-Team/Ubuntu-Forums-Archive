---
title: "Apache2 Mod-Auth-MySQL"
date: 2010-06-18
forum: Server Platforms
---

### Post by Skidbladnir on 2010-06-18
```

AuthType basic
AuthName "MySQL Administration Tests"
Auth_MySQL on
Auth_MySQL_Authoritative on
Auth_MySQL_Host localhost
Auth_MySQL_Port 3306
Auth_MySQL_User administration
Auth_MySQL_Password password
Auth_MySQL_DB administration
Auth_MySQL_Password_Table testpassword
Auth_MySQL_Username_Field username
Auth_MySQL_Password_Field passwd
Auth_MySQL_Group_Table testgroup
Auth_MySQL_Group_User_Field username
Auth_MySQL_Group_Field group
Auth_MySQL_Encryption_Types PHP_MD5 Crypt_MD5
AuthUserFile /dev/null
Require valid-user

```

I'm trying to get the hang of this, but, no matter what I do, it keeps prompting me for a username and password.  I enter the correct ones, and in error.log, it says '[Fri Jun 18 21:43:23 2010] [error] [client 192.168.0.10] user skidbladnir not found: /mysql-auth'.

---

### Post by Ryan Dwyer on 2010-06-18
And what's your database schema?

---

