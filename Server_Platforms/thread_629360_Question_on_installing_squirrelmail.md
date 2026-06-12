---
title: "Question on installing squirrelmail"
date: 2007-12-02
forum: Server Platforms
---

### Post by satimis on 2007-12-02
Hi folks,


Ubuntu 7.04 server amd64


I have squirrelmail-2:1.4.9 installed on repository


According to:-
Package: squirrelmail (2:1.4.10a-2~feisty1) [universe]
[http://packages.ubuntu.com/feisty-backports/web/squirrelmail](http://packages.ubuntu.com/feisty-backports/web/squirrelmail)

Other Packages Related to squirrelmail

apache-2.2.3 (already installed)
php-5.2.1 (already installed
libapache2-mod-php-5.2.1 (already installed)
perl-5.8.8 (already installed)
php-pear-5.2.1 (already installed)


ispell-3.1.20.0 (not yet installed)
squirrelmail-locales-1.4.8 (not yet installed)

imap-server (not available on repository)
courier-imap-4.1.1 (already installed)

imapproxy-1.2.4 (not yet installed)
php5-ldap-5.2.1 (not yet installed)
squirrelmail-decode-1.1-2 (not yet installed)

I can have above packages installed on repo except imap-server which is NOT on repository.  Do I need installing all of them?


Where can I find relevant doc to configure squirrelmail?


Another thought, would it be easier to down the packages on;

[http://www.squirrelmail.org](http://www.squirrelmail.org)

and installed them accordingly?


TIA


B.R.
satimis

---

### Post by MJN on 2007-12-02
Personally, I would just download it directly from Squirrelmail as it doesn't need much in the way of 'installation' given it uses PHP.

Incidentally, the requirement for 'imap-server' is not specifying the requirement for a package *called* 'imap-server' but rather any package that *is* an imap server (e.g. dovecot, courier, uw-imap etc) which you will have to have as Squirrelmail is a web-based IMAP client.

I don't normally install packages from outside the repositories however Squirrelmail is one where I consider it quite acceptable to do so - it also means you can easily keep uptodate with the newer releases as bug/security fixes are released.

Mathew

---

### Post by bmathis on 2007-12-02
you can install courier-imap as the imap server, just do a "sudo aptitude install courier-imap"

---

### Post by HermanAB on 2007-12-02
Before installing squirrel, have alook at roundcube and dare I say - Citadel.

Squirrel works, but pretty or modern, it is not.

---

### Post by satimis on 2007-12-02
Hi MJN and bmathis,


Your advice noted with thanks


satimis

---

### Post by satimis on 2007-12-02
> **HermanAB said:**
> Before installing squirrel, have alook at roundcube and dare I say - Citadel.
Hi HermanAB,


I have roundcube installed and running here.  But I can't configure it to work.  I'm stuck on follows;


I found this nice howto;

[http://forums.site5.com/showthread.php?t=9374](http://forums.site5.com/showthread.php?t=9374)


According to the howto;


1)

I don't have netAdmin and phpmyadmin.  Webmin and Usermin are running here.

# which netAdmin
# which netadmin
# which phpmyadmin
all w/o printout



2)

What shall I replace "databasename"?  Mysql is running on this server.


3)

What shall I replace "change this key"?  It has data here (rcmail-!24ByteDESkey*Str)


I posted my questions to their forum and got following response;```

netadmin is a skin of cpanel that site5 has made. phpmyadmin can 
be downloaded from 
http://www.phpmyadmin.net/home_page/index.php

you can use phpmyadmin to import the sql file into the database. 
you can also use phpmyadmin to create the database

```


On remote PC I failed to start roundcube-webmail on the server;

[https://domain.com/roundcube-webmail](https://domain.com/roundcube-webmail)```

Service Currently Not Available!

Error No. 1f4

```
I don't know how to proceed further.  Any suggestion?  TIA


B.R.
satimis

---

### Post by satimis on 2007-12-03
Hi folks,


Ubuntu 7.04 server amd64 (Host OS) - mail server
VMWare
Webmin
Usermin
CentOS 5 (Guest OS)
squirrelmail-1.4.11


[http://domain.com/squirrelmail](http://domain.com/squirrelmail)```

Not Found

The requested URL /squirrelmail was not found on this server.
Apache/2.2.3 (Ubuntu) DAV/2 SVN/1.4.3 PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at domain.com Port 80

```

[http://domain.com:80/squirrelmail](http://domain.com:80/squirrelmail)
[http://domain.com:8080/squirrelmail](http://domain.com:8080/squirrelmail)
Same output


Please advise where shall I check and how to fix it.  TIA


B.R.
satimis

---

### Post by bmathis on 2007-12-04
did you make a link in apache2 and activate the site? follow this link for more info [https://help.ubuntu.com/community/Squirrelmail]("https://help.ubuntu.com/community/Squirrelmail")

---

### Post by satimis on 2007-12-04
Hi bmathis,


Now I can start squirrelmail on Firefox by running;

[http://domain.com/squirrelmail](http://domain.com/squirrelmail)


But I can't login as root/users having account on Postfix.```

Error connecting to IMAP server: localhost.
110 : Connection timed out
```

Courier-imap is running here NOT IMAP

$ apt-cache policy courier-imap```

courier-imap:
  Installed: 4.1.1.20060828-5ubuntu1
  Candidate: 4.1.1.20060828-5ubuntu1
  Version table:
 *** 4.1.1.20060828-5ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```


Besides I can't start squirrelmail with;

[http://localhost/squirrelmail](http://localhost/squirrelmail).


Advice would be appreciated.  TIA


B.R.
satimis

---

### Post by bmathis on 2007-12-04
question: do you have a Maildir folder in your home directory? if not, this would prevent you from logging into squirrelmail, try sending yourself an email and it should auto create that folder for you, then try logging into squirrelmail again.

---

### Post by satimis on 2007-12-04
> **bmathis said:**
> question: do you have a Maildir folder in your home directory? if not, this would prevent you from logging into squirrelmail, try sending yourself an email and it should auto create that folder for you, then try logging into squirrelmail again.
Yes.  The mail server is working nicely.  Users can send and receive emails remotely via Internet or Intranet on their mail client, Evolution.


satimis

---

### Post by bmathis on 2007-12-04
alright, can you telnet to port 143 or can you connect to imap via a mail client? Can you post the block of code starting with $domain in /usr/share/squirrelmail/config/config.php, omitting sensitive information of course.

---

### Post by satimis on 2007-12-04
> **bmathis said:**
> alright, can you telnet to port 143 or can you connect to imap via a mail client? 

It seems the iptables blocking the connection !!!


$ sudo iptables -F


$ telnet localhost 143```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE
THREAD=ORDEREDSUBJECT THRE
AD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP
ready. Copyr
ight 1998-2005 Double Precision, Inc.  See COPYING for distribution
information.

```

On firefox;

[http://localhost/squirrelmail](http://localhost/squirrelmail)

starts;
Squirrelmail

URL changes to;
[http://localhost/squirrelmail/src/redirect.php](http://localhost/squirrelmail/src/redirect.php)


On login following warning popup;```

ERROR
Error opening ../data/default_pref
Could not create initial preference file!
/var/local/squirrelmail/data/ should be writable by user www-data
Please contact your system administrator and report this error.

```


$ ls -l /var/local/
total 0


Shall I create /var/local/squirrelmail/data directories?
???

What will be their owner and permission?


> 
Can you post the block of code starting with $domain in /usr/share/squirrelmail/config/config.php, omitting sensitive information of course.
The path is on;
/usr/local/squirrelmail/www/config/config.php```

.....
$domain                 = 'satimis.com';
$imapServerAddress      = 'localhost';
$imapPort               = 143;
$useSendmail            = false;
$smtpServerAddress      = 'localhost';
$smtpPort               = 25;
$sendmail_path          = '/usr/sbin/sendmail';
$sendmail_args          = '-i -t';
$pop_before_smtp        = false;
$imap_server_type       = 'other';
$invert_time            = false;
$optional_delimiter     = 'detect';
$encode_header_key      = '';

$default_folder_prefix          = 'INBOX';
$trash_folder                   = 'Trash';
$sent_folder                    = 'Sent';
$draft_folder                   = 'Draft';
$default_move_to_trash          = true;
$default_move_to_sent           = true;
$default_save_as_draft          = true;
$show_prefix_option             = false;
$list_special_folders_first     = true;
$use_special_folder_color       = true;
$auto_expunge                   = true;
$default_sub_of_inbox           = true;
$show_contain_subfolders_option = true;
$default_unseen_notify          = 2;
$default_unseen_type            = 1;
$auto_create_special            = true;
$delete_folder                  = false;
$noselect_fix_enable            = false;

$data_dir                 = '/var/local/squirrelmail/data/';
$attachment_dir           = SM_PATH . 'attachments/';
$dir_hash_level           = 0;
$default_left_size        = '150';
$force_username_lowercase = false;
$default_use_priority     = true;
$hide_sm_attributions     = false;
$default_use_mdn          = true;
$edit_identity            = true;
$edit_name                = true;
$hide_auth_header         = false;
$allow_thread_sort        = false;
$allow_server_sort        = false;
$allow_charset_search     = true;
$uid_support              = true;
....

```
I did something wrong here.  I'll delete this file and re-run conf.pl

I don't run sendmail```

$sendmail_path          = '/usr/sbin/sendmail';

```
Postfix is running here.

What will be your advice on this file?  TIA


B.R.
satimis

---

### Post by bmathis on 2007-12-05
1. Did you add a rule to your iptables setup to allow the localhost to connect to port 143?
2. The URL of squirrelmail will change due to the link created to activate the site
3. I'm not sure about /var/local because mine doesnt have any data or directories in it, the permissions are as follows:```
 drwxrwsr-x  2 root     staff 
```
4. Your config file looks okay from what I can tell and the sendmail part is okay as well.

It looks like you built squirrelmail from scratch instead of using the ubuntu provided deb file? Other than what i offered previously, I am at a lost. Have you tried the squirrelmail wiki/forums/mailing lists?

---

### Post by satimis on 2007-12-05
Hi bmathis,


After performed following steps, SquirrelMail works;

$ cd /usr/local/squirrelmail/www/config
$ su
Password

# ./conf.pl 
1. select imap server in D command
2. set domain
3. set data and attachment directory

# mkdir -p /var/local/squirrelmail/data
# chown www-data:www-data -c /var/local/squirrelmail/data```

changed ownership of `/var/local/squirrelmail/data' to www-data:www-data

```

# chmod 0750 -c /var/local/squirrelmail/data```

mode of `/var/local/squirrelmail/data' changed to 0750 (rwxr-x---)

```

# mkdir /var/local/squirrelmail/attach
# chown www-data:www-data -c /var/local/squirrelmail/attach```

changed ownership of `/var/local/squirrelmail/attach' to www-data:www-data

```

# chmod 0750 -c /var/local/squirrelmail/attach```

mode of `/var/local/squirrelmail/attach' changed to 0750 (rwxr-x---)

```


Then;

[https://localhost/squirrelmail](https://localhost/squirrelmail)

works


> 
Did you add a rule to your iptables setup to allow the localhost to connect to port 143?

$ cat /etc/rc.local```

# INPUT

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d 220.232.213.178 --reject-with icmp-port-unreachable


# OUTPUT

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s 220.232.213.178 -p UDP --destination-port 53

# reject all other traffic from localhost
iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 4 -j REJECT -s 220.232.213.178 --reject-with icmp-port-unreachable

```
How to add port 143?  TIA


B.R.
satimis

---

