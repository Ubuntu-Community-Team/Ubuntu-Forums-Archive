---
title: "Strange Apache Issue"
date: 2010-08-29
forum: Server Platforms
---

### Post by takybz on 2010-08-29
I restarted my PC to find that [http://localhost](http://localhost) wasn't resolving, so I tried restarting Apache in terminal and this is what I got:

```

Syntax error on line 204 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/mods-enabled/php4.load: No such file or directory [fail]

```

I did a quick Google for it but I couldn't find anything of use (it seems like it's a relatively rare error). Now, I have PHP5 installed and never intended on installing PHP4. In fact I can't even think of anything I have changed recently in my LAMP stack to cause Apache to do this.

in /mods-enabled I have the php4.load and php4.conf files in red. There are also similar files for PHP5 (which are not red).

The lines that the error is referring to in the apache configuration file look like this

```

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

```

I hate to just register here and ask for help (as my first post), although I Google everything and always end up here. This is the first time I've actually found an error that didn't have a thread and that I couldn't figure out for myself so I've never had to even register.

I would really appreciate if someone could help me get this solved!

---

### Post by James78 on 2010-08-29
As it says, the .load is missing.

With Apache modules, when they're in the folder mods-enabled, there's 2 files. For example, php5.load, and php5.conf

This is what my files show:
php5.load
```
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

php5.conf
```
<IfModule mod_php5.c>
    <FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>
```

So, this is what you do. To replace php4.load is easy, just find the .so, and create a file php4.load that says what my .load file says, except having the path replaced with the right one.

Also, one thing to note is this... If the module is enabled, there's 2 files in mods-enabled, the php4.conf, and the php4.load. Now, if those files aren't in mods-enabled, the module isn't enabled. Now look under mods-available, and all the available modules are there.

Your missing file MAY be in mods-available, and if it is, you can just copy it over.

You could try something like:
```
sudo a2dismod php4
sudo a2enmod php4
```
And that might fix it. Otherwise, check above for the solutions.

Edit: To disable php4, just "sudo a2dismod php4", then enable php5, "sudo a2enmod php5", although, php5 is probably already enabled. Anyways, just make sure the files are correct like I said above. Good luck!

---

### Post by takybz on 2010-08-30
Just for reference, I did what you suggested, edited the file /etc/apache2/mods-enabled/php.conf and replaced it with this

```

<IfModule mod_php4.c>
    <FilesMatch "\.ph(p3?|tml)$">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>
    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    <IfModule mod_userdir.c>
        <Directory /var/www>
            php_admin_value engine Off
        </Directory>
    </IfModule>
</IfModule>

```

LAMP stack is working properly again, thanks!

---

