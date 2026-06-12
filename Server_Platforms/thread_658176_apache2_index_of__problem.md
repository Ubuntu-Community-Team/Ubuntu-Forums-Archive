---
title: "apache2 index of / problem"
date: 2008-01-04
forum: Server Platforms
---

### Post by gryzzly on 2008-01-04
Hey people, just installed apache2 and everything looks fine and works, except this thing: 
in /var/www/ i have folder "www.test.com" which i can see from everywhere but not from [http://localhost](http://localhost) - which shows me "index of /" and it actually shows me all files and folders from /var/www/ except this one. Any ideas what i can do? (sorry for my english)

---

### Post by reckless2k2 on 2008-01-04
there's a few ways to approach this but basically you can just copy the contents from your folder into /var/www/ and restart apache and it'll show your page. 

you will need to get more in depth with apache to understand the nuances but your "root" of apache is /var/www/ so it's looking for a .html file and when it finds none it displays an index because you have folders in there.

---

### Post by reckless2k2 on 2008-01-04
sorry i missed what you were saying. i mis-posted. 

i would check the permissions as well as restart apache and refresh the viewing broswer.

---

### Post by gryzzly on 2008-01-04
> **reckless2k2 said:**
> sorry i missed what you were saying. i mis-posted. 

i would check the permissions as well as restart apache and refresh the viewing broswer.

Thanks for replying. What permissions i need to see that folder? now for this folder permissions are the same as for "phpMyadmin" folder, which is being showed normally.

---

### Post by reckless2k2 on 2008-01-04
run this from the terminal:
```

ls -l /var/www
```

that should give you info. the idea being that you want the other directories to match. also, have you restarted the apache server since added that directory?

```
/etc/init.d/apache2 force-reload
```

and lastly, i would open to that page in a browser and then refresh the page once or twice so the cache is cleared viewing the latest view of that page.

---

### Post by Will_SureTalk on 2008-01-05
Installing Apache2 on Ubunto Feisty Fawn 7.04 using the 
sudo sudo apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils
 command results in an incomplete Apache2 installation. 

The following critical files are not created /etc/apache2/modules.conf and /etc/apache2/httpd.conf. 

Executing the /usr/sbin/apache2 -t command will help you identify the missing configuration components.

In addition the Synaptic package manager does not have an Apache2 package reference and executing the apt command does not enable the package manager to add it.

Although the System.Administration.Services tool picks up the apt installation of Apache it indicates that its status incorrectly.

Is there a simple solution for 7.04 or is the only solution to upgrade to 7.10?

---

