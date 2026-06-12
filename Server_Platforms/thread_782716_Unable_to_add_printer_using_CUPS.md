---
title: "Unable to add printer using CUPS"
date: 2008-05-05
forum: Server Platforms
---

### Post by SumnerBoy on 2008-05-05
Hi - I am doing a fresh reinstall of my home server using 8.04 (from 7.10). I have come to the printer configuration and have hit a brick wall.

I have CUPS up and running and can access from the network on port 631. CUPS recognises I have a USB printer but when I try to add the printer and click the final 'Add Printer' button I get a 404 page and the following in the log (debug enabled)...

```
D [05/May/2008:23:01:51 +1200] cupsdReadClient: 8 POST /admin HTTP/1.1
D [05/May/2008:23:01:51 +1200] cupsdAuthorize: No authentication data provided.
D [05/May/2008:23:01:51 +1200] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 6186
I [05/May/2008:23:01:51 +1200] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=6186)
D [05/May/2008:23:01:51 +1200] cupsdSendCommand: 8 file=11
D [05/May/2008:23:01:51 +1200] [CGI] admin.cgi started...
D [05/May/2008:23:01:51 +1200] [CGI] http=0x8079ff8
D [05/May/2008:23:01:51 +1200] [CGI] op="add-printer"...
D [05/May/2008:23:01:51 +1200] [CGI] do_am_printer: DEVICE_URI="canon:/dev/usb/lp0"
D [05/May/2008:23:01:51 +1200] cupsdAcceptClient: 9 from localhost (Domain)
D [05/May/2008:23:01:51 +1200] cupsdReadClient: 9 POST /admin/ HTTP/1.1
D [05/May/2008:23:01:51 +1200] cupsdAuthorize: No authentication data provided.
D [05/May/2008:23:01:51 +1200] CUPS-Add-Modify-Printer ipp://localhost/printers/MP530
D [05/May/2008:23:01:51 +1200] cupsdIsAuthorized: username=""
E [05/May/2008:23:01:51 +1200] CUPS-Add-Modify-Printer: Unauthorized
D [05/May/2008:23:01:51 +1200] cupsdSendError: 9 code=401 (Unauthorized)
D [05/May/2008:23:01:51 +1200] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [05/May/2008:23:01:51 +1200] cupsdCloseClient: 9
D [05/May/2008:23:01:51 +1200] [CGI] cgi_passwd(prompt="Password for lp on localhost? ") called!
D [05/May/2008:23:01:51 +1200] PID 6186 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [05/May/2008:23:01:51 +1200] cupsdSendError: 8 code=401 (Unauthorized)
D [05/May/2008:23:01:51 +1200] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [05/May/2008:23:01:51 +1200] cupsdCloseClient: 8
I [05/May/2008:23:01:51 +1200] cupsdCloseClient: SSL shutdown successful!
D [05/May/2008:23:01:51 +1200] cupsdCloseClient: 8
D [05/May/2008:23:01:51 +1200] cupsdAcceptClient: 8 from 192.168.1.4:631 (IPv4)
D [05/May/2008:23:01:51 +1200] encrypt_client: 8 Connection from 192.168.1.4 now encrypted.
D [05/May/2008:23:01:51 +1200] cupsdReadClient: 8 POST /admin HTTP/1.1

```

Here is my /etc/cups/cupsd.conf

```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel debug

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen 192.168.1.21:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow From All
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow From All
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
#  Require user @SYSTEM
  Order allow,deny
  Allow From All
</Location>

<Location /printers>
  AuthType None
  Order Deny,Allow
  Deny From None
  Allow From All
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set$
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS$
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Prin$
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#

```

Thanks in advance for any pointers!

---

### Post by Gooorn on 2008-05-06
Exactly the same thing is giving me an headache.

Anyone can help?

Thanx,

Sinisa Perovic

---

### Post by SumnerBoy on 2008-05-08
Can anyone help with this? Seems quite a few people are having the same problems.

---

### Post by nquinnathome1 on 2008-05-09
In cupsd.conf, add somewhere near the top (i.e. before <Location />)

```
DefaultEncryption Never
```

Should then allow you to access CUPS over a standard HTTP connection without requiring HTTPS

