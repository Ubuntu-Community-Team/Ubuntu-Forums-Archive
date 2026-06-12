---
title: "How do I serve websites from my desktop?"
date: 2008-12-14
forum: Server Platforms
---

### Post by Maheriano on 2008-12-14
I have Ubuntu desktop installed and running as my main computer system/media centre but I also want to be able to host small websites from it. How do I set it up to serve the pages from the beginning?

---

### Post by hictio on 2008-12-14
Check [here](http://ubuntuforums.org/showpost.php?p=6327257&postcount=6)

---

### Post by Maheriano on 2008-12-15
Thanks, that was easy! Next questions:

1. How do I secure it from attacks?
2. How do I access Apache to create new databases, new mysql users, and all the other stuff you do with GoDaddy's nice GUI front end? I'm new to the webserver scene as you can tell, but I've hosted 3 sites remotely for 4 years.

---

### Post by hictio on 2008-12-15
1-
Check [mod_security](http://www.vinno.net/linux/server/how-to-install-mod-security-2-ubuntu-intrepid-810)

2-
Not sure... Perhaps using [phpMyAdmin](http://www.phpmyadmin.net/home_page/index.php)

---

### Post by Maheriano on 2008-12-15
Thanks. I figured out what I'm looking for is cPanel but can't afford a license for that. Is there anything like that for free?

---

### Post by hictio on 2008-12-15
Yeah, sure, take a look at [Webmin](http://www.webmin.com/)

---

### Post by Maheriano on 2009-01-19
Okay, got Webmin installed, works great, LAMP server is running perfectly. I installed Wordpress on it after creating some MYSQL databases and users and it looks good. My problem is that it looks terrible when viewed outside my network, like the CSS or PHP isn't loading or something. It's all text and left aligned with no images. What would cause this?

---

### Post by Maheriano on 2009-01-20
Anyone?

---

### Post by drubin on 2009-01-20
> **Maheriano said:**
> Anyone?

I think your worldpress url has been set to your internal ip address.

Under your wp-admin you need to set your blog url to be your dyndns domain name what ever it might be. 

I suggest you do this from your internal network so that it is easier to see)
[LIST]
[*]Ok login to the admin panel
[*]Click on the settings link (near the top, on the right hand side).
[*]There are a whole lot of configs/text boxes make sure "WordPress address (URL) " is your dyndnsdomainname and correct path.
[/LIST]

Let us know if that helps

---

### Post by Maheriano on 2009-01-20
> **drubin said:**
> I think your worldpress url has been set to your internal ip address.

Under your wp-admin you need to set your blog url to be your dyndns domain name what ever it might be. 

I suggest you do this from your internal network so that it is easier to see)
[LIST]
[*]Ok login to the admin panel
[*]Click on the settings link (near the top, on the right hand side).
[*]There are a whole lot of configs/text boxes make sure "WordPress address (URL) " is your dyndnsdomainname and correct path.
[/LIST]

Let us know if that helps

Genius! It worked, thanks!

---

