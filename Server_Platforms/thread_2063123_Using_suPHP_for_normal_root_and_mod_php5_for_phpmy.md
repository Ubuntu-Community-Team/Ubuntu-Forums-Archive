---
title: "Using suPHP for normal root and mod_php5 for phpmyadmin (and other /usr/share roots)"
date: 2012-09-26
forum: Server Platforms
---

### Post by chancezeus on 2012-09-26
Hi all,

Since suPHP by default disallows access to /usr/share and I do not want to change the owner of all /usr/share installed applications, I modified the config file php5.conf to allow for suPHP and mod_php5 coexistence.
The result is below:
```

<IfModule mod_php5.c>
    <IfModule !mod_suphp.c>
        <FilesMatch ".+\.ph(p[345]?|t|tml)$">
            SetHandler application/x-httpd-php
        </FilesMatch>
        <FilesMatch ".+\.phps$">
            SetHandler application/x-httpd-php-source
            # Deny access to raw php sources by default
            # To re-enable it's recommended to enable access to the files
            # only in specific virtual host or directory
            Order Deny,Allow
            Deny from all
        </FilesMatch>
        # Deny access to files without filename (e.g. '.php')
        <FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
            Order Deny,Allow
            Deny from all
        </FilesMatch>
    </IfModule>

    # Running PHP scripts in user directories is disabled by default
    # 
    # To re-enable PHP in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    #<IfModule mod_userdir.c>
    #    <Directory /home/*/public_html>
    #        php_admin_value engine Off
    #    </Directory>
    #</IfModule>
    <IfModule mod_suphp.c>
        <Directory /usr/share>
            <FilesMatch ".+\.ph(p[345]?|t|tml)$">
                SetHandler application/x-httpd-php
            </FilesMatch>
            <FilesMatch ".+\.phps$">
                SetHandler application/x-httpd-php-source
                # Deny access to raw php sources by default
                # To re-enable it's recommended to enable access to the files
                # only in specific virtual host or directory
                Order Deny,Allow
                Deny from all
            </FilesMatch>
            # Deny access to files without filename (e.g. '.php')
            <FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
                Order Deny,Allow
                Deny from all
            </FilesMatch>
        </Directory>
    </IfModule>
</IfModule>

```

If using mod_userdir, it might also be required to set ```
check_vhost_docroot=false
``` in order to use /home/*/public_html (otherwise the public_html has to be a subdir of the vhost_docroot

Yours sincerely,
ChanceZeus

---

