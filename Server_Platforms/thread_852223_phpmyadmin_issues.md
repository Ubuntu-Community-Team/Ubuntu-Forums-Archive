---
title: "phpmyadmin issues"
date: 2008-07-07
forum: Server Platforms
---

### Post by cooldude_832 on 2008-07-07
I'm trying to install phpmyadmin on apache2 in ubuntu 8.0.4 using

sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

terminal runs the installer just fine but when I go to localhost/phpmyadmin i get nothing.  Apache is running cause other files work but phpmyadmin gives me that page not found error.


Any ideas I've tried removing and reinstalling no help.

---

### Post by Titan8990 on 2008-07-07
Have you tried putting in your ip address instead of localhost?

Is your /etc/hosts file configured correctly?

---

### Post by cooldude_832 on 2008-07-07
yes I've tried it multiple ways 404 error any way

whats the config you are stating?

in my php.ini the line
extension=mysql.so is uncommented.


Whats interesting is everytime I reinstall phpmyadmin I don't get that autoconfig menu I expect.

---

### Post by Titan8990 on 2008-07-07
Have you tried hitting it from another machine on your local network?

---

### Post by cooldude_832 on 2008-07-07
yes its somethign in the config and i did it before but I forgot.  I ran through a few tutorials but some how phpmyadmin isn't syncing to apache2 properly.

---

### Post by Titan8990 on 2008-07-07
It shouldn't need to make any changes in the default config to get to phpmyadmin. However, changes made to the config file can prevent it from hitting phpmyadmin. For example, I can not view my phpmyadmin page because I have apache redirecting traffic to a RoR app.

---

### Post by cooldude_832 on 2008-07-07
its a fresh install there are no existing .htacess mods that would cause what you are saying the files aren't in the www folder either as I expected.

---

### Post by Titan8990 on 2008-07-07
You could purge you existing packages and then try to use LAMP. 

Are you able to see the default apache page from just going to [http://localhost?](http://localhost?)

---

### Post by cooldude_832 on 2008-07-07
I figured it out when i went to go edit the apache.conf I didn't save it :)

---

### Post by Titan8990 on 2008-07-07
Good to hear it was something simple. Sometimes odd issues can keep you stumped for long periods of time...

---

