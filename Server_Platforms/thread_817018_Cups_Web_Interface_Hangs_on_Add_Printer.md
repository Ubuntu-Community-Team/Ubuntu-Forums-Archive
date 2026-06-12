---
title: "Cups Web Interface Hangs on Add Printer"
date: 2008-06-03
forum: Server Platforms
---

### Post by matthewboh on 2008-06-03
I have a headless server and I'm trying to get the Cups Web Admin working for remote access.

Okay - now I've got the CUPS error log which says that I'm not authorized to add/change/update printers.

I'll start looking on my own - but any pointers gladly appreciated!

I've gotten the default cupsd.conf and altered it

```
#
# "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $"
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
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
      Require valid-user
      Order Deny,Allow
      Deny From All
      Allow From 127.0.0.1
      Allow From 192-158.1.0/24
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew$
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-H$
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
# End of "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $".
#

```

I have also created a group called lpadmin and made myself I member of the group.  However, when I try to connect to the web admin page, I get a Page Load Error.

The web server is definitely up and running, and I have been able to connect with another version of the cupsd.conf file (but that wasn't allowing me to change printers).  Anyone have a cupsd.conf file that allows remote access?

---

### Post by matthewboh on 2008-06-03
Sometime I just confuse myself ----

Anyway - here's what fixed it

```
# Show general information in error_log.
LogLevel info
SystemGroup printer-admin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
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
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  # Allow remote access to the configuration files...
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow @LOCAL
</Location>
```

Hope this helps someone else....

---

### Post by Hedian on 2008-12-02
It did, actually even in making me feel stupid. ;)

---

