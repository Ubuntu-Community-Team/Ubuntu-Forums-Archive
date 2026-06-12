---
title: "How do I install Wordpress 2.8.4 on my LAMP Server"
date: 2009-10-02
forum: Server Platforms
---

### Post by jigglypuff on 2009-10-02
I looked at the instructions @ help.ubuntu.com but I didnt want to try them because they are over 3 years old

---

### Post by Bachstelze on 2009-10-02
Just follow the instructions on the official website: [http://wordpress.org/download/](http://wordpress.org/download/)

Don't hesitate to come back with more specific questions if you have problems. ;)

---

### Post by solitaire on 2009-10-02
Wordpress is was the easiest to install of the 3 I tried, Others were, Drupal (Nightmare to install!)  and Joomla (needed a few tweeks!).

---

### Post by jigglypuff on 2009-10-02
solitaire I tried installing Drupal once. I thought I was going to die

---

### Post by solitaire on 2009-10-02
If you check out the "5 min install of wordpress" instructions it's should work.

Basically set up a empty database
Change the "wp-config.php" and add in the mysql database details
Then browse to [http://localhost/wordpress/wp-admin/install.php](http://localhost/wordpress/wp-admin/install.php)
Then that's it!

Add in your details and go!

---

### Post by tgalati4 on 2009-10-03
apt-cache search wordpress
sudo apt-get install wordpress

Tweak the config files per solitaire's instructions.

---

