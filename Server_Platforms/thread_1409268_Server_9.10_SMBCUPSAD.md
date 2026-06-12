---
title: "Server 9.10 SMB/CUPS/AD"
date: 2010-02-17
forum: Server Platforms
---

### Post by Skavenger0 on 2010-02-17
Hi, i've been working this issue all day and am getting nowhere fast.

I have installed Ubuntu Server 9.10 and selected the options for File and Print services.

I have configured SAMBA to connect with active directory and make the necessary shares and permissions successfully. I can log in as a domain user and can browse to the server from windows.

When I try to access the CUPS web access [http://address:631/admin](http://address:631/admin).

I [COLOR="Red"]CAN[/COLOR] connect to [http://address:631](http://address:631) and then navigate to the administration tab but when I click "Add printer"

I get and prompt for a username/password. I have tried root/[admin account]/domain admin and none work. I have added these accounts using lppasswd aswel.
I have activated the listen for the remote web access to the cups server but the error is also happening on the local server. In desperation I installed fluxbox and firefox to test it locally without success.

When typing in any username/password from the password.md5 file it requests again. If I use the root or admin account it accepts the password but then says "Cannot connect to page"

I also thought it was the ssl requirment so i have added the line: DefaultEncryption Never.

This is all Internal LAN. There are no firewalls or anything getting in the way between client and server. Also Ill repeat that this is also happening when going to [http://127.0.0.1:631](http://127.0.0.1:631)

O and yes I have remembered to sudo /etc/init.d/cups restart after each config change

[COLOR="Red"]RED[/COLOR] = Changes
[COLOR="Blue"]BLUE[/COLOR] = Does anyone know if this setting could be the problem or solution

> #
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

[[COLOR="Red"]#Disable SSL Requirment
DefaultEncryption Never[/COLOR]

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Administrator user group...
[COLOR="Blue"]SystemGroup lpadmin[/COLOR]


# Only listen for connections from the local machine.
Listen localhost:631
Listen 127.0.0.1:631
Listen /var/run/cups/cups.sock
[COLOR="Red"]Listen 192.168.20.5:631[/COLOR]

# Show shared printers on the local network.
[COLOR="Red"]Browsing On[/COLOR]
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
[COLOR="Red"]  Allow From ALL
  Allow @Local
  Allow Localhost[/COLOR]
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
[COLOR="Red"]  Allow From ALL
  Allow @Local
  Allow Localhost[/COLOR]
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
[COLOR="Red"]  Allow From ALL
  Allow @Local
  Allow Localhost[/COLOR]
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
    Order deny, allow
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

#
#


---

### Post by Skavenger0 on 2010-02-18
Anyone have any Ideas?

---

### Post by santhony on 2010-02-25
sorry.. Wish I knew.. I'm also looking for instructions for a Karmic Samba AD and PDC...

---

