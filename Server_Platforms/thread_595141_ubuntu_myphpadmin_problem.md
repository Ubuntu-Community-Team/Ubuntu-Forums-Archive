---
title: "ubuntu myphpadmin problem"
date: 2007-10-28
forum: Server Platforms
---

### Post by u_kraze on 2007-10-28
hi 


i have a problem whereby i installed webmin already and well i wanted to install phpmyadmin for some reason. anyway i got it installed and i followed a guide because i had teh same problem with the phpmyadmin not in the /vawr/www/ directory. 

Anyway i linked the phpmyadminfile from usr/share/phpmyadmin to /var/www/phpmyadmin.

When i try to go to the login page it shows this..

```

http://bdg.dyndns.org/3.png
```

can someone tell me whats up here thanks alot,..***link doesnt work nemore because i screwed up the server but iwill try to gt it up. Basically it says that the two files the header and footer are not present in the phpmyadmin folder
when i browse to this folder both of the files can be found there.

---

### Post by Peter Riche on 2007-10-29
Not sure I understood your problem, but if I did, it will be solved ;)

Why do you want phpmyadmin to be present in /var/www ???
As far as I remember, phpmyadmin files are in /usr/share/phpmyadmin and apache serves it because during phpmyadmin install, a phpmyadmin.conf is created in /etc/apache2/conf.d/ (making an apache alias /phpmyadmin)

After the installation, instead of looking to /var/www with nautilus and searching for guides because you can't see anything, just use firefox and get to localhost, you will see a phpmyadmin link, so you can also use [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) even if you can't see anything in /var/www

So I think now you just have to delete your link in /var/www and go to localhost with firefox

---

### Post by doogy2004 on 2008-04-15
> **Peter Riche said:**
> After the installation, instead of looking to /var/www with nautilus and searching for guides because you can't see anything, just use firefox and get to localhost, you will see a phpmyadmin link, so you can also use [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) even if you can't see anything in /var/www

Thanks for the info, I don't want to have to remember to type that in so I just made an empty folder /var/www/phpmyadmin/

Reload apache

So when I go to [http://localhost/](http://localhost/)  I get the index of /var/www/ and it shows the phpmyadmin folder.  When I click on the link it goes right to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  Just a suggestion for those who don't want to remember the link and are using the generic index page.

---