Failing that, I had a similar problem only it appears to be a bug where CUPS stops running when you try and authenticate, and I solved the problem here: [http://ubuntuforums.org/showthread.php?p=4916761#post4916761](http://ubuntuforums.org/showthread.php?p=4916761#post4916761)

---

### Post by *Timo* on 2010-01-19
Hello folks,

I have a KDC on a Mac server and I want to authorize CUPS (hosted on an Ubuntu server) against it. I'm struggling with this since three days and I'm really frustrated since I've googled so much and tried any suggestions available. Nothing helped, so I hope that I'll find support here.

Please find my config and log below:

cupsd.conf
```

# Allow remote access
Port 631
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultEncryption Never
#DefaultAuthType Basic
DefaultAuthType Negotiate
<Location />
  Allow from 10.153.158.*
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  Allow from 10.153.158.*
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
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
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Basic
    Require user root
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
</code>

```

excerpt from error_log
```
D [19/Jan/2010:15:57:27 -0100] cupsdReadClient: 26 POST /admin HTTP/1.1
D [19/Jan/2010:15:57:27 -0100] cupsdAuthorize: No authentication data provided.
D [19/Jan/2010:15:57:27 -0100] [CGI] /usr/lib/cups/cgi-bin/admin.cgi started - PID = 3476
I [19/Jan/2010:15:57:27 -0100] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=3476)
D [19/Jan/2010:15:57:27 -0100] cupsdSendCommand: 26 file=34
D [19/Jan/2010:15:57:27 -0100] cupsdAcceptClient: skipping getpeercon()
D [19/Jan/2010:15:57:27 -0100] cupsdAcceptClient: 27 from localhost:631 (IPv4)
D [19/Jan/2010:15:57:27 -0100] [CGI] admin.cgi started...
D [19/Jan/2010:15:57:27 -0100] [CGI] http=0x8e2ce28
D [19/Jan/2010:15:57:27 -0100] [CGI] op="add-class"...
D [19/Jan/2010:15:57:27 -0100] cupsdReadClient: 27 POST /admin/ HTTP/1.1
D [19/Jan/2010:15:57:27 -0100] cupsdAuthorize: No authentication data provided.
D [19/Jan/2010:15:57:27 -0100] CUPS-Add-Modify-Class ipp://localhost/classes/se
D [19/Jan/2010:15:57:27 -0100] cupsdIsAuthorized: username=""
E [19/Jan/2010:15:57:27 -0100] CUPS-Add-Modify-Class: Unauthorized
D [19/Jan/2010:15:57:27 -0100] cupsdSendError: 27 code=401 (Unauthorized)
D [19/Jan/2010:15:57:27 -0100] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [19/Jan/2010:15:57:27 -0100] [CGI] cgi_passwd(prompt="Password for lp on localhost? ") called!
D [19/Jan/2010:15:57:27 -0100] cupsdSendError: 26 code=401 (Unauthorized)
D [19/Jan/2010:15:57:27 -0100] cupsdSendHeader: WWW-Authenticate: Negotiate
D [19/Jan/2010:15:57:27 -0100] cupsdCloseClient: 26
I [19/Jan/2010:15:57:27 -0100] cupsdCloseClient: SSL shutdown successful!
D [19/Jan/2010:15:57:27 -0100] cupsdCloseClient: 26
D [19/Jan/2010:15:57:27 -0100] cupsdCloseClient: 27
D [19/Jan/2010:15:57:27 -0100] PID 3476 (/usr/lib/cups/cgi-bin/admin.cgi) exited with no errors.
D [19/Jan/2010:15:57:27 -0100] cupsdAcceptClient: skipping getpeercon()
D [19/Jan/2010:15:57:27 -0100] cupsdAcceptClient: 26 from 10.153.158.201:631 (IPv4)
D [19/Jan/2010:15:57:27 -0100] encrypt_client: 26 Connection from 10.153.158.201 now encrypted.
D [19/Jan/2010:15:57:27 -0100] cupsdReadClient: 26 GET /cups.css HTTP/1.1
D [19/Jan/2010:15:57:27 -0100] cupsdAuthorize: No authentication data provided.
D [19/Jan/2010:15:57:27 -0100] cupsdSendError: 26 code=304 (Not Modified)
D [19/Jan/2010:15:57:27 -0100] cupsdReadClient: 26 GET /favicon.ico HTTP/1.1
D [19/Jan/2010:15:57:27 -0100] cupsdAuthorize: No authentication data provided.

```

I think the biggest problem is that obviously, no credentials are passed to CUPS

```
cupsdIsAuthorized: username=""
```

and

```
cupsdAuthorize: No authentication data provided.
```

I would be so thankful if somebody could help..

Greetings,
Timo

---

### Post by *Timo* on 2010-01-20
really nobody? 

Sorry for stressing, but I really need some help.. thanks

---

### Post by *Timo* on 2010-01-20
well, that's frustrating. I hoped that I'll find some experts in this forum, but it seems like either there is none or nobody is interested in helping. That's such a pitty. :(

---

### Post by NCLI on 2010-03-19
Bump.

---

### Post by ShaneL on 2010-05-20
Hiya, just had some success getting pixma MP600 hooked up to Hardy using CUPS.
see more of my comments on another thread at
[http://ubuntuforums.org/showthread.php?p=9330959#post9330959](http://ubuntuforums.org/showthread.php?p=9330959#post9330959)
and links from there to good solutions (or at least potential answers to many of your hurdles)
Though some of the issues on this thread seem more network/server type glitches, my success may not be all you were hoping for, but one of the pages i referenced might back up a bit of the ideas on this thread...
anyhoo, hope it helps someone along the way :)

---

