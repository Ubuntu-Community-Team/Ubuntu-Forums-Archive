---
title: "Cupsys Trouble"
date: 2009-10-09
forum: Server Platforms
---

### Post by tybasher on 2009-10-09
I'm trying to install CUPS on my Ubuntu Server 9.04, and I cant seem to access it from the internet.

I ran > cat /var/log/cups/error_log
and then this came up

> E [09/Oct/2009:17:43:10 -0500] Unable to bind socket for address 192.168.2.1:631 - Cannot assign requested address.
E [09/Oct/2009:17:43:51 -0500] Unable to bind socket for address 192.168.2.3:631 - Cannot assign requested address.
E [09/Oct/2009:17:44:45 -0500] Unable to bind socket for address 24.166.151.154:631 - Cannot assign requested address.
E [09/Oct/2009:17:45:42 -0500] Unable to bind socket for address 192.168.2.2:631 - Cannot assign requested address.
E [09/Oct/2009:17:47:47 -0500] Unable to bind socket for address 192.168.2.2:631 - Cannot assign requested address.
E [09/Oct/2009:17:47:47 -0500] Unable to bind socket for address 24.28.193.9:631 - Cannot assign requested address.
E [09/Oct/2009:17:51:39 -0500] Hostname lookup for "192.168.2.*" failed!
E [09/Oct/2009:17:51:39 -0500] Bad Listen address 192.168.2.*:631 at line 17.
E [09/Oct/2009:17:51:44 -0500] Unable to bind socket for address 24.28.193.9:631 - Cannot assign requested address.
E [09/Oct/2009:17:52:20 -0500] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [09/Oct/2009:17:52:20 -0500] Unable to bind socket for address 24.28.193.9:631 - Cannot assign requested address.
E [09/Oct/2009:17:52:28 -0500] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [09/Oct/2009:17:52:28 -0500] Unable to bind socket for address 24.28.193.9:631 - Cannot assign requested address.
E [09/Oct/2009:17:53:45 -0500] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [09/Oct/2009:17:53:45 -0500] Unable to bind socket for address 24.28.193.9:631 - Cannot assign requested address.
E [09/Oct/2009:18:03:58 -0500] Unable to bind socket for address 24.166.151.154:631 - Cannot assign requested address.
E [09/Oct/2009:18:05:34 -0500] Unable to bind socket for address 24.166.151.154:631 - Cannot assign requested address.
E [09/Oct/2009:18:05:34 -0500] Unable to bind socket for address 192.168.2.1:631 - Cannot assign requested address.

my /etc/cups/cupsd.conf is as followed:

>  # Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen 192.168.2.4:631
Listen /var/run/cups/cups.sock
listen 192.168.2.1:631

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress 192.168.2.4:631

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription G$
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Act$
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


Any suggestions/help? Much appreciated.

---

### Post by Despot on 2009-10-10
I don't know much about CUPS, but I can give some general advice.

I think the line "Bad Listen address 192.168.2.*:631 at line 17." is important.

Also, you've got two "Listen" statements with different IP addresses. I doubt you want that.

> Listen 192.168.2.4:631
Listen /var/run/cups/cups.sock
listen 192.168.2.1:631

You might have a deeper problem with your network configuration...can your client ping your host and vice versa? Make sure you have basic connectivity before trying to run services.

---

