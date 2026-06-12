---
title: "Apache2 Hell"
date: 2007-06-27
forum: Server Platforms
---

### Post by crazyjx23 on 2007-06-27
I've been working with getting a local web server going. I'm running in to trouble when trying to put up the website. I keep getting the default index listing of all the files in my /var/www directory.  Is my configuration wrong?? How do I get all my files to run as html instead of just sitting in that stupid index?

---

### Post by Gruelius on 2007-06-28
You need to have a Index.html or .php or something else.
If you want to have a look into the apache config file you can set what the home page is (the page it goes to first)

---

### Post by crazyjx23 on 2007-06-28
Yea that was the default, but I cleaned it all out hoping that it will display my page without that index stuff.

---

### Post by asmweb on 2007-06-28
if you use firefox clear off the cache sometimes causes wrong redirections

---

### Post by crazyjx23 on 2007-06-28
Cache clears automatically and I still have problems.

---

### Post by crazyjx23 on 2007-06-28
Ok updated....Now it gives me a access forbidden message when I go to the server. Here is what I'm thinking I want to do. I just want to delete this site configuration and files, and build a new one. Is this better? Is there a good tutorial or guide to make the configuration files for a site?

---

### Post by az on 2007-06-28
> **crazyjx23 said:**
> How do I get all my files to run as html instead of just sitting in that stupid index?

Either change the default document root to the subdirectory that your site is in (in /var/www) or create a different site.

Copy the apache-default site in /etc/apache/sites-available to another name other than default and edit it to point to your web site directory.  The enable that site

sudo a2ensite myothersite

sudo /etc/init.d/apache2 restart

---

### Post by crazyjx23 on 2007-06-29
Thanks

---

