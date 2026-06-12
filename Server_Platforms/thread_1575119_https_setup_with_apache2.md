---
title: "https setup with apache2"
date: 2010-09-15
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-15
I have a site called [http://www.mysite.com/](http://www.mysite.com/) configured in apache virtual hosting.

Is it possible to make it use https like the below
[https://www.mysite.com](https://www.mysite.com)

Please anyone give me step by step guide

Thank you!

---

### Post by Ryan Dwyer on 2010-09-15
sudo a2enmod ssl
sudo nano /etc/apache2/sites-available/default-ssl # set DocumentRoot etc
sudo a2ensite default-ssl
sudo service apache2 restart

That will be using a self signed certificate which most browsers will show a warning for. To use "legit" SSL (no browser warnings) then you need to purchase an SSL certificate from someone.

---

