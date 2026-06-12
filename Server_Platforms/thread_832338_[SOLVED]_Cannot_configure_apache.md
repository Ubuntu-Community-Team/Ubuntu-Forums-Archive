---
title: "[SOLVED] Cannot configure apache"
date: 2008-06-17
forum: Server Platforms
---

### Post by Alnico on 2008-06-17
I am having problems configuring Apache. I installed LAMP to work on PHP.

I get the error "**You don't have permission to access / on this server.**" when I try and access "http://localhost/" in my Web browser.

I was initially trying to set myself permissions to copy, paste and edit files in /var/www and I seemed to have completely messed the permissions up. In addition, this is what I added to the /etc/apache2/httpd.conf file that was initially blank.

<Directory "/var/www">
AllowOverride All
Order allow,deny
Allow from all
</Directory>

I have attached the following screenshots:
A. Permissions of /var/www
B. Error message when accessing localhost

This is what I want to do:
1. Give my user account full rights to paste and edit files in **/var/www** 
2. Is the httpd.conf file content correct?
3. I am confused about the default directory. Is it **/var/www** or **/var/www/html** ? 

Please help!

---
Ubuntu 8.04

---

### Post by johnswb on 2008-06-17
Give [Webmin]("http://www.webmin.com/") at try.


Using webmin has made the apache experience so much better for me.

---

### Post by windependence on 2008-06-17
```
sudo chmod -R 775 /var/www
```

I think your ownership is messed up however. Do you have an Apache user? When you start Apache and run top, what user does Apache run as? 

If the user is www (as on most systems) you will also need to do an:

```
sudo chown -R www /var/www
```

-Tim

---

### Post by Alnico on 2008-06-18
> **johnswb said:**
> Give [Webmin]("http://www.webmin.com/") at try.


Using webmin has made the apache experience so much better for me.
Thanks for the link. I would try it, but at a later stage. As a new user, I would like to get my hands dirty the hard way and understand how the stuff works.

---

### Post by Alnico on 2008-06-18
> **windependence said:**
> ```
sudo chmod -R 775 /var/www
```

I think your ownership is messed up however. Do you have an Apache user? When you start Apache and run top, what user does Apache run as? 

If the user is www (as on most systems) you will also need to do an:

```
sudo chown -R www /var/www
```

-Tim
Hi Tim, 

Thanks it kinda worked. I chowned to my user account and it works fine now. I have a few questions:

1. I don't have an apache or www account set up. Is this ok? What is the significance of this account?
2. What is the difference between the /var/www and /var/www/html folders?

Thanks for solving my problem. :)

---

### Post by windependence on 2008-06-18
Well, I like to run my Apache stuff under it's own user for security. I run mostly FreeBSD hosts in VMs on top of Ubuntu server, and FBSD does this when Apache is installed. It's not necessary, but may be considered good practice.

As for the folders, you theoretically could set any folder on your system to be the root Apache file if you specify it in your httpd.conf file. I am not sure if yours is set to /var/www or /var/www/html. You will need to look in the file to see what the Document Root is set to. That is the directory where you want to put you web files.

-Tim

---

### Post by Kolipoki on 2008-06-18
> **windependence said:**
> Well, I like to run my Apache stuff under it's own user for security. I run mostly FreeBSD hosts in VMs on top of Ubuntu server...
Geeze Tim, I would give an ear just to know how you did this. Sounds mighty interesting and looks like the type of setup that my mind has been wanting to "chew" to implement my Apache stuff too. Well... hopefully I'll get there some day... *thumbs up*

---

### Post by Alnico on 2008-06-18
Just curious: What is 775 supposed to do?

---

### Post by johnswb on 2008-06-18
> **Alnico said:**
> Thanks for the link. I would try it, but at a later stage. As a new user, I would like to get my hands dirty the hard way and understand how the stuff works.

For me I had a BIG learning curve, so using Webmin helped me to learn the command line option as well.  After making a setting change in Webmin you can view the config file, and make other setting changes to the config file see what happens.  I agree with you in getting your hands dirty, but it nice to get results from the mud pies.

---

