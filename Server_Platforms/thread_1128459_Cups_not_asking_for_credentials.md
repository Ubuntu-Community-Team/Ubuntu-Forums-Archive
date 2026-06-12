---
title: "Cups not asking for credentials"
date: 2009-04-17
forum: Server Platforms
---

### Post by diederick76 on 2009-04-17
Hi everyone,

I'm having trouble with Cups policies. I have read [http://www.cups.org/documentation.php/policies.html](http://www.cups.org/documentation.php/policies.html), but I still can't figure out how to make cups ask for my user name/password. I have cups installed on a headless machine, so I access it over ssh and the web interface using another machine. Both are in the 192.168.2.0/8 range of the same network. I have added my user name and password on the server machine using:

```

lppasswd -a diederick

```

Still, when I go to the web interface and try to do stuff, it doesn't ask for my name and password, but just gives me a 403 forbidden. What am I doing wrong here?

Thanks for any help!

Here's my cupsd.conf:

```

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow 192.168.2.*
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order deny,allow
  Allow 192.168.2.*
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order deny,allow
  Allow 192.168.2.*
#AuthType None
#    Order Deny,Allow
#    Deny From All
#    Allow From @LOCAL
#    Allow From 192.168.0.0/16
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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


```

---

### Post by tgalati4 on 2009-06-14
Perhaps changing "Default" to "Basic" or "User" for all DefaultAuthType?

---

