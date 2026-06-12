---
title: "cannot get roundcube/phpmyadmin WebGUIs to load"
date: 2016-07-23
forum: Server Platforms
---

### Post by Heeter on 2016-07-23
Hi all,

This is for a working, production Owncloud/Email/Webserver sitting on a LAMP Ubuntu 14.04, running full time ssl virtual hosts/domains

I cannot get roundcube/phpmyadmin WebGUIs to load (they are going 404). It used to work properly until a few months ago.

I have tried to uninstall and reinstall them a few times, to no avail.

They used to work under any domain that I pulled them up from ([https://domain1.com/roundcube](https://domain1.com/roundcube), [https://domain2.com/roundcube](https://domain2.com/roundcube), etc, etc)

Any help would be greatly appreciated

Regards

---

### Post by houstonbofh on 2016-07-25
What did you change?
What have you tried?
What do the logs say?

If people have to struggle just to get the basic information, they often do not bother to try and help you.

---

### Post by Heeter on 2016-07-27
> **houstonbofh said:**
> 
What did you change?

I had to reinstall Apache and PHP due to a corrupted PHP install.

> **houstonbofh said:**
> 
What have you tried?

I have tried purging/reinstalling both applications multiple times.

> **houstonbofh said:**
> 
What do the logs say?

I have checked the apache logs but find nothing worth reporting

> **houstonbofh said:**
> 
If people have to struggle just to get the basic information, they often do not bother to try and help you.

My Apologies, I will try to better describe the situation next time.

---

### Post by darkod on 2016-07-27
Can you list the contents of your /etc/phpmyadmin folder?

Do you have apache.conf in there?

---

### Post by Heeter on 2016-07-27
> **darkod said:**
> Can you list the contents of your /etc/phpmyadmin folder?

Do you have apache.conf in there?

Hi darkod

Yes I do have that apache.conf file, here is the first couple of lines:

```

hpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php

        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_admin_flag allow_url_fopen Off
                php_value include_path .
                php_admin_value upload_tmp_dir /var/lib/phpmyadmin/tmp
                php_admin_value open_basedir /usr/share/phpmyadmin/:/etc/phpmya$
        </IfModule>

```

---

### Post by Graham_Willis on 2016-07-30
[QUOTE="Heeter"]I cannot get roundcube/phpmyadmin WebGUIs to load (they are going 404). It used to work properly until a few months ago.[/QUOTE]

Please:

1. post the output of **ls -la /etc/apache2/conf-available | grep -i phpmyadmin **.
2. check what addresses you see after issuing **netstat -an | grep 80 **, try to load phpmyadmin using all of these addresses both from the server (use **wget** or whatever you like). Report back the results.
3. send the output of case-insensitive grepping apache logs through phpmyadmin. I know that you wrote that there is nothing of interest, but I think they may prove useful anyway.

---

