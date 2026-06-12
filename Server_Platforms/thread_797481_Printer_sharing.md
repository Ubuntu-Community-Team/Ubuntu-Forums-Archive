---
title: "Printer sharing"
date: 2008-05-17
forum: Server Platforms
---

### Post by satimis on 2008-05-17
Hi folks,


ubuntu 7.04 server amd64
IP 192.168.0.10


I'm prepared to allow other PCs on the network sharing the printer connected to the server.


$ apt-cache policy cupsys cupsys-client cupsys-common```

cupsys:
  Installed: 1.2.8-0ubuntu8.4
  Candidate: 1.2.8-0ubuntu8.4
  Version table:
 *** 1.2.8-0ubuntu8.4 0
        500 http://us.archive.ubuntu.com feisty-updates/main Packages
        500 http://security.ubuntu.com feisty-security/main Packages
        100 /var/lib/dpkg/status
     1.2.8-0ubuntu8 0
        500 http://us.archive.ubuntu.com feisty/main Packages
cupsys-client:
  Installed: 1.2.8-0ubuntu8.4
  Candidate: 1.2.8-0ubuntu8.4
  Version table:
 *** 1.2.8-0ubuntu8.4 0
        500 http://us.archive.ubuntu.com feisty-updates/main Packages
        500 http://security.ubuntu.com feisty-security/main Packages
        100 /var/lib/dpkg/status
     1.2.8-0ubuntu8 0
        500 http://us.archive.ubuntu.com feisty/main Packages
cupsys-common:
  Installed: 1.2.8-0ubuntu8.4
  Candidate: 1.2.8-0ubuntu8.4
  Version table:
 *** 1.2.8-0ubuntu8.4 0
        500 http://us.archive.ubuntu.com feisty-updates/main Packages
        500 http://security.ubuntu.com feisty-security/main Packages
        100 /var/lib/dpkg/status
     1.2.8-0ubuntu8 0
        500 http://us.archive.ubuntu.com feisty/main Packages

```
What additional packages I have to add?  Thanks


/etc/cups/cupsd.conf
```

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

```
Change "Browsing Off" to "Browsing On"?


```

# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
```
Change "Listen localhost:631" to "Listen 631"?


```

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

```


Add follows:```

Deny all
Allow 127.0.0.1

```


Then;
sudo /etc/init.d/cupsys restart


Please advise.  TIA


B.R.
satimis

---

