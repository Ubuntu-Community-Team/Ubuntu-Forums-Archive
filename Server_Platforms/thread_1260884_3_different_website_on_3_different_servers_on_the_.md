---
title: "3 different website on 3 different servers on the same network"
date: 2009-09-08
forum: Server Platforms
---

### Post by nicosweden on 2009-09-08
Could someone pls help me setting up this.

I have a domain.com and i want to:

nagios.domain.com -> apache2 server1 port 80
webmail.domain.com -> exchange server2 port 80
site3.domain.com -> apache2 server3 port 80 
and sorry i have to add...

video.domain.com ->apache2 server4 port80 (zone minder)

I read a lot but i think i have lost my self..... :(

pls some help ?

thanks

---

### Post by Xipher on 2009-09-08
Any reason why setting each name to a unique IP address isn't possible?

---

### Post by nicosweden on 2009-09-08
> **Xipher said:**
> Any reason why setting each name to a unique IP address isn't possible?


I mean i need to reach them from outside the network and from my office i can use just port 80 (all the other are blocket) so to reach all my servers home i need to setup forward in apache

---

### Post by BadBoy4Live on 2009-09-08
He means, cant you give all of the servers a external ip address, because that would be alot easier to configure. Now your server have a ip addres of 192.x.x.x or 172.x.x.x or els. 

But i found a thread that might help you a litte( i think). In this thread there is a similar problem

[http://www.unix.com/unix-advanced-expert-users/11230-apache-config-one-ip-multiple-servers.html#post40384](http://www.unix.com/unix-advanced-expert-users/11230-apache-config-one-ip-multiple-servers.html#post40384)

---

### Post by R.Bucky on 2009-09-08
You could configure each server in Bind to have an separate internal ip (as they should) and then route appropriate traffic to each. No need for something uber complex. The concept would be similar to operating jail services.

---

### Post by samosamo on 2009-09-08
I don't have a fancy router capable of virtual hosts (not even sure they exist actually) so I use apache's ProxyPass module.  One server gets all the traffic, detects the virtual host, and proxies traffic to the server that I set.

I use Virtualmin GPL (the free one) as a GUI.  It's perfect.

---

### Post by kustomjs on 2009-09-08
yes you can put 3 different servers on 3 different internal IP's but if you want to access the servers from the outside of your network you can only have 1 port 80 on it if you want all 3 servers to be access your going have to do one server as 80 second server port 81 and 3rd server as port 83. you can just have all 3 servers access outside of your network on port 80 its not going to work that way.

you also want to put them as subdomain as virtual hosting like:

<VirtualHost *:80>
ServerName nagios.yourdomain.com
DocumentRoot /var/www/xxx/
</VirtualHost>

<VirtualHost *:81>
ServerName webmail.yourdomain.com
DocumentRoot /var/www/xxx/
</VirtualHost>

<VirtualHost *:82>
ServerName site3.yourdomain.com
DocumentRoot /var/www/xxx/
</VirtualHost>

<VirtualHost *:83>
ServerName video.yourdomain.com
DocumentRoot /var/www/xxx/
</VirtualHost>

that is how your servers should be setup.

---

### Post by X-Rated on 2009-09-08
Hi, long time lurker, 1st time poster.
I think I can help. this should allow you to access all your webservers from the outside on the standard http port 80.

1) route all http:80 traffic to a single server. http -> router -> server1

2) configure server1 for **NameVirtualHost** in apache.
Create a virtual host for each site.
[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)
> 
NameVirtualHost *:80

<VirtualHost *:80>
  ServerName [www.domain.tld](www.domain.tld)
  DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:80>
  ServerName [www.otherdomain.tld](www.otherdomain.tld)
  DocumentRoot /www/otherdomain
</VirtualHost>


3) configure on server1 each VirtualHost as a ReverseProxy in apache.
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)
> 
<VirtualHost *:80>
  ServerName [www.domain.tld](www.domain.tld)
  ProxyRequests Off

  <Proxy *>
    Order deny,allow
    Allow from all
  </Proxy>

  ProxyPass / [http://server2](http://server2)
  ProxyPassReverse / [http://server2](http://server2)
  DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:80>
  ServerName [www.otherdomain.tld](www.otherdomain.tld)
  ProxyRequests Off

  <Proxy *>
    Order deny,allow
    Allow from all
  </Proxy>

  ProxyPass / [http://server3](http://server3)
  ProxyPassReverse / [http://server3](http://server3)
  DocumentRoot /www/otherdomain
</VirtualHost>



4) make sure your external and internal dns/hosts file lookups work as expected.

---

### Post by kustomjs on 2009-09-09
just follow what I posted earlier then you wont have any problems.

---

### Post by nicosweden on 2009-09-09
i think i have not explained my self in the right way....


i have 3 ip addresses on 3 different servers.

1) Nagios  192.168.2.5/nagios
2) Zoneminder 192.168.2.6/zm
3)exchange   192.168.2.101/exchange

i want to ...

[www.domain.com/nagios](www.domain.com/nagios)   -> 1
[www.domain.com/zm](www.domain.com/zm) ->2
[www.domain.com/exchange](www.domain.com/exchange) ->3

could you pls help me with this ?


ps. thank you all for your replies

---

### Post by kustomjs on 2009-09-09
like I said before if you want it to see the servers outside of your network you need to change the listening ports on the servers like:

yourdomain.com:81/nagios
yourdomain.com:82/zm
yourdomain.com:83/exchange

so on......

---

### Post by infallible on 2009-09-10
Create a single virtualhost, *.domain.com , for apache on the main server.

make an index web page linking to domain.com/whatever

make samba shares on the other servers.

make a soft link to the samba shares "ln -s /target /var/www/domain/whatever"

use them as if they were folders on the local drive when writing head server html.

I think routing subdomains would be a much more elegant and efficient solution, however.

---

### Post by X-Rated on 2009-09-10
Hey infallible, that's a great idea, I never thought of that. Although it may not work if he has a MS Exchange server/IIS as a backend. I must remember that idea though.

---

### Post by recentcoin on 2009-09-10
You need to set up DNS then or something else to tell your port 80 request where to find the server you're looking for (e.g. nagios).  

One poster mentioned putting in a single server with redirects and you can do that using the IP addresses if DNS is too complex for you to handle.

---

