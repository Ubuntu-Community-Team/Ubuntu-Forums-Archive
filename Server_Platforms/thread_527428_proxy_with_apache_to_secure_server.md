---
title: "proxy with apache to secure server?"
date: 2007-08-16
forum: Server Platforms
---

### Post by sleepkreep on 2007-08-16
Hello all.  Here's my situation.  I have a splunk server that accepts connections on port 8000.  Unfortunately the free version of splunk does not include authentication methods.  So I set up an iptables rule to restrict access on port 8000 to a web server.  I need the web server to reverse proxy the connection to splunk through the apache server.  I have mod_proxy and mod_proxy_html installed and enabled.  However, I keep getting an access forbidden error.  Here's what I did:

create a file called splunk in /etc/apache2/sites-available/ on [www.domain.com](www.domain.com)
enable it with a2ensite splunk
The file contains:
     ProxyRequests off
     ProxyPass /splunk [http://splunk.domain.com:8000](http://splunk.domain.com:8000)
     ProxyPassReverse /splunk [http://splunk.domain.com:8000](http://splunk.domain.com:8000)

When I go to [www.domain.com/splunk](www.domain.com/splunk) I get a 403 (Access forbidden) error.
The ultimate purpose of this is to require authorization to [www.domain.com/splunk](www.domain.com/splunk) and have it be a proxy to splunk.domain.com:8000
Any ideas?

---

