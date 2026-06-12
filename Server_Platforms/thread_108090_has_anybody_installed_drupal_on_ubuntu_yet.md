---
title: "has anybody installed drupal on ubuntu yet?"
date: 2005-12-25
forum: Server Platforms
---

### Post by harisund on 2005-12-25
I tried installing Drupal and followed the instructions here
[http://www.umasslug.org/index.php/Drupal_on_ubuntu_server](http://www.umasslug.org/index.php/Drupal_on_ubuntu_server)

Everything went fine and I could open the web based interface (as instructed so in the end of the above link) however, to create an administrator user for Drupal, I have to enter an email id. 

I enter my email id (**@yahoo.com) but it simply stays there and I get no email in my yahoo inbox. Is there a problem? Do I need to be running a mail server too to get Drupal to work? 

Oh, and has anybody got phpMyAdmin to work too? I go to phpmyadmin and it gives an error that says the configuration file needs a password ??


Thanks for your help !

---

### Post by daschl on 2005-12-26
[QUOTE=harisund]I tried installing Drupal and followed the instructions here
[http://www.umasslug.org/index.php/Drupal_on_ubuntu_server](http://www.umasslug.org/index.php/Drupal_on_ubuntu_server)

Everything went fine and I could open the web based interface (as instructed so in the end of the above link) however, to create an administrator user for Drupal, I have to enter an email id. 

I enter my email id (**@yahoo.com) but it simply stays there and I get no email in my yahoo inbox. Is there a problem? Do I need to be running a mail server too to get Drupal to work? 

Oh, and has anybody got phpMyAdmin to work too? I go to phpmyadmin and it gives an error that says the configuration file needs a password ??


Thanks for your help ![/QUOTE]

i cant help you with the drupal problem because i dont use it, but for the phpMyAdmin i have some issues:

- download it
- extract it
- copy it to your htdocs folder (so that you can access it with localhost/phpmyadmin/), maybe you have to rename it to a shorter name for usability
- there is a config file, and if you have set a password for the user you have to enter it there

look here for more info:
[http://www.phpmyadmin.net/home_page/docs.php](http://www.phpmyadmin.net/home_page/docs.php)

---

### Post by harisund on 2005-12-26
thanks...didn't think of that method.. thought apt-get install phpmyadmin would work.. will try it and get back !

Thank you again !

---

