---
title: "where is httpd"
date: 2009-10-20
forum: Server Platforms
---

### Post by zhangw on 2009-10-20
i install apache with apt-get install command,but where is the httpd command.how can i use "httpd -v", "httpd -l"...?

---

### Post by dominiquec on 2009-10-20
On Ubuntu, the Apache web server package is apache2.  So to install it:

sudo apt-get install apache2

To start, stop, or restart the service:

sudo /etc/init.d/apache2 start | stop | restart

Default root directory is in /var/www/

---

### Post by zhangw on 2009-10-20
how to display the apache version?   
how to list the modules installed in apache?
if install with tarball,i can use /etc/init.d/httpd -v and /etc/init.d/httpd -l
on ubuntu ,how to get it

---

### Post by Lars Noodén on 2009-10-20
> **zhangw said:**
> how to display the apache version?   
how to list the modules installed in apache?
if install with tarball,i can use /etc/init.d/httpd -v and /etc/init.d/httpd -l
on ubuntu ,how to get it

You can find the version of the package you have installed this way:
```

dpkg -l apache2
# or
apt-cache policy apache2
# or
/usr/sbin/apache2 -v

```

The first two are best.

> **zhangw said:**
> 
how to list the modules installed in apache?



**a2emod** with no parameters, will give you a full list of the installed modules.  For example:

[INDENT][FONT="Courier New"]
$ a2enmod
Your choices are: actions alias asis auth_basic auth_digest authn_alias authn_anon authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_default authz_groupfile authz_host authz_owner authz_user autoindex cache cern_meta cgi cgid charset_lite dav dav_fs dav_lock dbd deflate dir disk_cache dump_io env expires ext_filter file_cache filter headers ident imagemap include info ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http rewrite setenvif speling ssl status substitute suexec unique_id userdir usertrack version vhost_alias
Which module(s) do you want to enable (wildcards ok)?
[/FONT][/INDENT]

a2enmod and a2dismod activate or deactivate the modules.

> **zhangw said:**
> if install with tarball...


Please don't mess with installing via tarballs.  The package manager will keep things much more orderly for you -- automatically.

The easiest way to get the apache modules is to use the package manager.  You can use it directly via the shell, using **apt-get**.  However, aptitude is a nice UI for it, and even more people prefer the graphical UI provided by synaptic or kpackage.

---

