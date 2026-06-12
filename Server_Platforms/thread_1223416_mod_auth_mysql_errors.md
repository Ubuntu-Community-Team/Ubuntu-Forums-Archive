---
title: "mod_auth_mysql errors"
date: 2009-07-26
forum: Server Platforms
---

### Post by xsilvergs on 2009-07-26
Hi I'm new to servers and struggling to get mod_auth_mysql to work.

I've had mysql working well for some time now, I then added a .htaccess and .htpasswd file and that worked fine.

I've now installed mod_auth_mysql but get errors. My .htaccess looks like this at the moment:
AuthName "some name"
AuthType Basic

Auth_MySQL On
Auth_MySQL_Host local

Auth_MySQL_DB bwam
Auth_MySQL_Password_Table observers
Auth_MySQL_Username_Field username
Auth_MySQL_Password_Field password
Auth_MySQL_Encryption_Types Plaintext
Auth_MySQL_Empty_Passwords off

Auth_MySQL_Authoritative on

require valid-user


I have also removed the .htpasswd file as I believe it is no longer required.

In my web site each time I expect to see a login box I get a Internal Server Error page. The Apache2 error.log shows (9)Bad file descriptor: Could not open password file: (null) refer: http:// address of my server

Can anybody give me some advice please?

---

### Post by wojox on 2009-07-26
Try this:

AuthName "some name"
AuthType Basic

AuthMySQLEnable On
AuthMySQLHost localhost

AuthMySQLDB test
AuthMySQLUserTable observers
AuthMySQLNameField username
AuthMySQLPasswordField password
AuthMySQLPwEncryption none
AuthMySQLNoPasswd Off

AuthMySQLAuthoritative On

---

### Post by xsilvergs on 2009-07-26
Hi wojox, thanks for reply.

I tryed your suggestion, it still doesn't work but the error.log now reads:-

[alert] [client 192.168.1.3] /var/www/BWAMgoog/observers/.htaccess: Invalid command 'AuthMySQLEnable', perhaps misspelled or defined by a module not included in the server configuration, referer: [http://192.168.1.104/BWAMgoog/index.php](http://192.168.1.104/BWAMgoog/index.php)

Can you help with this?

Thanks

---

### Post by xsilvergs on 2009-07-27
Well I've got a little further and my .htaccess looks like this:-

Auth_MySQL On
Auth_MySQL_Authoritative on
Auth_MySQL_Host localhost

Auth_MySQL_DB bwam
Auth_MySQL_Password_Table observers
Auth_MySQL_Empty_Passwords Off
Auth_MySQL_Encrypted_Passwords on
Auth_MySQL_Username_Field username
Auth_MySQL_Password_Field password
Auth_MySQL_Encryption_Types MySQL


AuthBasicAuthoritative Off
AuthUserFile /dev/null

AuthName "observers sections"
AuthType Basic

<Limit GET POST>
Require valid-user
</Limit>

Now when I hit the button in my web page I get the login box but when I type in a correct name and password  followed by OK the login box reappears empty waiting for me to login.

Here are the changes I've made to the apache2.conf:-

Auth_MySQL_Info localhost name password

<Directory "/var/www/BWAMgoog/observers">
Options +Indexes FollowSymLinks MultiViews
AllowOverride AuthConfig Options FileInfo Limit
Order allow,deny
Allow From All
</Directory>

Any ideas?

---

### Post by xsilvergs on 2009-07-30
Well I keep trying but have now run out of new ideas.

I get an error message in apache2 error.log:-

[error] [client 192.168.1.3] user joe.bloggs not found

Can any one help please??

Thank you

---

### Post by wojox on 2009-07-30
What does /var/log/mysql/mysql.log say?

---

### Post by xsilvergs on 2009-07-30
/var/log/mysql is empty! The folder is empty.

---

### Post by EdGy28376 on 2009-12-31
I am fighting the same problem you posted. Did you ever get it solved?

Happy New Year!

---

### Post by fang0654 on 2012-05-01
Edit: I didn't realize he had already done the following, and it didn't fix it for him.  It did fix it for me however, so I'll leave it for anyone else that comes across this thread with this error.

---
I know this is an old thread, but it comes up pretty high in a Google search, so I figured I'd post the answer.

Apache2 will still try to use the file auth as the primary authentication source.  If the AuthUserFile isn't set, you get the bad file descriptor error.  If it is set, then Apache only uses that.  The fix is to add this:

```

AuthUserFile /dev/null          
AuthBasicAuthoritative Off

```

You may also need the following:
```
Auth_MySQL_Authoritative On
```

I don't think you do, but I haven't tested without it.

---

