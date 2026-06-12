---
title: "mod_auth_mysql insanity"
date: 2010-03-08
forum: Server Platforms
---

### Post by ztripez on 2010-03-08
Okeii,

I've a Ubuntu 9.10 64Bit server running apache, I'm trying to create a WebDAV and use the mod_auth_mysql for authorization.
I've done this before on a Interpid Server.

However, I can't get to work, all i get is:

```
Internal error: pcfg_openfile() called with NULL filename
[Mon Mar 08 23:08:09 2010] [error] [client 87.96.177.26] (9)Bad file descriptor: Could not open password file: (null)

```

After -some- (aka many many hours of) googling the only thing I have found about the problem is that Auth_Basic somehow collide with mod_auth_mysql.

Since Windows 7 WEBDAV don't support Auth_Basic, only Auth_Digest i had to switch anyway.

Ok now it't doesn't crash but it don't login.

I've enabled mysql logging but it show nothing...


Here is my Apache config (for dav):

```
Alias /Public /media/Fatty/Public
<Location /Public>
    DAV On
    AuthBasicAuthoritative Off
    AuthMYSQL on
    AuthMySQL_Authoritative on
    AuthMySQL_DB ****
    Auth_MySQL_Host localhost
    Auth_MySQL_User ****
    Auth_MySQL_Password ****
    AuthMySQL_Password_Table ****
    AuthMySQL_Username_Field ****
    AuthMySQL_Password_Field ****
    AuthMySQL_Empty_Passwords off
    AuthMySQL_Encryption_Types PHP_MD5

    # Standard auth stuff
    AuthType Digest
    AuthName "restricted zone"
    Require valid-user
</Location>

```

Here is a snippet from my error.log

```
[Mon Mar 08 23:47:44 2010] [notice] caught SIGTERM, shutting down
[Mon Mar 08 23:47:45 2010] [notice] Digest: generating secret for digest authentication ...
[Mon Mar 08 23:47:45 2010] [notice] Digest: done
[Mon Mar 08 23:47:45 2010] [notice] Apache/2.2.12 (Ubuntu) DAV/2 PHP/5.2.10-2ubuntu6.4 with Suhosin-Patch mod_scgi/1.13 configured -- resuming normal operations
[Mon Mar 08 23:47:55 2010] [error] [client 127.0.0.1] Digest: user `testuser' in realm `restricted zone' not found: /Public/


```

And as i said, the mysql log don't give anything (well there is stuff in it but nothing relevant.


Any Ideas??

---

### Post by ianbmorgan on 2010-03-16
I'm having problems with this as well, but I am getting a segfault in my Apache logs.

Looks like there is a bug in the 4.3.9-11 release that affects 64-bit systems...

[https://bugs.launchpad.net/ubuntu/+source/mod-auth-mysql/+bug/364581](https://bugs.launchpad.net/ubuntu/+source/mod-auth-mysql/+bug/364581)

I think the options are to apply the patch mentioned, or get the -12 version.  I haven't tried it yet, though--still hoping to find an easier fix.

---

