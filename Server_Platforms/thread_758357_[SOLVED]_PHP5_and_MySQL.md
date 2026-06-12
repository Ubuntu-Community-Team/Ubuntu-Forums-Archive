---
title: "[SOLVED] PHP5 and MySQL"
date: 2008-04-17
forum: Server Platforms
---

### Post by tamoneya on 2008-04-17
I am trying to get kPlaylist which is an php web app working that requires PHP and MySQL to work.  When I point my web browser at the server I get the following error:```
Your PHP seem to lack MySQL support. Please locate your php.ini file and enable MySQL support.
``` I did some quick searching and found a forum post about uncommenting ```
extension =mysql.so
``` in php.ini and then restarting apache but it didn't work.  Does anyone else have any ideas.

---

### Post by conjur3r on 2008-04-18
You probably haven't installed the mysql module for php.  Assuming you are running php5, do so with the following:

# sudo apt-get install php5-mysql

After you've done this, restart apache for changes to take affect.

# sudo apache2ctl restart

---

### Post by tamoneya on 2008-04-18
That worked perfectly thanks.

---

