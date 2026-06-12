---
title: "Directory public_html Apache2 access login"
date: 2012-12-13
forum: Server Platforms
---

### Post by borjamf on 2012-12-13
Hello,
Running 12.04 Ubuntu Server.

I've been the last week trying to get working a local server with Apache2. Im using LDAP authentication and it's working OK, but I dont know how to do this:

- LDAP users can access their own files and read / write / replace them at will.
**- Each user can't even read the contents of the other users files, or preferably even see they files exist.**
- All of them can be properly accessed by apache and php

That's the biggest problem. I can't allow, for example, userldap1 to access /userldap2/public_html. With my actual config, every successful LDAP login can access to /*/public_html 

ldap_auth.conf

```
<Directory /home/disco2/*/public_html>
  AuthBasicProvider ldap
  AuthBasic basic
  AuthName "Authentication"
  AuthzLDAPAuthoritative off
  AuthLDAPURL ldap://myip/dc=prueba,dc=borja?uid?sub
  Require ldap-filter objectClass=posixAccount

</Directory>
```
I've tried several configurations and permissions, but I can't achieve this.

Could any help me? Im totally stuck on this.
Sorry for my english.

Thanks!

---

### Post by SeijiSensei on 2012-12-13
The trick is to give only the www-data user that Apache runs as the right to read the files.

First, you need to grant the www-data group access to the users' directories like this:

```

cd /home
sudo chgrp www-data *
sudo chmod g+x *

```

That grants members of the www-data group, which by default contains only the Apache user, the right to look into directories below /home/username.  It cannot read those files, but it can list the directory's contents.

Now we want to give the Apache user access to the users' public_html directories.

```

cd /home
sudo chgrp www-data */public_html
sudo chmod g+x */public_html
sudo chmod -R g+r */public_html/*

```

That should do it.  By default, any later files the user creates will have world-readable privileges, so they will be readable by the www-data user automatically.  However even though the files are world-readable, because other users have no rights in /home/username, they will still not be able to see each others' files.

---

### Post by borjamf on 2012-12-13
Thank you for answer. 

The problem persists. See:

[IMG]http://imageshack.us/a/img339/2471/authldap.jpg[/IMG]

[IMG]http://imageshack.us/a/img560/6537/authsuccess.jpg[/IMG]

Authentication correct? Yes -> see dir userldap2.

---

