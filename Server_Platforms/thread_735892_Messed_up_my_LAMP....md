---
title: "Messed up my LAMP..."
date: 2008-03-26
forum: Server Platforms
---

### Post by DocHobbes on 2008-03-26
I had installed LAMP on my computer and thought I had installed php incorrectly. I tried uninstalling it by typing 

 sudo apt-get remove php5 libapache2-mod-php5

I don't know if it removed everything correctly...because now when I try to run 
 sudo apt-get install php5 libapache2-mod-php5
It doesn't work. It looks like it works. But the test.php page asks me what I would like to open the file in. 
I'd really like to get this working. 

 THANKS in advance for any help!

---

### Post by jrib on 2008-03-26
Does sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart make it work?

---

### Post by DocHobbes on 2008-03-26
YES! It does...well for some reason the test.php page is actually displaying the test php on the page, but it's no longer asking me how to open it so I'm happy. 
 or for my own knowledge...what did that first command do? 
Thanks again!

---

### Post by jrib on 2008-03-31
The first command enables the php module in apache.  It basically creates symlinks from things in from/etc/apache2/mods-enabled/ to things in /etc/apache2/mods-available/

---

