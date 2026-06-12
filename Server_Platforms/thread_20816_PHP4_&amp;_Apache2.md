---
title: "PHP4 &amp; Apache2"
date: 2005-03-18
forum: Server Platforms
---

### Post by ejms07 on 2005-03-18
How can I enable php4 modules in Apache2?

Thank guys.....you all ROCKS!

---

### Post by Jad on 2005-03-19
I'm not sure how to 
if its not a production server then you can always go with ApacheFriends.org, they have Xampp it has to many good features, the top one for me you can switch from php4 to php5 with single command line.

---

### Post by garyng on 2005-03-19
in a terminal :

apt-cache search libapache2

find the php4 module name and :

apt-get install <php4 apache2 module, you look up the name>

---

### Post by ejms07 on 2005-03-21
I have libapache2-mod-php4 installed.  I just need to edit http.conf and modules.conf but I cannot find the exact path of the php4 modules.

---

### Post by garyng on 2005-03-21
/etc/apache2/mods-available

usually controlled by "a2enmod/a2dismod"

---

