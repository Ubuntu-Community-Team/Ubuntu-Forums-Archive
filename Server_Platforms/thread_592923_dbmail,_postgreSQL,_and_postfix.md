---
title: "dbmail, postgreSQL, and postfix"
date: 2007-10-26
forum: Server Platforms
---

### Post by reddcell on 2007-10-26
Looking for information on getting a set up like this up and running on Edgy. Went through the bit of information on dbmail's wiki, but no success...and pretty much every other bit of information found when googling isn't in english : ( Thanks in advance!

---

### Post by HermanAB on 2007-10-26
If you need a database mail system that can handle terrabytes of mail, have a look here: [http://citadel.org](http://citadel.org)

Fast, efficient and super easy to install.  It takes only about 20 minutes to have a fully working system, so it is well worth a try.

Cheers,

Herman

---

### Post by reddcell on 2007-10-31
BerkleyDB backend? No thanks.

Any suggestions to this problem would be appreciated!!

---

### Post by ubnuturero on 2007-10-31
once you've installed  dbmail 
you need to create your schema  and its located in   /usr/share/doc/dbmail-pgsql/examples/create_tables.pgsql  

this for the dbmail-pgsql in edgy 

then  configure your  dbmail.conf in /etc or /etc/dbmail
then config  your postfix as  the doc in :
[http://www.dbmail.org/dokuwiki/doku.php?id=setup_postfix](http://www.dbmail.org/dokuwiki/doku.php?id=setup_postfix)

check in /var/log/mail.log for errors  and post them here if you need more help

---

