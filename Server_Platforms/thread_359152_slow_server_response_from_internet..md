---
title: "slow server response from internet."
date: 2007-02-11
forum: Server Platforms
---

### Post by kjacks on 2007-02-11
I need help finding why my applications are running slow when accessed from the internet but run quite fast when accessed by a computer on my home network.  Applications like Webmin, Torrentflux, SWAT, CgiProxy all run very slow when I access them from the internet.  I don't think it's my connection speed because if I tunnel my HTTP traffic thru my server using SSH (me being on the internet) I get 380kbps from speed test sites.  

Here's what I've got setup at home.  
Westell model 2200 DSL modem   - port forwarding all ports to my router
Linksys BEFW11S4 wirless router, but nothing all pc's are wired, -port forwarding all ports used by webmin, SWAT, torrentflux ...  to server (static IP )

Sometimes it can take a minute to load a simple page.  Where do I start to isolate what is causing this?

---

### Post by jhp-dk on 2007-02-12
If its browsing, try:

in Firefox write about:config in the adressbar
find "network.dns.disableIPv6" and set it to true

this speed a little up..

---

