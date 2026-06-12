---
title: "Ununtu Server -&gt; Print Server : Cant Find Server"
date: 2010-02-19
forum: Server Platforms
---

### Post by wwsoft on 2010-02-19
Hello ! I'm running a server for my local network it is a print server as wall as a web , ftp , and samba server. However I cannot get my local Ubuntu machines to recognize the printer I added to the server. Can I have some advice on how to get it recognized ? 

Thank in Advance !
Jason White

---

### Post by joberly on 2010-02-19
How are you making the printer available to the other machines?

---

### Post by wwsoft on 2010-02-19
yes

---

### Post by joberly on 2010-02-19
I said **how**, not just "are you". :)

---

### Post by wwsoft on 2010-02-19
Im accepting all connections on port 631. On cups share printer is checked.

Im not sure how to get to it

---

### Post by joberly on 2010-02-19
Check your /etc/cups/cupsd.conf file and make sure it isn't only listening on localhost.

Also make sure browsing is enabled, and BrowseAddress is set.

[This]("http://www.cups.org/documentation.php/ref-cupsd-conf.html") is a good reference.

---

### Post by wwsoft on 2010-02-19
Ok its found but ...

> There was an error during the CUPS operation: 'client-error-forbidden'

some config thing again ?

---

### Post by joberly on 2010-02-19
Did you do this on the client yet?

From the system menu, click System -> Administration -> Printing

From the window on the left of the printer configuration window, select "Server Settings".

Add a check next to "Show printers shared by other systems".

Click 'Apply' in the lower right corner.

Shared printers should now appear in the window on the left.

---

### Post by wwsoft on 2010-02-19
The client would not have found it if I had not already

in other words yes , and your suggestion seems unrelated to a permissions error

EDIT: I would like to know what to do to get permissions for my own printer (on the print server)

---

### Post by joberly on 2010-02-19
How about posting your /etc/cups/cups.conf file to take a look at? Put it inside the code brackets so it doesn't take up the whole page! :)

---

### Post by wwsoft on 2010-02-19
Your lucky I just installed xfce

just an edited standard confg

```

#
#
# Sample configuration file for the CUPS scheduler.  See "man cupsd.conf" for a
# complete description of this file.
#

# Log general information in error_log - change "warn" to "debug"
# for troubleshooting...
LogLevel warn

# Deactivate CUPS' internal logrotating, as we provide a better one, especially
# LogLevel debug2 gets usable now
MaxLogSize 0

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
#Listen localhost:631
#Listen /var/run/cups/cups.sock
#Listen 192.168.10.250:631

Port 631 # I edited here

# Show shared printers on the local network.
Browsing On # I edited here
BrowseOrder allow,deny
BrowseAllow all
BrowseLocalProtocols CUPS dnssd
BrowseAddress 255.255.255.255:631 # I edited here

# Default authentication type, when authentication is required...
DefaultAuthType Basic

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

#
#

```

---

### Post by joberly on 2010-02-19
Above where the Port directive is, use

Listen *:631 //just to make sure

Then,

DefaultAuthType none //not requiring authentication

Then,

<Location />
  Allow from All //allowing connections from all host/users
</Location>

Or if just localhosts you can use

<Location />
  Allow from @LOCAL //allow from localhosts only
</Location>

Save, restart the cups daemon, try again. I'll cross the fingers for you!

---

### Post by wwsoft on 2010-02-19
cant find again .. hmm

Im lost ...


Are there any "allow all" configs ?
If I tell it from the server it prints. If I try to find it from here , doomed to never print ...

---

### Post by wwsoft on 2010-02-20
Printer is now not being detected by cups itself , anybody know how to get that working ?

---

### Post by cariboo on 2010-02-20
I would suggest you use the cups interface at [http://localhost:631]("http://localhost:631") and setup your printer from there. Make sure your printer is supported by going [here]("http://www.openprinting.org/printer_list.cgi"), the server was down when I checked it so give it a couple of hours.

---

### Post by Queue29 on 2010-02-21
This question comes up over and over again. The default cups server settings are a disaster. You have to edit a config file on your client computers as well as screw around completely with the server's config file to make it usable. 

[http://bozosort.com/content/?p=19]("http://bozosort.com/content/?p=19")

---

