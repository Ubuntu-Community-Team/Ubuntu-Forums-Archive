---
title: "CUPS problem"
date: 2008-11-16
forum: Server Platforms
---

### Post by Chris_Foster on 2008-11-16
I have a headless ubuntu server, and I installed cups on it. I want to be able to configure it over a network. So that means I have to configure the web application to accept connections from a remote location (my computer on the LAN). Everytime I try to connect to it on the appropriate port, I get a connect failed response (firefox). Here is the part of my configuration file, I can print out the rest if nessesary, its just all of it wouldnt fit on the screen at once:
```

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Allow 192.168.1.68
  Allow 192.168.1.68/24
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Allow 192.168.1.68
  Allow 192.168.1.68/24
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  Allow 192.168.1.68
  Allow 192.168.1.68/24
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

```

I hope someone can help me with this issue, because its rather important...

---

