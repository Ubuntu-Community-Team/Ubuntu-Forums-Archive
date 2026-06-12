---
title: "Subversion/Apache authentication issues"
date: 2009-02-13
forum: Server Platforms
---

### Post by LPomfrey on 2009-02-13
I've been using Subversion on my server for a while now with no problems, however, as of today I am no longer able to commit any changes to my repository. Committing fails with the message:
```
Commit failed (details follow):
svn: MKACTIVITY of '/svn/project4_rivet_analyses/!svn/act/a2b76762-84db-4957-b79b-f969aa0dc964': authorisation failed (http://svn.lukepomfrey.org)
```

As far as I know I've made absolutely no changes to the server, or my client machine, aside from installing updates.

I've tried deleting ~/.subversion and the entire project from my client and checking out from the server again, but that hasn't solved it. Neither has resetting my password on the server, and neither has using mod_authz_svn instead of just blanket authorisation.

Here is the config file for the relevant Apache virtual server:
```
<VirtualHost *:80>
  ServerAlias   svn.lukepomfrey.org
  ServerAdmin   webmaster@lukepomfrey.org
  ServerSignature On

  DocumentRoot  /var/www/svn.lukepomfrey.org

  CustomLog     /var/log/apache2/svn.lukepomfrey.org-access.log combined
  ErrorLog      /var/log/apache2/svn.lukepomfrey.org-error.log
  LogLevel warn

  <Directory /var/www/svn.lukepomfrey.org>
     Options Indexes FollowSymLinks
     AllowOverride AuthConfig
     Order allow,deny
     allow from all

     AddType text/html .php .phps
     AddHandler application/x-httpd-php .php
     AddHandler application/x-httpd-php-source .phps
  </Directory>
  <Location /svn/>
  # Uncomment this to enable the repository
  DAV svn

  SVNParentPath /var/www/svn/repos/

  AuthType Basic
  AuthName "Subversion Repository"
  AuthUserFile /etc/apache2/passwd/.dav_svn
  

  # The following three lines allow anonymous read, but make
  # committers authenticate themselves. 
  <LimitExcept GET PROPFIND OPTIONS REPORT>
    Require valid-user
  </LimitExcept>

  </Location>

  <IfModule mod_proxy.c>
    ProxyVia On
    <LocationMatch "^[^/]">
      Deny from all
    </LocationMatch>
  </IfModule>
</VirtualHost>

```

Any help would be most appreciated!

---

### Post by LPomfrey on 2009-02-14
I've tracked the problem down to the fact that www-data doesn't have permission to access the password file.

The password file is owned by www-data:www-data and has permissions 644, I've tried moving the file to a subdirecory of /var/www but this hasn't solved the problem. :confused:

Edit: Solved. I hadn't set the executable bit for the folders above where the password file was.

---

