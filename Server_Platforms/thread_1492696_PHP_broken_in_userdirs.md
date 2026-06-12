---
title: "PHP broken in userdirs"
date: 2010-05-25
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-05-25
I have apache2 installed on my laptop with php5 and userdirs enabled so I can do development.  It was working fine in karmic, but somewhere between the upgrade to lucid or more recently, php stopped working.

PHP scripts in /var/www work fine.  I can go to [http://localhost/somescript.php](http://localhost/somescript.php) and it executes as expected.

But scripts in ~/public_html do not.  They prompt me to download a PHTML file.  Yes, I am accessing from [http://localhost/~myusername/](http://localhost/~myusername/), not directly through the file system.

I was looking through configs trying to solve this, and noticed the php5.conf file (in /etc/apache2/confs-available) is quite a bit more verbose than in debian stable.  On Lucid it reads:

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

Naturally, I tried commenting out the indicated section and restarting apache, but it didn't fix the problem.

No errors show in /var/log/apache2/error.log (nothing unusual or seemingly related, that is).

I've googled a few things, but haven't turned up anything on this issue.  Any wisdom?

---

### Post by BoneKracker on 2010-05-25
I doubt this is it, since your upgrade probably didn't involve fstab, but I don't suppose you're mounting a separate /home partition with -o noexec?

---

### Post by lykwydchykyn on 2010-05-25
> **BoneKracker said:**
> I doubt this is it, since your upgrade probably didn't involve fstab, but I don't suppose you're mounting a separate /home partition with -o noexec?

Nope; and my ~/bin directory works fine (place where I keep custom scripts).

I should add, if I just add a symlink of ~/public_html to /var/www, it works fine.  So it's something with userdirs.

---

### Post by lykwydchykyn on 2010-05-25
I just found this post:
[http://ubuntuforums.org/showthread.php?p=9271711](http://ubuntuforums.org/showthread.php?p=9271711)

[s]So I'm not the only one.  But the solution didn't work for me.  Maybe I'll clear the cache and try again.[/s]

Ok, seems I just needed to clear the cache after making that change to php5.conf.  It works now.

---

