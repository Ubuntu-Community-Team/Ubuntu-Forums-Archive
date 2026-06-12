---
title: "HELP!  Config Inside for ProFTPd"
date: 2006-10-04
forum: Server Platforms
---

### Post by Zephirus on 2006-10-04
I am running 3 virtual servers to test this lamp server out...

apacheone.dyndns.org
apachetwo.dyndns.org
apachethree.dyndns.org


I have them working, however, I am having problems setting up this FTP.  I want the owner of apachethree to be able to access their files ONLY, Like a web hosting service does....  

Below is my config file.   I dont know where I have to add what username and password they need to log into the FTP site with.   If someone can look over this and explain it for me.  I used a template so It may be very wrong....


```
chris@TRINITY:/etc$ sudo vi proftpd.conf
Password:

ServerName "Cohutta Webserver"
ServerType inetd
DeferWelcome off
Port 21
Umask 002
TimeoutLogin 120
TimoutIdle 600
TimeoutNoTransfer 900
TimoutStalled 3600

User ftp
Group ftp
DefaultRoot /web/Legacy
UseReverseDNS off
ScoreBoardPath /var/run/proftpd
TransferLog /var/spool/syslog/proftpd/xferlog.legacy
LogFormat default "%h %l %u %t \"%r\" %s %b"
LogFormat auth "%v [%P] %h %t \"%r\" %s"
LogFormat write "%h %l %u %t \"%r\" %s %b"

<Global>
DisplayLogin welcome.msg
DisplayFirstChdir readme
AllowOverwrite yes
IdentLookups off

<Limit WRITE>
DenyAll
</Limit>

# --------------------------------------------------------------------------
#  VIRTUAL SERVER 1 CONFIG - APACHEONE.DYNDNS.ORG
# -------------------------------------------------------------------------

<VirtualHost apacheone.dyndns.org>
ServerAdmin chris@cohutta.com
ServerName "Cohutta Webserver"
User apacheone
Group ftp
MaxLoginAttempts 2
RequireValidShell no
TransferLog /var/www/apacheone/logs/transfer.txt
MaxClients 5
DefaultServer on
DefaultRoot /var/www/apacheone/
AllowOverwrite yes
TimeoutLogin 120
TimeoutIdle 600
TimeoutNoTransfer 900
</VirtualHost>
-- INSERT --     
```

---

### Post by sonic2000gr on 2006-10-05
Ok, first things first: To limit an FTP account so it can only access the home directory of the user add the following to the <Global> section of proftpd.conf:

```
DefaultRoot ~
```

What you really need to do with apache is:

- Setup standard linux accounts for apacheone, apachetwo and apachethree sites. Let's say you call them www-user1, www-user2 and www-user3

- These three accounts will have home directories like /home/www-user1, /home/www-user2, /home/www-user3

- Create a folder called e.g. www inside each one of these home folders. Make sure the users have read-write permissions on them (e.g. sudo chown -R www-user1:www-user1 /home/www-user1/www ; sudo chmod -R 755 /home/www-user1/www )

- Assign them good passwords

- Proftpd uses the linux accounts,it does not have separate user/password files. When either of the three users ftp into the server, they will be limited (chrooted) to their respective home directories (provided you enterred the DefaultRoot above).

- For every virtual apache2 site, change e.g:

for apacheone.dyndns.org 
```
DocumentRoot /home/www-user1/www 
```

for apachetwo.dyndns.org
```
DocumentRoot /home/www-user2/www 
```

for apachethree.dyndns.org
```
DocumentRoot /home/www-user3/www 
```

effectively, you are redirecting the root folder where apache reads files from /var/www (which is inaccessible by your ftp users) to a folder on their own home directory which they can access via ftp. Whatever files they copy in there will become part of the respective sites.

You may also want to completely disable anonymous ftp by commenting out the entire <Anonymous ~ftp> area in /etc/proftpd/proftpd.conf

---

### Post by Zephirus on 2006-10-05
WoW I was online when yo posted this... let me look over it.  Thanks for taking the time to help me out!

---

### Post by Zephirus on 2006-10-05
Sounds great, let me try this tonight

So the rest of the crap in there, I dont really need, just bells and whistles.

---

