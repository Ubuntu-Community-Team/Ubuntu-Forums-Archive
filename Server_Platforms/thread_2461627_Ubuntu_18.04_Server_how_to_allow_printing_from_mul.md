---
title: "Ubuntu 18.04 Server how to allow printing from multiple vlans"
date: 2021-05-04
forum: Server Platforms
---

### Post by DantePasquale on 2021-05-04
Hi Everyone. I'm a bit confused on this issue. I am running Ubuntu 18.04.03 and have 2 printers USB connected to it. 

When my clients connect from on VLAN they see the printers

When they connect from the other VLAN (google mesh) they don't see ANY printers.

I'm at a loss as I enabled 'Internet Printing' thinking that would help, but it doesn't

```

LogLevel debug
PageLogFormat
MaxLogSize 1m
# Allow remote access
Port 631
Listen /run/cups/cups.sock
Browsing On
BrowseLocalProtocols dnssd
DefaultAuthType Basic
WebInterface Yes
<Location />
  # Allow remote access...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
</Location>
AuthType Default
Require valid-user
Order allow,deny
Allow @LOCAL
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
</Location>
<Location /admin/log>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy kerberos>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Negotiate
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Negotiate
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
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

---

### Post by gsahli on 2021-05-04
I don't think Internet Printing means anything in your context.
Please tell us more detail about how your two VLANS are connected: router/switch, nested routers, etc.

---

### Post by slickymaster on 2021-05-05
*Thread moved to **Server Platforms**.*

---

### Post by volkswagner on 2021-05-05
If your vlans are on separate networks (broadcast domains) then
you devices won't be discoverable (see the printer).

If you have firewall rules to allow traffic between the vlans you
should be able to specify the ip address of the host machine.

First test you can ping the host machine?

---

### Post by DantePasquale on 2021-05-10
After figuring out I could ping the 'server' for the printers, I was able to use the 'Add Printer' dialog and by using the IP in the search, the printers showed up

However, I still can't add them :(

It just says "Error Adding Printer" 

Any ideas?

---

### Post by DantePasquale on 2021-05-10
I do see these entries in the client journal

```
May 10 15:36:38 drai-blade.cocoanet.us org.gnome.ControlCenter.SearchProvider[2806]: mkdir failed on directory /var/cache/samba: Permission denied
May 10 15:36:38 drai-blade.cocoanet.us org.gnome.ControlCenter.SearchProvider[2806]: mkdir failed on directory /var/cache/samba: Permission denied
May 10 15:36:58 drai-blade.cocoanet.us dbus-daemon[1430]: [system] Activating service name='org.opensuse.CupsPkHelper.Mechanism' requested by ':1.211' (uid=1000 pid=11729 comm="gnome-control-center printers " label="unconfined") (using servicehelper)
May 10 15:36:58 drai-blade.cocoanet.us dbus-daemon[1430]: [system] Successfully activated service 'org.opensuse.CupsPkHelper.Mechanism'
May 10 15:36:58 drai-blade.cocoanet.us gnome-control-c[11729]: cups-pk-helper: addition of printer iX6550-TurboPrint failed: client-error-not-authorized
May 10 15:36:59 drai-blade.cocoanet.us gnome-control-c[11729]: Installation of the new printer failed.
May 10 15:36:59 drai-blade.cocoanet.us gnome-control-c[11729]: GtkDialog mapped without a transient parent. This is discouraged.
```

---

### Post by volkswagner on 2021-05-10
Please clarify the symptom.

Can clients on the same vLAN print to your share printers?

If clients on the same subnet can print but others can't perhaps
you need to enable "from any" via [cupsctl command]("https://www.cups.org/doc/sharing.html").

---

