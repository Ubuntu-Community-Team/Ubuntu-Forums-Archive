---
title: "[SOLVED] new to apache - question"
date: 2008-10-06
forum: Server Platforms
---

### Post by vitotol on 2008-10-06
hello guys, i got apache 2 running in a pc. i haven't define a domain name so when i type the ip in the browser i got the default apache page shown "it works". the problem is that when i create an index page in a user when i hit ip/~user the page is not shown. is there any configuration i have to do in the apache files???:confused:

---

### Post by lykwydchykyn on 2008-10-06
Yeah that's not set up by default.  I think you just need to enable the userdir module and reload apache.

```

a2enmod userdir
/etc/init.d/apache2 restart

```

---

### Post by vitotol on 2008-10-06
thanx man, it worked!!!

-

i'd also like to know what about the main index ??? i replaced the "it works" default index but where do they usually place the main index??? and how i define this directory in the apache configuration???

---

### Post by mbeach on 2008-10-06
look to the DocumentRoot directive in /etc/apache2/sites-available/default file which will typically point to /var/www.  

for your userdir folder setting, it'll be in /etc/apache2/mods-available/userdir.conf

---

