---
title: "Virtual Hosts Configurable"
date: 2011-06-11
forum: Server Platforms
---

### Post by ItsAsh on 2011-06-11
Hello Community!

I have installed bind9 for DNS. I have also installed Apache2, PHP5, MySQL, and correctly configured these together.

When I view domain1.co.uk it currently works fine as required. I would like to change it to:

* /var/www/**domain1.co.uk/prod/** - becomes the root dir of domain1.co.uk
* /var/www/**domain2.co.uk/prod/** - becomes the root dir of domain2.co.uk

Nevertheless, I have created a the following files; these are copies of the "default" file and correctly amended. the required destination directories are in place!

* /etc/apache2/sites-available/domain1.co.uk
* /etc/apache2/sites-available/domain2.co.uk

I then executed:

```
sudo ln -s domain1.co.uk ../sites-enabled/domain1.co.uk
```
```
sudo ln -s domain2.co.uk ../sites-enabled/domain2.co.uk
```

It is important to understand domain1.co.uk and domain2.co.uk represent 2 Existing domain names i own, and both point to my server.

domain1.co.uk currently works in /var/www

Hense why i would like multiple domain names on the server.

---

### Post by Lloyd_mcse on 2011-06-11
Have you set up the document roots for each domain...
 
eg..
 
/var/www/vhosts/domain1/http
 
and 
 
/var/www/vhosts/domain2/http
 
 
EDIT: Sorry I mis-read, looks like u have done this.

---

