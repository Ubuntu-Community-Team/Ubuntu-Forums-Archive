---
title: "Unable to start squirrelmail"
date: 2008-11-22
forum: Server Platforms
---

### Post by satimis on 2008-11-22
Hi folks,


Postfix
squirrelmail
mysql
amavis


On login;```

Preference database error (connect failed). Exiting abnormally

```

login - [email]satimis@satimis.com[/email]
password - mypassword


Both of them are correct.


# tail /var/log/mail.log```

Nov 22 08:46:03 xen05 imapd-ssl: LOGIN: ip=[::ffff:127.0.0.1], command=LOGIN
Nov 22 08:46:03 xen05 imapd-ssl: LOGIN: ip=[::ffff:127.0.0.1], username=satimis@satimis.com
Nov 22 08:46:03 xen05 imapd-ssl: LOGIN: ip=[::ffff:127.0.0.1], password=mypassword
Nov 22 08:46:03 xen05 authdaemond: received auth request, service=imap, authtype=login
Nov 22 08:46:03 xen05 authdaemond: authmysql: trying this module
Nov 22 08:46:03 xen05 authdaemond: SQL query: SELECT id, "", clear, uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "satimis@satimis.com" AND (enabled=1)
Nov 22 08:46:03 xen05 authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=satimis@satimis.com, fullname=Stephen, maildir=/var/spool/mail/virtual/Stephen/, quota=<null>, options=<null>
Nov 22 08:46:03 xen05 authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=satimis@satimis.com, fullname=Stephen, maildir=/var/spool/mail/virtual/Stephen/, quota=<null>, options=<null>
Nov 22 08:46:03 xen05 imapd-ssl: LOGIN, user=satimis@satimis.com, ip=[::ffff:127.0.0.1], protocol=IMAP
Nov 22 08:46:03 xen05 imapd-ssl: LOGOUT, user=satimis@satimis.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=46, sent=376, time=0, sta

```

No warning there.


# cat /etc/amavis/conf.d/50-user```

use strict;

@lookup_sql_dsn = (
    ['DBI:mysql:database=maildb;host=127.0.0.1;port=3306',
     'mail',
     'mailpassword']);

$sql_select_policy = 'SELECT name FROM virtual_domains WHERE CONCAT("@",name) IN (%k)';

#------------ Do not modify anything below this line -------------
1;  # insure a defined return

$mydomain= 'satimis.com';
$daemon_user= 'virtual';
$daemon_group= 'virtual';
@local_domains_acl = qw(.);
$inet_socket_port = 10024;
$forward_method = 'smtp:127.0.0.1:10025';
# @bypass_virus_checks_acl = qw( . );
# @bypass_spam_checks_acl = qw( . );

# I also change these
$TEMPBASE = "$MYHOME/tmp";
# Whilst debugging
$log_level = 2;
$warnbannedrecip = 1;
$warn_offsite = 1;
$warnvirusrecip = 1;
$spam_quarantine_to = "spam-quarantine\@$mydomain";
$virus_quarantine_to = "virus-quarantine\@$mydomain";
$sa_local_tests_only = 0;

```


Please help.  TIA


B.R.
satimis

---

### Post by MJN on 2008-11-24
You are barking up the wrong tree.
 
Squirrelmail is an IMAP client hence doesn't have anything to do with your AV scanner.
 
The error will be down to your SM config and/or your user preference table in MySQL.
 
For the former, perform a self-test on the config by browsing to <your SM mail root>/src/configtest.php
 
If this test passes than the fault likely lies in the MySQL preference table (or the authenticated access to it). I likely cannot help you there as the devil likely lies in the detail of how you set it up. Why don't you use simple text files for user configuration? Or do you have hundreds of users to support?
 
Mathew

---

### Post by satimis on 2008-11-24
> **MJN said:**
> You are barking up the wrong tree.
 
Squirrelmail is an IMAP client hence doesn't have anything to do with your AV scanner.
 
The error will be down to your SM config and/or your user preference table in MySQL.
 
For the former, perform a self-test on the config by browsing to <your SM mail root>/src/configtest.php
 
If this test passes than the fault likely lies in the MySQL preference table (or the authenticated access to it). I likely cannot help you there as the devil likely lies in the detail of how you set it up. Why don't you use simple text files for user configuration? Or do you have hundreds of users to support?

 
Mathew,


I don't know what magic I have done here.  


The mail server is now running serving multiple domains (4 domains are running).  Users of all domains can login the server with password to send/receive mails on mail client, Evolution.


SquirrelMail is also working.  Users can login SM with their password to send/read mails direct on browser.


The final solution on SM is a mystery.  

Re-run
# /var/www/squirrelmail/config/conf.pl

DSN for Address Book = mysql://satimis@satimis.com:mypassword@127.0.0.1/maildb


On browser
http:/satimis.com/src/configtest.php```

......
Warning;
ERROR: Database error: connect failed .......

```

Disregard the above warning SM is working.

"DSN for Preferences" must be blank.  Otherwise SM won't start.


satimis

---

