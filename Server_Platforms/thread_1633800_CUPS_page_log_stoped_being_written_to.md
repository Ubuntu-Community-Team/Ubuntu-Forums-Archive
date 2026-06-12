---
title: "CUPS page_log stoped being written to"
date: 2010-11-29
forum: Server Platforms
---

### Post by MrNatewood on 2010-11-29
Hello,

Using Ubuntu Hardy LTS Server edition, CUPS's page log has stopped working.
Prints being sent through the server are no longer logged.

What could be the cause of this?

Contents of the CUPS config file:

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
  # Restrict access to the server...
  Order allow,deny
  Allow localhost
  Allow 132.68.50.*
  Allow 132.68.58.*
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
  Allow localhost
  Allow 132.68.50.*
  Allow 132.68.58.*
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
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
Listen 127.0.0.1:631
Listen 132.68.50.*
Listen 132.68.58.*
Listen localhost:631
Listen /var/run/cups/cups.sock

Browsing on

# Only listen for connections from the local machine.
Listen 127.0.0.1:631
Listen 132.68.50.*
Listen 132.68.58.*
Listen /var/run/cups/cups.sock
```

Any ideas on how to fix this?

---

