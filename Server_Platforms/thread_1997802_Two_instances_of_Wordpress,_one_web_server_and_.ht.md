---
title: "Two instances of Wordpress, one web server and .htaccess"
date: 2012-06-05
forum: Server Platforms
---

### Post by OliverHaslam on 2012-06-05
Hi,

I have one wordpress blog at oliverhaslam.com, with the files housed in /var/www/wordpress. I have the .htaccess file in /var/www and that tells the install to look in the wordpress folder for all the install files. It's how the WP docs said to do it if you don't want the files to live in root, and it works.

Now I fancy installing another WP blog, and buy a new domain to go along with it. How do I deal with this?

I can buy the domain, say testdomain.com. I can isntall WP in /var/www/testdomain for example, but now what? How do I handle the .htaccess file and the virtualhosts?

Any tips?

Thanks.

---

### Post by sandyd on 2012-06-06
> **OliverHaslam said:**
> Hi,

I have one wordpress blog at oliverhaslam.com, with the files housed in /var/www/wordpress. I have the .htaccess file in /var/www and that tells the install to look in the wordpress folder for all the install files. It's how the WP docs said to do it if you don't want the files to live in root, and it works.

Now I fancy installing another WP blog, and buy a new domain to go along with it. How do I deal with this?

I can buy the domain, say testdomain.com. I can isntall WP in /var/www/testdomain for example, but now what? How do I handle the .htaccess file and the virtualhosts?

Any tips?

Thanks.

Just create a new name-based virtualhost and set the root as a  different directory, like /var/www/testdomain. 

The htaccess in /var/www will not affect a seperate virtualhost with a root in one of its subdirectories.

If I were you, I would reconfigure the setup to be something like this. Placing the root folder of the domain in the root folder of another domain is bad practice.

Folders in /var/www
[LIST]
[*]oliverhaslam.com
[*]testdomain.com
[*]testdomain2.com
[/LIST]

Use name-based virtual hosts to set the root to each folder.

i.e.
/var/www/oliverhaslam.com is the root for the oliverhaslam.com virtualhost

/var/www/testdomain.com is the root for the testdomain.com virtualhost

.etc .etc.

This is less confusing.

---

