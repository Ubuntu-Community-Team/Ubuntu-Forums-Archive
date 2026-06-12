---
title: "How TO: Two Web Servers, One IP address = reverse Proxy"
date: 2012-02-05
forum: Server Platforms
---

### Post by volkswagner on 2012-02-05
I have seen this request several times.  I have also wanted to get this working myself.

Scenario, you have multiple Web Servers, either Physical or VM's, each with their own ip inside your LAN/firewall.
This can be two Linux servers, or Linux and Windows IIS, or any combination really.

Question:  How can you have more than one machine serve websites on port 80 with only one IP address from your isp?  

Answer:  Use Reverse Proxy.

This can be done using Apache2, Nginx or you favorite HTTP server.  I have chosen Apache2, but others may opt for Nginx when a light weight server is desired.

**QuickList**
[LIST=5]
[*]Decide which machine will be the "Main" Server.  This will be the server that has port 80 forwarded from your router.   This will be your proxy server machine.
[*]This assumes you have NameVirtualHosts already working on both servers.
[*]Enable proxy on your main server.
[*]Create a vhost (on main server) for you site that is hosted elsewhere.
[*]Reload apache and test.
[/LIST]

**Main server**
```
sudo a2enmod proxy_http
```  
```
sudo a2enmod rewrite
```
```
nano /etc/apache2/sites-available/site_hosted_elswhere
```
```
#This is for virtual host sites on server2 @ 192.168.1.3
<VirtualHost *>
        ServerAdmin webmaster@domain.com
        ServerName elswhere.domain.com
# You can have list of space separated aliases if you server2 hosts multiple domains
        ServerAlias elswhere2.domain.com elswhere.domain.com otherdomain.net
# If you have multiple hosts (NameVirtualHosts on server 2, you will need to preserve
# hostname, or you will always land at the root of
# the second server… ie: what ever the default site is.
        ProxyPreserveHost on
# Need to allow location / if you want the proxy to 
# work when no folder is written in the url.
         <location />
          allow from all
     </location>

# This is where all the magic happens. 
# You can modify the following for specific folders only and any remote host
# you can also specify a different port if you like
        ProxyPass / http://192.168.1.3/
        ProxyPassReverse / http://192.168.1.3/

</VirtualHost>
```  
```
sudo service apache2 restart
```

You should have a working setup.  Make sure to clear browser cache before testing.

---

### Post by SeijiSensei on 2012-02-05
Just a note to remind people we're talking about HTTP only here.  HTTPS requests don't easily lend themselves to being proxied.  It's [possible](http://httpd.apache.org/docs/2.2/mod/mod_ssl.html) but not for the faint-of-heart.  Usually the easiest solution is to forward traffic for port 443 to that port on the internal server.  You can use iptables for this task, or an application-level proxy like [this one]("http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/proxies/TcpProxy").

---

