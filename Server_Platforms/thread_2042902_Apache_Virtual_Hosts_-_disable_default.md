---
title: "Apache Virtual Hosts - disable default"
date: 2012-08-15
forum: Server Platforms
---

### Post by mcc28x on 2012-08-15
Hi,

I have created 3 virtual hosts e.g. /etc/apache2/sites-available/mynewsite and used a2ensite and restarted apache. I can browse to the site no problem.

I want to disable the default site /etc/apache2/sites-available/default but when I issue a2dissite default and restart apache none of the virtual hosts can be accessed either?

How do I do this?

cheers

Mark

---

### Post by Habitual on 2012-08-16
[U]n/m
[/U]

---

### Post by SeijiSensei on 2012-08-16
You need to have some virtual host that will handle requests that don't match a name-based virtual host.  Trust me, you'll see requests in your server logs for requests against your server IP, for instance, from machines trying to find holes in your configuration.  Just leave the default there to give requests like these the "It Works!" page.

---

### Post by Wim Sturkenboom on 2012-08-16
I've created my own default page that simply contains urls to the other sites.

---

### Post by mcc28x on 2012-08-16
Okie dokie, cheers

---

