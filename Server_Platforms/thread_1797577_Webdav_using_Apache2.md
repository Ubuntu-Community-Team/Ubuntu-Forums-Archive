---
title: "Webdav using Apache2"
date: 2011-07-05
forum: Server Platforms
---

### Post by and3p on 2011-07-05
Hello!

I've been struggling with this for a week with no luck, so I hope somebody could help me.
The thing is I have to build a Webdav server on Ubuntu 10.04 which could be easily accessible from Windows XP and 7 machines. So far I've managed to enable necessary modules and have basic Webdav server running. Now I need to restrict access rights for certain users.

Here is our folders tree:
-Folder1[INDENT]-SubFolder1[INDENT]+SubSubFolder1
[/INDENT][INDENT]File1.txt
[/INDENT][INDENT]File2.txt
[/INDENT][/INDENT][INDENT]-SubFolder2
[/INDENT][INDENT]-SubFolder3
[/INDENT]-Folder2[INDENT]+SubFolder4
[/INDENT]Scenario is simple:

[LIST]
[*]User1 and User2 are admins so they have full access rights in entire server
[*]All other _valid_ users (no anonymous here) can browse top folders and have full access rights inside SubFolders.
[/LIST]
Here is how my configuration file looks like so far:
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName example.com

        DocumentRoot /var/www/webdav

        DAVLockDB /etc/apache2/webdavkaccess/DAVLock

        <Directory />
                Dav On
                Options Indexes
                AllowOverride None
                Order allow,deny
                Allow from all
                AuthType Digest
                AuthName "webdav"
                AuthDigestDomain / http://example.com
                AuthDigestProvider file
                AuthUserFile /etc/apache2/webdavkaccess/.htpasswd

                BrowserMatch "MSIE" AuthDigestEnableQueryStringHack=On
                <Limit GET PROPFIND OPTIONS>
                        Require valid-user
                </Limit>
                <LimitExcept GET PROPFIND OPTIONS>
                        Require user User1 User2
                </LimitExcept>
        </Directory>
        ErrorLog /etc/apache2/webdavklogs/error.log
        LogLevel debug
        CustomLog /etc/apache2/webdavklogs/access.log vhost_combined
</VirtualHost>

```All attempts so far gave very strange results (i.e. valid users can delete but not create collections in SubFolders) so I'm asking if somebody could post how Limit and LimitExcept should look like and where they should be placed to make it work.

Thank you!

---

### Post by and3p on 2011-07-05
One more question:
Is it possible to make apache move files and folders to another directory instead of deleting it when using DELETE method?

---

