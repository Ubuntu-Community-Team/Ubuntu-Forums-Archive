---
title: "Problem on configuring phpmyadmin"
date: 2009-04-25
forum: Server Platforms
---

### Post by satimis on 2009-04-25
Hi folks,


Ubuntu 8.04
Apache2
phymyadmin


On running;

# apache2ctl -t```

[Sat Apr 25 07:57:02 2009] [warn] The Alias directive in /etc/apache2/sites-enabled/400-phpmyadmin at line 3 will probably never match because it overlaps an earlier Alias.
Syntax OK

```

and

# /etc/init.d/apache2 reload```

 * Reloading web server config apache2                                                 [Sat Apr 25 07:57:11 2009] [warn] The Alias directive in /etc/apache2/sites-enabled/400-phpmyadmin at line 3 will probably never match because it overlaps an earlier Alias.
                                                                                [ OK ]

```

A warning popup.


# cat /etc/apache2/sites-enabled/400-phpmyadmin```

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options Indexes FollowSymLinks
        DirectoryIndex index.php

        # Authorize for setup
        <Files setup.php>
            # For Apache 1.3 and 2.0
            <IfModule mod_auth.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            # For Apache 2.2
            <IfModule mod_authn_file.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            Require valid-user
        </Files>
        <IfModule mod_php4.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
</Directory>

```

However it doesn't affect running phymyadmin.  On the web browser of a remote machine;

[http://domain.com/phpmyadmin](http://domain.com/phpmyadmin)

can start the login page and login.


Please advise where shall I check?  How to fix the warning?  TIA


B.R.
satimis

---

