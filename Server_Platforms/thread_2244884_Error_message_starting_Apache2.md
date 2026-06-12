---
title: "Error message starting Apache2:"
date: 2014-09-19
forum: Server Platforms
---

### Post by irv on 2014-09-19
I am getting this error message when I restart Apache2 server.

> * Restarting web server apache2                                                
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message

Was wondering what file I can fix to get rid of this error.

---

### Post by Lars Noodén on 2014-09-19
It's just a warning and can be ignored.  

But if you want tidy logs, that particular virtual host needs a [ServerName](https://httpd.apache.org/docs/2.4/mod/core.html#servername) directive and a corresponding DNS entry for that hostname.  If you do not have full DNS for your host names, then there are two work-arounds.  One would be if you are using dnsmasq for DHCP to put an enty in the dnsmasq configuration file to resolve that hostname.  Another would be to put the appropriate line in /etc/hosts.

---

### Post by irv on 2014-09-19
Thanks for the quick replay. I will mark solved.

---

