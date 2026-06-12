---
title: "Setting up dedicated print server?"
date: 2016-05-01
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2016-05-01
I'm looking into LTSP again for my home use. I'm having trouble setting up printers with it so I'm thinking I may need to have a separate print server. Surprisingly I can find very little on how to set this up and what packages to use. I want it to be headless, most likely a virtual machine on my server or something. The printer will be attached directly to the print server and I'd like access to the cups interface from anywhere on my lan.

Everything google leads me to involves using a GUI in the Desktop distro so mostly useless for me. Any direction or suggestion, links or whatever would be appreciated.

---

### Post by volkswagner on 2016-05-02
To host a USB printer on a VM guest, you'll need [USB passthrough]("http://www.linux-kvm.org/page/USB_Host_Device_Assigned_to_Guest") on your hypervisor.
It may be easier to host on real hardware.

To share printers with other Linux LAN devices, [CUPS]("https://help.ubuntu.com/14.04/serverguide/cups.html") should be your solution.

---

### Post by SeijiSensei on 2016-05-02
You might consider something like a Raspberry Pi as the hardware platform for your print server.  Passing through USB ports to a VM is not an easy task.

You can access the CUPS control panel on the machine from anywhere on your network with a web browser:  [https://injustfiveminutes.com/2013/11/07/remote-access-to-cups-admin-inter/](https://injustfiveminutes.com/2013/11/07/remote-access-to-cups-admin-inter/). (To restart the daemon, use the command "sudo service cups restart" rather than the command presented in step 3.)

Before you go too far down this road, you might check to see whether your router can also function as a print server.  There are also [inexpensive standalone print server boxes]("http://www.newegg.com/Network-Print-Servers/SubCategory/ID-387?Order=PRICE") that might be easier to manage.

---

### Post by Tadaen_Sylvermane on 2016-05-02
Solved. Thank you for direction. Posting configs if others need them.

Installed cups on my main server / htpc and added my printer over the network to it.

/etc/cups/cupsd.conf. This makes server and web interface available over the network.

```
jason@micromachine:~$ cat /etc/cups/cupsd.conf 
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


# Only listen for connections from the local machine.
#Listen localhost:631
Port 631
Listen /var/run/cups/cups.sock


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
  Allow all
</Location>


# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow all
</Location>


# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow all
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


#
#

```
LTSP server /var/lib/tftpboot/ltsp/amd64/lts.conf. This points the clients to the remote cups server. Obviously substitute your print server ip instead of mine.

```

jason@ltspserver1604:~$ cat /var/lib/tftpboot/ltsp/amd64/lts.conf 
[Default]
    CUPS_SERVER=192.168.1.240:631

```

---

### Post by kurt18947 on 2016-05-02
I'm not a pro like SeijiSensei but if the printer does not have a network connection - ethernet preferably - I'd look at a standalone print server. I used one for a while, cheap little Netgear ethernet-parallel port gadget and it worked perfectly on an old HP printer. That poor box has enough to do:biggrin:.

---

### Post by Tadaen_Sylvermane on 2016-05-02
Don't print much at the moment. Right not just my wife and i also so it doesn't see much use. This is more testing for future purposes. Appreciate responses and suggestions. Marked as solved.

---

