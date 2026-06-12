---
title: "Apache issues!!!!"
date: 2006-07-02
forum: Server Platforms
---

### Post by afbase on 2006-07-02
-okay installed the 6.06 lamp server
-i installed proftpd
-i can type in localhost into the browser and the IP adress to the server and i get the index page just fine

-WHERE THE HECK IS THE DEFAULT DIRECTORY THAT THE STUPID INDEX.HTML FILE IS LOCATED BY DEFAULT?  
I CAN'T SEEM TO FIND THAT INFO IN MY /ETC/APACHE2/APACHE2.CONF


oh ya i am a linux noob coming off of years in M$ windows.  How could i search for a file or folder in terminal shell?

---

### Post by scxtt on 2006-07-02
/var/www and/or /var/www/apache2

---

### Post by afbase on 2006-07-02
[QUOTE=scxtt]/var/www and/or /var/www/apache2[/QUOTE]
THANKS!!!!!!

---

### Post by Kurt` on 2006-07-03
You can change the document root in /etc/apache2/sites-enabled/000-default if that location is undesirable :)

---

### Post by lamego on 2006-07-03
Next time try to be polite like avoiding using CAPS, the lack of Linux experience does not justify to be rude.

To  locate a file on your system you can use:
  locate filename
or
  find path -name filename

The locate command is based on a local database so it will return the results much faster.

---

### Post by MJN on 2006-07-03
[quote=lamego]The locate command is based on a local database so it will return the results much faster.[/quote]
 
Althought just to caveat that, the database is updated only daily(?) by default so bear that in mind if you're hunting for a 'new' file that you know exists yet locate appears to say not.
 
Mathew

---

