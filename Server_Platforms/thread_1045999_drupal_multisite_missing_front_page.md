---
title: "drupal multisite missing front page"
date: 2009-01-21
forum: Server Platforms
---

### Post by prkos on 2009-01-21
I had multisite drupal installed on LAMP on fedora. Now I want to migrate it to ubuntu, I have apache2, php5, mysql and drupal up and (seemingly) working but there a couple of weird symptoms I need help with: 

Going to [http://mysite.local/](http://mysite.local/) I just get the apache "It works!" page. 
Going to [http://mysite.local/drupal/](http://mysite.local/drupal/) I get Page not found (in correct drupal theme style)

On fedora when I went to [http://mysite.local/](http://mysite.local/) I got the front page, how can I get it here? All the other links seem to work ok (for example [http://mysite.local/admin](http://mysite.local/admin)) just the front page is missing. 

I guess it might be my virtual hosts configuration, it's different on ubuntu using sites-enabled, maybe I did something wrong there?

---

### Post by Sef on 2009-01-21
moved to server platforms.

---

### Post by prkos on 2009-01-21
It was about mysql users apparently, I created a new user and gave it all permissions for the database in question, and updated the settings.php file to reflect that. 
Before the user was root.

---

