---
title: "CUPS server error"
date: 2009-12-09
forum: Server Platforms
---

### Post by atentik on 2009-12-09
After upgrading to Karmic, my printer was nowhere to be found. I tried adding a new printer System->Administration->Printing... but whenever I do, I get the following error:
> 
**CUPS server error**
There was an error during the CUPS operation: 'client-error-bad-request'
I spent about 2 hours trying to figure out what the problem might be but to no avail. I reinstall cups but nothing... Any suggestions?

---

### Post by atentik on 2009-12-11
It is a shame nobody got a clue

---

### Post by atentik on 2009-12-11
Ok, when I did >  tail /var/log/cups/error_log, I get the following error.
> Request from "localhost" using invalid Host: field ""
How do I change the localhost name?

---

### Post by Queue29 on 2009-12-11
> **atentik said:**
> Ok, when I did , I get the following error.

How do I change the localhost name?


Sounds like the update screwed your /etc/cups/cupsd.conf file. You need to open it up and fix things by hand. 

Here's a generic one that I made: 
[http://bozosort.com/dloads/cupsd.conf](http://bozosort.com/dloads/cupsd.conf)

You need to edit the ip's at the bottom to match your LAN.

---

### Post by atentik on 2009-12-15
> **Queue29 said:**
> Sounds like the update screwed your /etc/cups/cupsd.conf file. You need to open it up and fix things by hand. 

Here's a generic one that I made: 
[http://bozosort.com/dloads/cupsd.conf](http://bozosort.com/dloads/cupsd.conf)

You need to edit the ip's at the bottom to match your LAN.

Thanks for the information. I tried modifying my cupsd.conf file to reflect the one you sent but the error message > Request from "localhost" using invalid Host: field ""  persist. I changed the IP address as you advised. Any other alternative?

---

### Post by sloopveedub on 2009-12-16
I'm certainly no expert and arrive at this thread whilst dinking around with my own CUPS issues, but perhaps it would be helpful to post your /etc/cups/cupsd.conf file here.  Could be something as simple as a typo that another pair of eyes catches.

---

### Post by atentik on 2009-12-16
> **sloopveedub said:**
> I'm certainly no expert and arrive at this thread whilst dinking around with my own CUPS issues, but perhaps it would be helpful to post your /etc/cups/cupsd.conf file here.  Could be something as simple as a typo that another pair of eyes catches.

Hey, thanks. That's a good idea. Here we go.
> 
LogLevel warn
MaxLogSize 1m
SystemGroup lpadmin
# Allow remote access
ServerName 123.456.78.9
ServerAlias *
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols cups

DefaultAuthType Basic

<Location />
  # Allow shared printing...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>

<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
Require user @OWNER @SYSTEM
Order allow,deny
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order allow,deny
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Require user @OWNER @SYSTEM
      Order allow,deny
        </Limit>
  <Limit All>
        Order allow,deny
          </Limit>
</Policy>


---

### Post by sloopveedub on 2009-12-19
Are you able to access the CUPS web interface?

---

### Post by atentik on 2009-12-19
> **sloopveedub said:**
> Are you able to access the CUPS web interface?

Yes. I am able to do that. When I did that though, only the computers that have Ubuntu system connected to the server were able to print. All the others are unable to print, including the main server.

---

### Post by atentik on 2009-12-21
My eyes are hurting reading from the monitor everyday. Still can't print from my server. Any suggestion?

---

### Post by atentik on 2009-12-30
Still no solution to this problem? I hope I am the only one having this problem... cause it is not pretty having this problem and i don't want anybody else to go through it...

---

### Post by Muttley99 on 2009-12-30
Try adding;

[HTML]Listen 127.0.0.1:631
Listen lan_ip_address:80[/HTML]

If this works add;

[HTML]BrowseAllow from lan_ip_subnet (i.e. 192.168.1.0/24)
BrowseOrder deny,allow
[/HTML]
to secure it again

I had problems with the conf file recently; I also found them difficult to pin down!

---

### Post by atentik on 2010-01-18
> **Muttley99 said:**
> Try adding;

[HTML]Listen 127.0.0.1:631
Listen lan_ip_address:80[/HTML]

If this works add;

[HTML]BrowseAllow from lan_ip_subnet (i.e. 192.168.1.0/24)
BrowseOrder deny,allow
[/HTML]
to secure it again

I had problems with the conf file recently; I also found them difficult to pin down!

Tried this but to no avail. I am out of options now. Thanks to all those that tried helping.

---

### Post by atentik on 2010-02-04
Can someone help?

---

### Post by cdunham on 2010-03-14
Try adding:

ServerAlias *

to /etc/cups/cupsd.conf and restarting cups.

---

### Post by n4ym on 2012-04-06
I was having a similar issue in logfile (and showing 'Bad Request' in browser), so I tried a bunch of things with curl, mainly mixing combinations of the Host header and the actual hostname (IP) used in the connection (ocean is my hostname, and resolves in DNS):

Fail:[FONT=Courier New] curl -H 'Host: ocean:631' [http://ocean:631/printers/](http://ocean:631/printers/)[/FONT]
Fail: [FONT=Courier New]curl -H 'Host: ocean' [http://ocean:631/printers/](http://ocean:631/printers/)[/FONT]
Success:[FONT=Courier New] curl -H 'Host: localhost:631' [http://localhost:631/printers/](http://localhost:631/printers/)[/FONT]

It turns out my first two lines of /etc/hosts were:

[FONT=Courier New]127.0.0.1       localhost
127.0.1.1       ocean[/FONT]

I think this is a NetworkManager thing (oneiric)...

So while cupsd.conf had a Listen 0.0.0.0:631 line, cups did not like connections coming in on 127.0.1.1.
I removed the second line above and was able to connect...

---

### Post by shved on 2013-03-07
Maybe I last, but when I'm trying to connect from my laptop to PC's printer server, using hostname "shvedPC" from /etc/hosts I geted same error and 
<code> Request from "192.168.0.100" using invalid Host: field "shvedPC"</code>
lines in cups logs. Using real IP 192.168.0.100 in server's host addres solved my problem. Try to use 127.0.0.1 istead localhost.

---

