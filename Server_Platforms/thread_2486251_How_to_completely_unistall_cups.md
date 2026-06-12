---
title: "How to completely unistall cups"
date: 2023-04-24
forum: Server Platforms
---

### Post by greg612 on 2023-04-24
I messed up.  I had it running perfectly and I messed with the config file on the upper right on main page. I lost all connectivity to it.   well long story short i uninstalled reinstalled but it kept the same config files.   How can I uninstall completely so i can start fresh.....  ya my fault lol   ubuntu server 22.04

---

### Post by #&amp;thj^% on 2023-04-24
first have a look at:
```
cat /etc/cups/cupsd.conf
```
I'll give mine to help you refer:
```
#
# Configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn
PageLogFormat

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Only listen for connections from the local machine.
Listen localhost:631
Listen /run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseLocalProtocols dnssd

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Web interface setting...
WebInterface Yes

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Restrict access to log files...
<Location /admin/log>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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

# Set the kerberized printer/job policies...
<Policy kerberos>
  # Job/subscription privacy...
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default

  # Job-related operations must be done by the owner or an administrator...
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Negotiate
    Order deny,allow
  </Limit>

  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Negotiate
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
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Negotiate
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```
No need to uninstall it>>>Yet lol

---

### Post by greg612 on 2023-04-24
couple difference   my browsing is on  and  
# Only listen for connections from the local machine.
Listen localhost:631
Listen /run/cups/cups.sock

mine is
port631
Listen localhost:631
Listen /run/cups/cups.sock

---

### Post by #&amp;thj^% on 2023-04-24
Your really only uninstalling just few cups applications IE:
```
sudo apt-get remove cups -y -s
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  bluez-cups cups hplip indicator-printers printer-driver-cups-pdf
  printer-driver-gutenprint printer-driver-hpcups printer-driver-splix

```
But if you look at this:
```
*me*&#57520;*~*&#57520;*dpkg -l | grep cups
ii  bluez-cups                                        5.66-0ubuntu1                              amd64        Bluetooth printer driver for CUPS
ii  cups                                              2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed                                      2.0~rc1-0ubuntu1                           amd64        OpenPrinting cups-browsed
ii  cups-client                                       2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                       2.4.2-3ubuntu2                             all          Common UNIX Printing System(tm) - common files
ii  cups-core-drivers                                 2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - driverless printing
ii  cups-daemon                                       2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters                                      2.0~rc1-0ubuntu1                           amd64        OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers                         2.0~rc1-0ubuntu1                           amd64        OpenPrinting CUPS Filters - Driverless printing
ii  cups-ipp-utils                                    2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - IPP developer/admin utilities
ii  cups-ppdc                                         2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common                                2.4.2-3ubuntu2                             all          Common UNIX Printing System(tm) - server common files
ii  libcups2:amd64                                    2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - Core library
ii  libcupsfilters1:amd64                             1.28.15-0ubuntu1                           amd64        OpenPrinting CUPS Filters - Shared library
ii  libcupsfilters2:amd64                             2.0~rc1-0ubuntu1                           amd64        OpenPrinting libcupsfilters - Shared library
ii  libcupsfilters2-common                            2.0~rc1-0ubuntu1                           all          OpenPrinting libcupsfilters - Auxiliary files
ii  libcupsimage2:amd64                               2.4.2-3ubuntu2                             amd64        Common UNIX Printing System(tm) - Raster image library
ii  printer-driver-cups-pdf                           3.0.1-14                                   amd64        printer driver for PDF writing via CUPS
ii  printer-driver-hpcups                             3.22.10+dfsg0-1                            amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  python3-cups:amd64                                2.0.1-5build3                              amd64        Python3 bindings for CUPS
ii  python3-cupshelpers                               1.5.18-1ubuntu1                            all          Python utility modules around the CUPS printing system

```
**EDIT: Please do not uninstall anything yet, I'm still trying to find why here?**
Notice a world of difference?
I'm still not clear on what you have done yet, What command did you use to remove cups?

---

### Post by greg612 on 2023-04-24
no command  on cups gui there is a config box on upper right side.  It shows basically  the same thing as your first post.   well  it didnt match what i did on install so i changed it to match.   that was the last time i could access it   I should have left it alone but nooooo   not me   so mad at myself

---

### Post by #&amp;thj^% on 2023-04-24
> **greg612 said:**
> no command  on cups gui there is a config box on upper right side.  It shows basically  the same thing as your first post.   well  it didnt match what i did on install so i changed it to match.   that was the last time i could access it

