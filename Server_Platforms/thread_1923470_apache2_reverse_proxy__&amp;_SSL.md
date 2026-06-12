---
title: "apache2 reverse proxy  &amp; SSL"
date: 2012-02-10
forum: Server Platforms
---

### Post by dbecker on 2012-02-10
Current ubuntu server1.dom.com is running apache2 and hosting a domain, along with a few sub-domains, each on different virtual hosts. Each virtual hosts is a seperate config. file under /ect/apache2/sites-enabled. 

I want to add 2 more dedicated web servers behind router firewall; server2.dom.com and server3.dom.com. 
server2 & server3 will need to have ssl certs installed.

For behind-firewall redirection, would this work?

1. fwd port 443 to server1 
2. create 2 virtual hosts on server1 for server2.dom.com and server3.dom.com
3. these virtual hosts would listen on port 443
4. generate/install a .key/CSR/.crt on server1 for server2.dom.com
5. generate/install a .key/CSR/.crt on server1 for server3.dom.com
6. setup reverse proxy for server2 & server3 virutal hosts that points to the actual server2 & server3 boxes

would I also need to generate/install a .key/CSR/.crt on the server2 and server3 boxes? 

thanks!

---

### Post by dbecker on 2012-02-13
ok, bought wildcard ssl cert from comodo.

Here's the config for the virtual host, listening on port:443:

```
ServerName timecard.domain.com
SSLEngine on
SSLCertificateFile /usr/local/apache/timecard_cert/domain.com.crt
SSLCertificateKeyFile /usr/local/apache/timecard_cert/private.key
SSLCertificateChainFile /usr/local/apache/timecard_cert/timecard.domain.com.cabundle
<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>
ProxyPass / http://server2/timecard/  <---web app. accessible from internal LAN only
ProxyPassReverse / http://server2/timecard/
<Location />
    Order allow,deny
    Allow from all
</Location>
```As you can see, the ssl encryption is between the client and the Apache virtual host. Communication b/t the Apache web server and internal server2 is on port 80. 

Everything works when visiting [https://timecard.domain.com](https://timecard.domain.com), just as if you were inside the LAN and accessing [http://server2/timecard](http://server2/timecard). 

Is this setup correctly?

---

