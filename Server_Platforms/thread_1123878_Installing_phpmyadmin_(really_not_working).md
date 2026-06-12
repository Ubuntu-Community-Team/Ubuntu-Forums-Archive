---
title: "Installing phpmyadmin (really not working)"
date: 2009-04-12
forum: Server Platforms
---

### Post by MinatureCookie on 2009-04-12
Hey again guys..
Stuck again, trying to access phpmyadmin ¬_¬

Basically, I've done this in the Terminal:
```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin
```

None throw up any errors, it's all happy with itself.
I can see PHP through [http://localhost/](http://localhost/) - fine.
I go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and I get a 404 Not Found... Which leaves me struggling to understand what to do now, as all the tutorials online just say to do what I've done, and no more...

(also how does sudo apt-get install work? Seems pretty magic to me that the Terminal just knows where to look to get the files to install it with :S)

---

### Post by Iowan on 2009-04-12
> **MinatureCookie said:**
> (also how does sudo apt-get install work? Seems pretty magic to me that the Terminal just knows where to look to get the files to install it with :S)**apt-get** is a package handling utility that knows what to do with the files, etc.  There is a list of repositories (repo's for short) - though I can't remember where the list is kept - that tells **apt-get** where to go get the files.

I'll fire up my server to see if I can find any phpmyadmin info for you.
Unfortunately, nothing really helpful... If I go to history (on Elinks), [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) takes me to the login page.
Although... if I enter [http://localhost/](http://localhost/), I get the "It works!" page.> I can see PHP through [http://localhost/](http://localhost/) - fine.
What do you see?

---

### Post by MinatureCookie on 2009-04-12
I did previously see the "It works!" page, but I changed the root directory to another folder that contains all of my PHP files, and they all work through the [http://localhost/](http://localhost/) (as in the actual PHP scripting works).
Is the change of the directory possibly the cause of the problem?

---

### Post by Iowan on 2009-04-14
Which root directory did you change - ServerRoot or DocumentRoot?

---

### Post by Kareeser on 2009-04-14
Possibly. If apt installed phpmyadmin in /var/www, in which case that directory is inaccessible now that you've changed the DocumentRoot.

Hell, I didn't even KNOW phpmyadmin was in the repositories... I just download the files straight from the website :)

Cool.

---

### Post by jms1989 on 2009-04-14
May I be of assistance.

Add this to your web config file in /etc/apache2/sites-enabled at the end but before </VirtualHost>

```

    Alias /phpmyadmin/ "/usr/share/phpmyadmin/"
    <Directory "/usr/share/phpmyadmin/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride All
        Order deny,allow
        Allow from all
    </Directory>

```

You can change /usr/share/phpmyadmin/ to the actual location of phpmyadmin. That will work the the one from the repos. Then just visit [http://server/phpmyadmin](http://server/phpmyadmin) after you restart apache to see if it works.

Cheers!

---

