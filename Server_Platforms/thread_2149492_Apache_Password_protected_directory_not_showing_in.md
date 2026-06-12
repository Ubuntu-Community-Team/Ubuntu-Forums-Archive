---
title: "Apache Password protected directory not showing in index"
date: 2013-05-28
forum: Server Platforms
---

### Post by Loki57701 on 2013-05-28
Hello, 


I'm using Apache to serve up some content on my home network, and I'm running into an issue with a password protected directory now showing up in the index.

```

**apachectl -v**
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Mar 15 2013 14:04:36

```

```

**apachectl -M**
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 version_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 auth_digest_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 reqtimeout_module (shared)
 setenvif_module (shared)
 status_module (shared)
Syntax OK

```

```

<Directory /var/www>
Options Indexes Includes FollowSymLinks Multiviews
IndexOptions FancyIndexing IconsAreLinks NameWidth=*
HeaderName header.html
IndexIgnore *.html *.css *.jpg *.ini
</Directory>

<Directory /var/www/Music>
Options Indexes Includes FollowSymLinks Multiviews
IndexOptions FancyIndexing IconsAreLinks NameWidth=*
IndexIgnore *.html *.css *.jpg *.ini
HeaderName ../header.html
</Directory>

<Directory /var/www/Pictures>
Options Indexes Includes FollowSymLinks Multiviews
IndexOptions FancyIndexing IconsAreLinks NameWidth=* 
IndexIgnore *.html *.css *.ini
HeaderName ../header.html
AllowOverride AuthConfig
Authtype Digest
AuthName "Pictures"
AuthDigestDomain example.home.net/Pictures
AuthDigestProvider file
AuthUserFile /etc/.htdigest
Require valid-user
</Directory>

```

I would like the Pictures directory to show up, but all I get is:

[IMG]http://i.imgur.com/PeeXTfd.png[/IMG]

I've looked into IndexOption ShowForbidden, but that didn't seem to work. 

I can view the Pictures directory if I type out the path in the browser, or if I remove the password protection.

Admittedly I'm not an expert on apache, but I feel like I'm missing something obvious..

Any suggestions?

**Edit:**

I should also mention that I'm using symbolic links - although I'm not sure that it makes a big difference.

```

**ls -l /var/www**
total 4
-rw-r--r-- 1 root root 84 May 28 23:41 header.html
lrwxrwxrwx 1 root root 17 May 27 20:57 Music -> /home/$user/Music
lrwxrwxrwx 1 root root 20 May 28 14:56 Pictures -> /home/$user/Pictures

```

---

### Post by SeijiSensei on 2013-05-29
Does the www-data user have access to the /home/user/Pictures?  The directory should have 755 permissions and the files 644 permissions.  

What do you see in /var/log/apache2/error.log?

---

