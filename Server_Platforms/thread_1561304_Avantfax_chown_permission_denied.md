---
title: "Avantfax chown permission denied"
date: 2010-08-26
forum: Server Platforms
---

### Post by Desert Farmer on 2010-08-26
Hi Friends

First time on ubuntu forums.

I need some help. I've been setting up a hylafax server with avantfax as a front end. I have been following the steps set out on this link:
[http://howtoforge.com/build-a-hylafax-server-with-avantfax-on-debian-etch](http://howtoforge.com/build-a-hylafax-server-with-avantfax-on-debian-etch)

Everything went well except here:

 ```
 # cd /var/spool/hylafax/bin
 # mv faxrcvd faxrcvd.old
 # mv notify notify.old
 # ln -s /var/www/avantfax/includes/faxrcvd.php  /var/spool/hylafax/bin/faxrcvd
 # ln -s /var/www/avantfax/includes/notify.php  /var/spool/hylafax/bin/notify
 # mv /usr/bin/faxcover /usr/bin/faxcover.old
# ln -s /var/www/avantfax/includes/faxcover.php /usr/bin/faxcover 
 Edit create_tables.sql to use avantfax  database:
  # nano create_tables.sql
 Add "USE avantfax;" to top.
 Edit setup.sh to chown to "root.root":
  # nano setup.sh
  Change apache.apache to "root.root".
 Run the setup script:
 # ./setup.sh
```I believe I have changed ownership of the setup.sh file correctly but still when I run it I get this error:
```
-bash: ./setup.sh: Permission denied
```


Any suggestions?

---

### Post by Desert Farmer on 2010-08-26
Found my own solution, had to do a chmod

chmod 111 setup.sh

---

