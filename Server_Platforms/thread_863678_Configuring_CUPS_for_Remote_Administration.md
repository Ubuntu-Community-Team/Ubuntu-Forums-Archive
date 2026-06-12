---
title: "Configuring CUPS for Remote Administration"
date: 2008-07-18
forum: Server Platforms
---

### Post by duiu on 2008-07-18
I am attempting to run CUPS on my server (8.04). My printer is an HP Laserjet 4M Plus. I don't have X Windows on my server. I have/want to configure CUPS through a web browser on one of the other machines on my network. My cupsd.conf (attached) file is set to allow 192.168.1.* for 'location' 'location admin' 'config files' and 192.168.0/24 for the 'Listen' area. I tried going to [http://myserver:631/](http://myserver:631/) to configure it and get the 'IE cannot display the webpage' or 'Firefox is unable to connect screen.' I have not configured a firewall yet. I assume the default is to allow everything on the firewall. Any suggestions on why I can't connect to the CUPS admin? 

Note: I can ssh, though that's a whole different process and port.

Note: My server's hostname is 'mainhub'

---

### Post by laytek on 2008-08-07
duiu,

CUPS may not be starting. Check to see if the process is running.

Listen mainhub may cause an error and prevents CUPS from starting. Otherwise try Port 631 for a catchall.

LayTek

---

