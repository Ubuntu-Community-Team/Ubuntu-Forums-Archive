---
title: "Apache 2.2 on Win XP SP2 only works for localhost"
date: 2006-06-22
forum: Server Platforms
---

### Post by linux_developer on 2006-06-22
Hi all,

I am at my wits end trying to set up a Apache HTTP server running on WinXP SP2. I know this is a Ubuntu/Linux forum, but I have run out of places to ask or to search, so if anyone can offer assistance it would be greatly appreciated :)

Some information about my system:
- Win XP SP2
- Apache 2.2
- NetComm NB1300 Plus 4 Modem/Router
- Forwarded port 8023 - My server
- Forwarded port 4662 - eMule
- Trying to run webserver on port 8023
-> To rule out the chance that my ISP blocks port 80, though it does not.
- I have a dynamic IP, but I check the ip (i.e. whatismyip.org) before I try connecting.
-> To rule out the problem of the connection failing due to a change in IP
- I try to access my server using the IP and not a domain name, i.e. [http://abc.def.ghi.jkl:8023](http://abc.def.ghi.jkl:8023)
-> To rule out the problem of zoneedit.com not working properly
- The server has a manually assigned IP of 192.168.1.24
-> To rule out the problem of the port being forwarded to the wrong ip
- Shut down all firewalls, including ZoneAlarm, Windows Firewall
-> To rule out failure due to firewall.
- Tried using a proxy to pretend to be a foreign user

I only can access the webpage from localhost, i.e. [http://localhost:8023](http://localhost:8023)

I cannot access the webpage from another computer on the same LAN., i.e. from 192.168.1.23. However ping works.

I purposely forwarded 4662 so that I can run emule. When emule is running and I try sniffing port 4662 at [http://myserver.org/CustomPortSniff.asp?po...2&Submit=Submit](http://myserver.org/CustomPortSniff.asp?po...2&Submit=Submit), it is listed as detected. If I close emule, it is listed as undetctable - which is correct.

However when I start apache, forward port 8023 and try to sniff the port, it is listed as undetectable, as if Apache is not running.

I changed Apache to listen on port 4662 and tried sniffing again but to no avail.

I tried running Apache on a different computer and updated the port forward but it still fails.

I really cannot figure out what is wrong - emule works as a server on a forwarded port (4662) perfectly, but Apache, even when running on port 4662, fails.

Any help would be greatly appreciated.

Regards,
linux_developer

---

### Post by x64Jimbo on 2006-06-22
I'd recommend turning off your WIndows firewall or specifically let port 80 through if you know how to configure the advanced options.

---

### Post by linux_developer on 2006-06-22
All my firewalls are turned off, i.e. Zone Alarm and Windows Firewall. Just curious, why should I open port 80 when I am running apache on port 8023?

---

### Post by mrcowcow on 2006-06-22
Mke sure these options are in your httpd.conf

Listen 8023

ipaddress:8023

Order allow,deny
Allow from all

If using virtual hosting:

<VirtualHost *:8023>
    ServerAdmin [email]user@example.com[/email]
    DocumentRoot "C:/whatever/"
    ServerName ipaddress
</VirtualHost>

And speaking from experience, running a webserver on Windows XP is a bad idea. I would reccomend using Linux, or is you must use Windows, use Windows Server 2003.

---

### Post by linux_developer on 2006-06-23
The settings in my httpd.conf file is:

Listen 8023
Servername localhost:8023

For the default directory, my settings are:
Order deny, allow
Deny from all

For my document directory, my settings are:
Order allow,deny
Allow from all

Please let me know if you think anything is misconfigured.

Regards,
linux_developer

---

### Post by mrcowcow on 2006-06-23
Try setting servername to *Servername ipaddress:8023*. They way you have it now may only be allowing requests from localhost. Using the ip should allow them from outside addresses and localhost.

---

