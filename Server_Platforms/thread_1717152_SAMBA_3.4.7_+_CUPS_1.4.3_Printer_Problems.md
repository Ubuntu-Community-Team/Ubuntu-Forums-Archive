---
title: "SAMBA 3.4.7 + CUPS 1.4.3 Printer Problems"
date: 2011-03-29
forum: Server Platforms
---

### Post by compytechy on 2011-03-29
Our users are having issues printing through Samba-shared CUPS printers.  Here are the symptoms we're running into:


[LIST]
[*]When browsing to our Samba server, the printers will intermittently disappear from within Samba and return after a few minutes (this affects multiple computers)
[*]Users receive **[FONT=Verdana][B]"You do not have sufficient access to your computer to connect to the selected printer"**[/FONT][/B]
[*]The following error appears in several of the computers' Samba logs:  **"process_usershare_file: share name ::{2227a280-3aea-1069-a2de-08002b30309d} contains invalid characters (any of %<>*?|/\+=;:",)"**
[*]When trying to print, the following error appears in affected computers' Event Viewers: **"Application popup: sw: IEXPLORE.EXE - Application Error : The instruction at "0x7857d423" referenced memory at "0x24548b08". The memory could not be "read"."**  (It's not just IE, this error happens for Adobe Reader, MS Office).
[/LIST]
We've tried deleting printers and drivers and re-creating them on the local machines to no avail.

Here are snippets from our conf files:

**[/etc/samba/smb.conf]:**[INDENT]```
[global]
        .....
        load printers = yes
        printing = cups
        printcap name = cups
        printer admin = @"Domain Admins"
        .....
[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = yes
        write list = @"Domain Admins"
        browseable = no
        guest ok = yes
        writable = no
        printable = yes
        printer admin = @"Domain Admins"

[print$]
        comment = Printer Drivers
        path = /home/.samba/drivers
        write list = @"Domain Admins"
``` [/INDENT]**[/etc/cups/cupsd.conf]:**[INDENT]```
LogLevel WARN
MaxLogSize 0
SystemGroup lpadmin
SSLListen *:XXXXX
Listen *:631
Listen /var/run/cups/cups.sock
ServerAlias XXXXX.YYYYYYY
Browsing Off
BrowseOrder allow,deny
BrowseAllow from localhost
BrowseAddress localhost
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  .....
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  .....
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
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

# Set the authenticated printer/job policies...
<Policy authenticated>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
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
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
``` [/INDENT]Any troubleshooting steps you can recommend will be greatly appreciated; we need this resolved as quickly as possible.

Thank you!


-compytechy

---

