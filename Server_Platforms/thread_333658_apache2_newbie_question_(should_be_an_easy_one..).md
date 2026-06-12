---
title: "apache2 newbie question (should be an easy one..)"
date: 2007-01-07
forum: Server Platforms
---

### Post by igeterrors on 2007-01-07
I want to be able to browse to localhost and see whatever home page I have set for myself there, whether it be index.html or index.php or whatever. Instead, localhost redirects to the /apache2-default/ directory and shows the apache2 success page.  

I mean, if I manually type into my browser "http://localhost/index.html" then yes, I will see my page, but if I just type "localhost" it redirects.  

Must be an apache2 configuration thing but I can't find where to change it.

Oh, and I am putting the files in /var/www/

Thanks.

---

### Post by kebes on 2007-01-07
Hmm... I think the way to fix it is to edit the file:
/etc/apache2/sites-available/default

(You need to be root so do "sudo nano /etc/apache2/sites-available/default").

In it you'll see a section like this:
```

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

```

Make sure that last line "RedirectMatch" is commented-out with a #
Then save the file, and restart your server:

sudo /etc/init.d/apache2 restart


Now it should work the way you want/expect.

---

### Post by nucrebain on 2007-01-07
This is the same problem I was running into and doing the edit helped.
Don't forget to change the permissions of the dir: .../www/ to user group www-data with full read write privilages otherwise you wont be able to view your pages.

---

### Post by igeterrors on 2007-01-08
> **kebes said:**
> Make sure that last line "RedirectMatch" is commented-out with a #


Yep, that did it.  It's great when the fix requires typing just a single character.  

Thanks for your help!

---

