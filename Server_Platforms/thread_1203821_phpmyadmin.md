---
title: "phpmyadmin"
date: 2009-07-03
forum: Server Platforms
---

### Post by keemosabi on 2009-07-03
I setup an Apache server and used apt-get to install Apache2, PHP, MYSQL, phpmyadmin, etc.  However, when I go to localhost/phpmyadmin I do not get a page not found error.  However, when I go to just lcoalhost I get the phpinfo() page as I put a php file with that command in the /var/www directory.  There is no phpmyadmin information in the /var/www so did I do something wrong?

---

### Post by credobyte on 2009-07-03
Not sure if understand your problem correctly, but - **phpmyadmin** is located at [COLOR=Blue]/etc/phpmyadmin/[/COLOR] and uses [COLOR=Blue]/etc/phpmyadmin/apache.conf[/COLOR] as Apache configuration file ( so you shouldn't keep it in [COLOR=Blue]/var/www/[/COLOR] ).

---

### Post by keemosabi on 2009-07-08
> **credobyte said:**
> Not sure if understand your problem correctly, but - **phpmyadmin** is located at [COLOR=Blue]/etc/phpmyadmin/[/COLOR] and uses [COLOR=Blue]/etc/phpmyadmin/apache.conf[/COLOR] as Apache configuration file ( so you shouldn't keep it in [COLOR=Blue]/var/www/[/COLOR] ).
I simply want to open the phpmyadmin windows in my browser.  I can access [http://localhost/](http://localhost/) which is the phpinfo() page I set up, but I don't know how to get to phpmyadmin.  I tried [http://localhost/phpmyadmin](http://localhost/phpmyadmin) but I got a 404 Not Found error.

---

### Post by solitaire on 2009-07-08
Did you try: 

[http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php)

Sometimes you have to put the full address in.

---

### Post by wojox on 2009-07-08
In terminal

```
sudo gedit /etc/apache2/apache2.conf
```

Look for:

Include /etc/phpmyadmin/apache.conf

If it's not there add it.

Save & then

```
sudo /etc/init.d/apache2 restart
```

Then try:

[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

