---
title: "How to upgrade SquirrelMail"
date: 2008-04-18
forum: Server Platforms
---

### Post by satimis on 2008-04-18
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8
SquirrelMail version 1.4.11


I'm prepared following;

4. Upgrading SquirrelMail
[http://squirrelmail.org/docs/admin/admin-4.html#ss4.1](http://squirrelmail.org/docs/admin/admin-4.html#ss4.1)

to upgrade SquirrelMail to version "SquirrelMail version 1.4.13"


I can't upgrade it on repo because I installed SM on tarball sometimes ago.  However I don't know which directory/directories I have to backup.  The Maildirs are on;


# ls /home```

user1	user2	user3	user3	user4	ftp	etc.

```


# ls /home/user1/```

Maildir

```


# ls /home/user1/Maildir/```

courierimapkeywords  courierimapsubscribed  courierimapuiddb  cur  new  tmp

```

etc.


# ls /home/ftp/```

welcome.msg

```


# find / -name squirrelmail -type d```

/usr/local/squirrelmail
/var/local/squirrelmail
/etc/squirrelmail

```


# ls /usr/local/squirrelmail/```

data  temp  www

```
data and temp are empty directories


# ls /usr/local/squirrelmail/www/```

AUTHORS    configure  doc        include    plugins       src
ChangeLog  contrib    functions  index.php  po            themes
class      COPYING    help       INSTALL    README        UPGRADE
config     data       images     locale     ReleaseNotes

```


# ls /var/local/squirrelmail/```

attach  data

```
attach is empty directory


data directory containing users' .abook .pref


# ls /etc/squirrelmail/```

apache.conf         config_local.php  default_pref       index.php
config_default.php  config.php        filters_setup.php  sqspell_config.php

```


Previously by mistake I have another set of users on
# ls /var/mail/```

user1	user2	user3	user4	etc.	Maildir

```
They are doc files not directories.  All incoming mails were added to the respective users' doc.  How the mistake was made is unknown to me.


After adding following lines```

DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL

```
on /etc/procmailrc

All incoming mails are delivered to users' Maildir on /home/user1 /home/user2 etc.  Those users' doc files are still there but not used anymore.


Now which directory/directories I have to backup?  Whether I still can follow the document "Upgrading SquirrelMail".  Please help.  TIA


B.R.
satimis

---

