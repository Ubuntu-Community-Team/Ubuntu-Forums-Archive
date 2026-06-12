---
title: "Where's apache mod_auth_pam gone in 9.10?"
date: 2010-03-23
forum: Server Platforms
---

### Post by fhendrik on 2010-03-23
Hi folks,

I want to set up PAM authentication with Apache2, but I cannot find a package for mod_auth_pam anywhere. Apparently it did exist in previous releases, but not in 9.10 anymore.

Do I need to compile mod_auth_pam from scratch, or is there a package?

cheers
Hendrik

---

### Post by cdenley on 2010-03-23
[https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-auth-pam/+bug/130099](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-auth-pam/+bug/130099)

---

### Post by fhendrik on 2010-04-12
Thanks.

Just for reference, here's a summary of what I did to make it work:

```

$ sudo apt-get install pwauth
$ cd /etc/apache2/mods-enabled
$ sudo ln -s ../mods-available/authnz_external.load .

```

and then add this section to the sites file (/etc/apache2/sites-available/...):

```

<Location /path>
  [...]

  AuthType Basic
  AuthName "Restricted Server"
  AuthBasicProvider external
  AuthExternal pwauth
  Require valid-user
  Allow from all

  [...]
<Location>

AddExternalAuth pwauth /usr/sbin/pwauth
SetExternalAuthMethod pwauth pipe

```

cheers
Hendrik

---

