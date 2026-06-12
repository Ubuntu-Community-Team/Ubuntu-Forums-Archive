---
title: "Problem with PHP"
date: 2009-12-23
forum: Server Platforms
---

### Post by Vegan on 2009-12-23
I have some PHP code, but its just being displayed instead of being acted upon. I wonder if I need to change my Apache config files to support the code?

---

### Post by wsonar on 2009-12-23
Did you install LAMP server or install apachee and php seperate?

have you installed libapache2-mod-php5?

---

### Post by Vegan on 2009-12-23
That is installed. I wonder if PHP parser is not enabled?

Does not make any sense.

---

### Post by HighCommander540 on 2009-12-23
> **Vegan said:**
> That is installed. I wonder if PHP parser is not enabled?

Does not make any sense.

You need to check whether Apache is actually loading PHP or not. 

Navigate here "/etc/apache2/mod-enabled/". It should be a folder of sym-links. If you don't see two files named "php5.load" and "php5.conf". Then PHP is not enabled on your server yet.

To enable run this:

```
a2enmod
```

Then it will ask you what mod to enabled and type php5.

---

### Post by Vegan on 2009-12-23
ubuntu@ubuntu:~$ a2enmod
Your choices are: actions alias asis auth_basic auth_digest authn_alias authn_anon authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_default authz_groupfile authz_host authz_owner authz_user autoindex cache cern_meta cgi cgid charset_lite dav dav_fs dav_lock dbd deflate dir disk_cache dump_io env expires ext_filter file_cache filter headers ident imagemap include info ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http rewrite setenvif speling ssl status substitute suexec unique_id userdir usertrack version vhost_alias
Which module(s) do you want to enable (wildcards ok)?
php5
Module php5 already enabled

Any other ideas why my ad code is not being parsed?

I also checked /etc/apache2/mods-enabled and the symlinks are all fine.

Wonder if 9.10 is simply useless?

---

### Post by Vegan on 2009-12-23
Duh finally realized my problem....

Was missing the <? ?> tags in the file to enable the parser.

:guitar:

Well now the fun of working on the styles, fooey.

---

