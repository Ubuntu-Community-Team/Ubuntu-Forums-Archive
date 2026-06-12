---
title: "cups authentication problems in 10.04"
date: 2011-01-22
forum: Server Platforms
---

### Post by raymondvillain on 2011-01-22
Can't print at all.  When I use the cups administration pages available on the browser ([http://localhost:631/](http://localhost:631/)) I can do just about anything EXCEPT print a test page.

For example, if I edit the cupsd.conf file I get a message box asking for my userid and password.  I click "authenticate" and the box goes away and I can edit the file, save it, and it restarts cups.  Everything seems to work fine.

But if I click on the "administation" tab, select "print test page" from the "maintenance" drop down box, I get the same message box asking for userid and password.  Only this time, after I click "authenticate", the box disappears briefly and then comes back.  Over and over and over.  I can't print a test page.

Finally, if I click "cancel", I get the browser page that says "401 authorization error".

Don't know what to do.  It seems odd that I can edit the cupsd.conf file, add and delete printers, modify printers, etc. but not print a test page.

This is the cupsd.conf file:

```
LogLevel debug
MaxLogSize 250
SystemGroup lpadmin
DefaultEncryption Never
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
  Allow @LOCAL #new
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
  Allow @LOCAL #new
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
#   Require valid-user
   Allow localhost
   Allow @LOCAL #new
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
#    Require user @OWNER @SYSTEM
     Require valid-user
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
#    Require user @SYSTEM
     Require valid-user
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType none
#    Require user @SYSTEM
     Require valid-user
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
#    Require user @OWNER @SYSTEM
     Require valid-user
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
#Require user @OWNER @SYSTEM
     Require valid-user
Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
#  Require user @SYSTEM
     Require valid-user
  Order deny,allow
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
#    Require user @SYSTEM
     Require valid-user
    Order deny,allow
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
#      Require user @OWNER @SYSTEM
     Require valid-user
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>
```

Does anyone know what to do?

---

