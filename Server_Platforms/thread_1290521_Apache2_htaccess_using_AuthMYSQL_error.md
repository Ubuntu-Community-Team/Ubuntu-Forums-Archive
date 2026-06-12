---
title: "Apache2 htaccess using AuthMYSQL error"
date: 2009-10-13
forum: Server Platforms
---

### Post by adman4054 on 2009-10-13
In the Apache error log I,m seeing "user pattypatty not found". Its a small db with only a few fields, I'm sure the pattypatty user exists in the username field in the subscribers table. 
As one post suggested I put some junk in the htaccess file and it throws a server error, so I would like to think that the webserver is reading the file.  My htaccess file contains:
AuthMYSQL On
AuthMySQL_Authoritative On
AuthMySQL_Host localhost
AuthMySQL_User patty
AuthMySQL_Password dontcare1
AuthMySQL_DB gratiot
AuthMySQL_Password_Table subscribers
AuthMySQL_Empty_Passwords off
AuthMySQL_Encrypted_Passwords off
AuthMySQL_Username_Field Username
AuthMySQL_Password_Field pw
AuthUserFile /dev/null 
AuthName "myName"
AuthType Basic
require valid-user 

I think its something simple but hours and hours later I still cant get it to work. I'm using 8.04, MYSQL5 and PHP5. Any help would be appreciated.:)

---

### Post by windependence on 2009-10-13
This is a FreeBSD tutorial, but it's no different for Ubuntu:

[http://www.freebsdmadeeasy.com/tutorials/web-server/password-protect-directories-with-htaccess.php](http://www.freebsdmadeeasy.com/tutorials/web-server/password-protect-directories-with-htaccess.php)

-Tim

---

### Post by adman4054 on 2009-10-13
> **windependence said:**
> This is a FreeBSD tutorial, but it's no different for Ubuntu:

[http://www.freebsdmadeeasy.com/tutorials/web-server/password-protect-directories-with-htaccess.php](http://www.freebsdmadeeasy.com/tutorials/web-server/password-protect-directories-with-htaccess.php)

-Tim

Thanks Windependence for the reply. I'm trying to use a db for the user/pass and it appears that there is a bug. I took me most of the day, and part of the night, so when someone else finds this topic, look here; [https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649](https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649)

In the mean time, if anybody knows a "work around" I would surely appreciate it. Thanks again!

---

