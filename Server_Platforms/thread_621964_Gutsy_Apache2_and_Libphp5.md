---
title: "Gutsy Apache2 and Libphp5"
date: 2007-11-24
forum: Server Platforms
---

### Post by jhenes on 2007-11-24
Hi !

After updating to the latest version of packages on my 7.10 server (apt-get dist-upgrade), Apache stops with the following message :

---
apache2: Syntax error on line 183 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: undefined symbol: xmlTextReaderSchemaValidate
   ...fail!
---
I have checked for bad symlinks, reinstalled apache, ibapache2-mod-php5 , libxml2 (as the symbol refers to) with the same result... 

Googling gives me nothing, does anybody have a clew on what is going on ?

:confused:

---

### Post by S-AVR on 2007-11-25
i have the same problem :(

---

### Post by Brazen on 2007-11-26
Your best bet is to stick with an LTS release on servers - namely Ubuntu Dapper.

My guess is you are going to have to submit a bug report on this.

---

### Post by staticvoid on 2007-11-26
it comes with LAMP. maybe look for a tutorial to install LAMP and just reinstall everything

---