I NEED Details here, What cups-gui?
Also please paste back here in Code Tags this:
```
systemctl status cups
```
Should look like this:
```

&#9679; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; preset: enabled)
     Active: active (running) since Mon 2023-04-24 06:28:06 MDT; 5h 43min ago
TriggeredBy: &#9679; cups.socket
             &#9679; cups.path
       Docs: man:cupsd(8)
   Main PID: 9667 (cupsd)
     Status: "Scheduler is running..."
      Tasks: 1 (limit: 9067)
     Memory: 2.4M
        CPU: 29ms
     CGroup: /system.slice/cups.service
             &#9492;&#9472;9667 /usr/sbin/cupsd -l

Apr 24 06:28:06 me-Lenovo-Legion-5-15ARH05 systemd[1]: Starting cups.service - >
Apr 24 06:28:06 me-Lenovo-Legion-5-15ARH05 systemd[1]: Started cups.service - C>
```

---

### Post by greg612 on 2023-04-24
its what pop up when u go to localhost.    

&#9679; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-04-24 16:27:09 UTC; 1h 59min ago
TriggeredBy: &#9679; cups.path
             &#9679; cups.socket
       Docs: man:cupsd(8)
   Main PID: 8200 (cupsd)
     Status: "Scheduler is running..."
      Tasks: 2 (limit: 38252)
     Memory: 3.8M
        CPU: 42ms
     CGroup: /system.slice/cups.service
             &#9500;&#9472;8200 /usr/sbin/cupsd -l
             &#9492;&#9472;8204 /usr/lib/cups/notifier/dbus dbus:// ""

Apr 24 16:27:09 rockn systemd[1]: Starting CUPS Scheduler...
Apr 24 16:27:09 rockn systemd[1]: Started CUPS Scheduler.

---

### Post by #&amp;thj^% on 2023-04-24
Do you mean in a browser "[http://localhost:631/admin]("http://localhost:631/admin")"? (Take a screenshot from the link shown by me)
Your cupsd is running no issues there

---

### Post by greg612 on 2023-04-24
i cant get to it to show you    I cant sign in   

Unable to connect

Firefox can&#8217;t establish a connection to the server at localhost:631.

    The site could be temporarily unavailable or too busy. Try again in a few moments.
    If you are unable to load any pages, check your computer&#8217;s network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the web.

is all i get  i did something  in cups its self   I was connecting fine

---

### Post by #&amp;thj^% on 2023-04-24
Ok let's take a fresh aproach here, and run one line at a time:
```
 sudo dpkg -P --force-depends libcups2 cups-bsd cups-client cups-daemon libcups2:i386 libcupscgi1 libcupsmime1 libcupsimage2 libcupsppdc1 cups
```
You may see some Warnings but just Ignore
```
 sudo apt-get install -f
```
Now a make or break it:
```
 sudo apt install cups bluez-cups hplip printer-driver-gutenprint printer-driver-hpcups printer-driver-postscript-hp printer-driver-splix
```
You now should be able to configure your printers again

---

### Post by greg612 on 2023-04-24
ok did them one at a time   nothin changed still cant get to it    I really thank you for your time  but i must go to work  and wont be back for a couple days   again  thank you    i will check back  and look while gone

---

### Post by #&amp;thj^% on 2023-04-24
I'm out of Ideas, we basically rebuilt CUPS sooo???
Maybe something will show here:
Now this may have been changed>>>Default
```
cat  /etc/hosts.allow 
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "rpcbind" for the
# daemon name. See rpcbind(8) and rpc.mountd(8) for further information.
#

```
If your looks that way or** is minus "cupsd : all"**
Then edit to read like this:
```
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "rpcbind" for the
# daemon name. See rpcbind(8) and rpc.mountd(8) for further information.
cupsd : all
```
Restart cups:
```
sudo systemctl restart cups.service
```
Good Luck

---

### Post by TheFu on 2023-04-24
To completely remove cups, use 
```
sudo apt purge cups
```
Then I'd check the remaining cups libraries so see if any need to be manually purged too.

CUPS is how Unix systems print (usually), so you'll probably want to reinstall it.  Avahi and CUPS work together to setup "known" printers. If you have any issues printing, it is usually either
[LIST]
[*]unsupported printer
[*]application issue - for example, Okular has problems printing PDF files.
[/LIST]

---

