---
title: "Remote Access to CUPS Web Interface"
date: 2008-06-04
forum: Server Platforms
---

### Post by LRT on 2008-06-04
i'm running ubuntu server 8.04. i just installed CUPS and i am trying to access the web interface from another computer (on the same subnet) because i don't have a gui installed on the server to use the web interface locally. 

my problem is that i can't seem to access the admin section. when i click on the 'Administration' tab, i'm prompted for a username and password into which i type root and its password. then all i get is a white screen (nothing loads). when i check /var/log/cups/error_log logs i get the following line:

cupsdCloseClient: SSL shutdown successful!

to me it looks like SSL is shutting down when i try to login. why its doing that i have no idea.

anyone help me???

here is my cupsd.conf

```
SystemGroup lpadmin

LogLevel info
Port 631
Browsing On
BrowseAddress 192.168.3.255

<Location />
Order Deny,Allow
Deny From All
Allow From 192.168.3.0/24
Allow From 127.0.0.1
</Location>

<Location /admin>
AuthType Basic
Order Deny,Allow
Deny From All
Allow From 192.168.3.0/24
Allow From 127.0.0.1
</Location>

```

thanks!

---

### Post by dmizer on 2008-06-04
just have to add your server user to the cups admin group:

more information here: [https://help.ubuntu.com/community/PrintingCupsWebInterface?](https://help.ubuntu.com/community/PrintingCupsWebInterface?)

---

### Post by LRT on 2008-06-04
thanks for your reply... i did not have a cupsys user that existed on my system so i added the root user to the shadow group and to the lpadmin group. after restarting cupsys i still was having the same problem.

could it be that maybe i don't have SSL installed since this is a fresh install of ubuntu 8.04 server. what do you think?? how do i check if i have SSL installed and running?? do u have any other ideas on how to fix this? thanks.

---

### Post by LRT on 2008-06-04
i'm hoping someone could help because i'm really stuck with this one. i had no problems using cups in 7.10, but 8.04 is really giving me a headache with this.

---

### Post by LRT on 2008-06-04
ok, this configuration seems to be working nicely except there is no authentication... how can i modify this to get authentication to work???

```
SystemGroup root

LogLevel info

Browsing On
BrowsingAddress 192.168.3.255:631
BrowseAllow from all

Port 631
Listen localhost:631
Listen 192.168.3.1:631
Listen /var/run/cups/cups.sock

<Location />
Order Deny,Allow
Deny from All
Allow from 192.168.3.*
Allow from @LOCAL
</Location>

<Location /admin>
AuthType None
Order Deny,Allow
Deny from All
Allow from 192.168.3.*
Allow from @LOCAL
</Location>

```

---

### Post by dmizer on 2008-06-04
the first command:
```
sudo adduser cupsys shadow
```
would have added the cupsys user.

the second command:
```
sudo adduser <yourusername> lpadmin
```
should have been run with the system user ("yourusername" should be the account you created when you installed ubuntu), not the root account.  if you enable the root account for cups web interface, you're looking at a security risk (no authentication among other things).

---

### Post by LRT on 2008-06-05
```
cat /etc/group | grep shadow

shadow:x:42:cupsys

cat /etc/group | grep lpadmin

lpadmin:x:113:itmanager
```

restarting cupsys (/etc/init.d/cupsys restart) shows no errors.

this is my cupsd.conf:

```
SystemGroup lpadmin

LogLevel info

Browsing On
BrowsingAddress 192.168.3.255:631
BrowseAllow from all

Port 631
Listen localhost:631
Listen 192.168.3.1:631
Listen /var/run/cups/cups.sock

<Location />
Order Deny,Allow
Deny from All
Allow from 192.168.3.*
Allow from @LOCAL
</Location>

<Location /admin>
AuthType Basic
Order Deny,Allow
Deny from All
Allow from 192.168.3.*
Allow from @LOCAL
</Location>
```

when i try to log in to the admin section on the web interface it asks me for a username and password so i put in 'itmanager' for the username and its unix password, but all i get is a blank screen and i have to restart cupsys to get into the interface, but i can never get into the admin section... 

obviously i'm stumped, anymore ideas??? (thanks for your help!)

---

### Post by dmizer on 2008-06-06
humm ... here's my working cupsd.conf file:
```
# Show general information in error_log.
LogLevel info
SystemGroup lpadmin
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow @LOCAL
DefaultAuthType Basic
<Location />
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
Include /etc/cups/cups.d/browse.conf
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
```

---

### Post by LRT on 2008-06-06
copied your cupsd.conf word for word and when i try to edit the configuration file through the web interface i still get a blank screen when i type my username and password... the error log shows the same error as before:

cupsdCloseClient: SSL shutdown successful!

i wish i knew how to investigate SSL, but i know nothing about it.

why is SSL shutting down?
how do i check if its running or even installed??

in /etc/apache/mods-enabled/ there is no ssl.load or ssl.conf

do i simply create a symbolic link from mods-available/ to mods-enabled/ to enable SSL??

---

### Post by LRT on 2008-06-06
i also noticed that firefox never asks me to accept a certificate... 

maybe a certificate is not being generated???

---

