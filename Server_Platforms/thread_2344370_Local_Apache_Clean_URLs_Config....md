---
title: "Local Apache Clean URLs Config..."
date: 2016-11-24
forum: Server Platforms
---

### Post by b14speedfreak on 2016-11-24
Hi All,

I have literally being beating myself up with this for two days, and I carn't work out what I am doing wrong.

I have installed a Lamp stack on Ubuntu 16.04 LTS.  The version of apache I am using is 2.4.18, I am using PHP 7.0.8-0, and I am using MYSQL 5.7.16-0.

As I said previously I am having a lot of problems getting Apache to use clean urls.  The main idea is to be able to use it with a Drupal 7 install locally.  

I have the rewrite module installed.  When I run apachectl -M I get the following:

```
Loaded Modules:
 core_module (static)
 so_module (static)
 watchdog_module (static)
 http_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 unixd_module (static)
 access_compat_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 filter_module (shared)
 mime_module (shared)
 mpm_prefork_module (shared)
 negotiation_module (shared)
 php7_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
```

In the /etc/apache2/apache2.conf file I have the following:
```
<Directory /var/www>
        Options Indexes FollowSymLinks
        #AccessFileName .htaccess
        Require all granted
</Directory>
```

If I try to uncomment the AccessFileName .htaccess in order to get .htaccess to work on restarting the apache it alls falls over and asks for it to be removed.  This is actually been put in the config file below in the standard install:

```
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
# 

AccessFileName .htaccess
```

If I can get apache to work with .htaccess files (which at the moment it won't) then the drupal install should in theory sort it out (it has a .htaccess file at root level as standard install).

I tried to turn on RewriteLog option.  However again this seems to be failing.

Has anyone got any ideas and could help?

Thanks in advance,

Mark.

---

### Post by b14speedfreak on 2016-11-25
Ok, so I did a full clean install, which took a lot more effort than I had imagined.

Reading the documentation really closely and playing a fair bit has resulted in a working install.

Thanks for bearing with me folks!

Mark.

---

