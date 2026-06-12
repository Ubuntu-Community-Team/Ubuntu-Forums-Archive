---
title: "[Apache] Serving on Localhost"
date: 2011-07-12
forum: Server Platforms
---

### Post by ki4jgt on 2011-07-12
[http://ubuntuforums.org/showthread.php?t=470204](http://ubuntuforums.org/showthread.php?t=470204)

[http://httpd.apache.org/docs/current/mod/mod_authz_host.html#allow](http://httpd.apache.org/docs/current/mod/mod_authz_host.html#allow)
[http://httpd.apache.org/docs/2.0/mod/mod_access.html#allow](http://httpd.apache.org/docs/2.0/mod/mod_access.html#allow)

Checked into the Apache dev irc earlier. I was referred to the two apache.org pages above. I still don't quite understand what I'm doing guys. I've tried editing httpd.conf, ports.conf and 000-default. I've commented out lines from 000-default. I've altered allow statements from ports.conf and added an allow statement to httpd.conf. Each time I made sure to restart the server. What am I doing wrong?

What I'm wanting:
I'm wanting to only serve on localhost at port ****. I'm going to have Tor connect to localhost at that port, and be the intermediary between the server and users. I already have Tor configured. It's was pretty easy. I just set it up to listen on port **** and output at port 80. But I need all Apache connections to go through localhost:****
All help is appreciated. Thanks guys.

---

### Post by SeijiSensei on 2011-07-12
[http://ubuntuforums.org/showpost.php?p=11035949&postcount=4](http://ubuntuforums.org/showpost.php?p=11035949&postcount=4)

---

### Post by ki4jgt on 2011-07-12
> **SeijiSensei said:**
> [http://ubuntuforums.org/showpost.php?p=11035949&postcount=4](http://ubuntuforums.org/showpost.php?p=11035949&postcount=4)

Thanks, already did that step. Found out I had to switch allow,deny to deny,allow then allow from localhost:**** deny from all on the default. I'm thinking of writing a tut for it on my blog and on here. Then I had to add my URL name from Tor. Had to change the ports in ports.conf and then I was fininshed :-) If that makes any sense at all, thanks :-)

---

