---
title: "change cgi-bin directory?"
date: 2007-02-07
forum: Server Platforms
---

### Post by mrpeenut24 on 2007-02-07
I was wondering if, like changing the home directory in Apache, it were possible to change the cgi-bin directory?  I tried changing the /usr/apache2/sites-available/default line that has the cgi-bin "Script-Alias" information to the directory I wanted, but it didn't work.  I was hoping to get the directory into the same directory as the rest of the website (i.e. /var/www/cgi-bin).  Do I need to restart Apache after I change the file?  Would this work?

---

### Post by mrpeenut24 on 2007-02-07
Nevermind, I restarted it with the changes and it worked.  Fixed!

---

### Post by chalex on 2007-02-07
Yes, you need to at least reload apache each time you make a change.  

/etc/init.d/apache2 {reload|restart}

---

