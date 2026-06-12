---
title: "[SOLVED] Web Server and Subdomains"
date: 2008-08-18
forum: Server Platforms
---

### Post by The Titan on 2008-08-18
I have a server i have been using locally for a while and im getting pretty fimiliar with it.  I recently came into a domain name and i have it pointed to my IP address and it works fine. 

The problem is that i want to set up different services on this one server and one ip addresses with corresponding subdomains.  I tried just punching in the port via "ipa.ddr.ess.:21" in my DNS and it said invalid IP (figures).  

I have read about using Virtual Hosts in apache but im not very fimiliar with this (yet).  So, if anyone can help me out or just point me in the right direction that would be great.  

Note: The server is Ubuntu 8.04 Server Freshly installed with LAMP and SSH

-Dan

---

### Post by cdenley on 2008-08-18
> **The Titan said:**
> I have a server i have been using locally for a while and im getting pretty fimiliar with it.  I recently came into a domain name and i have it pointed to my IP address and it works fine. 

The problem is that i want to set up different services on this one server and one ip addresses with corresponding subdomains.  I tried just punching in the port via "ipa.ddr.ess.:21" in my DNS and it said invalid IP (figures).  

I have read about using Virtual Hosts in apache but im not very fimiliar with this (yet).  So, if anyone can help me out or just point me in the right direction that would be great.  

Note: The server is Ubuntu 8.04 Server Freshly installed with LAMP and SSH

-Dan

You need the DNS server for your domain to provide records for your subdomains as well. What is the output of these commands?
```

dig +short mydomain.com
dig +short sub.mydomain.com

```
Are you running your own DNS server? If not, what service are you using?

---

### Post by The Titan on 2008-08-18
> **cdenley said:**
> You need the DNS server for your domain to provide records for your subdomains as well. What is the output of these commands?
```

dig +short mydomain.com
dig +short sub.mydomain.com

```
Are you running your own DNS server? If not, what service are you using?
no i have a company that does my DNS, i want to have an SVN server and a web server and ftp and mail and such services and i want to point my dns to them but i only have 1 ip.

---

### Post by cdenley on 2008-08-18
> **The Titan said:**
> no i have a company that does my DNS, i want to have an SVN server and a web server and ftp and mail and such services and i want to point my dns to them but i only have 1 ip.

You only answered one of my questions. Do you have the DNS configured correctly for subdomains? If not, you need to work that out with the company that does your DNS.

After you have DNS configured, you just need to create new vhost or site configurations in /etc/apache2/sites-available. You can start out with a copy of default, but remove the top line (NameVirtualHost *). Inside the VirtualHost tag, set the ServerName variable to your sub-domain. If you want the vhost to be for mulitple domains/sub-domains, use the ServerAlias variable. To enable the site
```

sudo a2ensite sitename
sudo /etc/init.d/apache2 reload

```

You don't need to use subdomains for running multiple services on the same IP. Web, FTP, and mail all use different ports and can share a domain.

---

### Post by The Titan on 2008-08-18
> **cdenley said:**
> You only answered one of my questions. Do you have the DNS configured correctly for subdomains? If not, you need to work that out with the company that does your DNS.

After you have DNS configured, you just need to create new vhost or site configurations in /etc/apache2/sites-available. You can start out with a copy of default, but remove the top line (NameVirtualHost *). Inside the VirtualHost tag, set the ServerName variable to your sub-domain. If you want the vhost to be for mulitple domains/sub-domains, use the ServerAlias variable. To enable the site
```

sudo a2ensite sitename
sudo /etc/init.d/apache2 reload

```

You don't need to use subdomains for running multiple services on the same IP. Web, FTP, and mail all use different ports and can share a domain.
Yes it is configured correctly and this is exactly what i was looking for.  Thank you!

---

### Post by The Titan on 2008-08-19
Okay, Now I have everything running great, all my (web)subdomains work perfectly.  I have a couple more questions maybe somebody can answer.  

1.  Is it possible to have two different names for a virtual host? One for local and one for outside the network.  Because I can't directly access my domain because I get my modem interface. (If anyone knows a workaround for this please let me know)  Right now it works perfect outside the network, but i can only access one of the hosts from the browser locally.

2. How can i point a virtual host to another port or service like mail, ftp, or svn?  for example, when a client is gonna connect via ftp he uses an address like this "ftp.domain.com".


I appreciate your help on this topic.  I can only find tutorials and such that tell you exactly what to do and not why you do it and i found the documentation on this a bit confusing also...   I'm just really lost...

Edit: Sorry to double post =/

---

### Post by thefekete on 2008-08-19
1. To have a specific virtual host respond to multiple names, use the ServerAlias directive after the ServerName directive. For example:
```

ServerName     yourdomain.tld
ServerAlias    www.yourdomain.tld
ServerAlias    dev.yourdomain.tld
ServerAlias    anotherdomain.tld

```
It seems you can only use hostnames for the values. If can only access the server from the lan, a work-around would be to add the domains/sub-domains to /etc/hosts on your workstation pointing to the LAN IP of your server. Assuming your server is at 192.168.0.23:
```

192.168.0.23  domain.com
192.168.0.23  www.domain.com
192.168.0.23  ftp.domain.com
192.168.0.23  svn.domain.com
192.168.0.23  etc.domain.com

```
This will bypass external DNS lookups for these domains and automatically resolve them to the IP you specify. Apache should then see the request being for svn.domain.com, rather than 192.168.0.23.

2. I'm assuming that you have an svn, ftp and other services running on the same IP as your apache server. Unless you have web apps to interface these services, you don't want apache answering those requests.

Per your example, ftp.domain.com will resolve to your IP address. The only thing that differentiates this from an http request is the port number. Apache only listens on port 80 (by default). FTP clients will send the request to port 21, which will go to your ftp server automatically.

However, if you need apache to answer these requests, you need to do [port based virtual hosts]("http://httpd.apache.org/docs/1.3/vhosts/examples.html#port").

---

### Post by cdenley on 2008-08-19
It sounds like you are unable to connect to your WAN IP from within your LAN. This is a typical problem with routers. Some have ways around it, some don't. It depends on your router. You can also edit the /etc/hosts file on all the clients in the LAN, or you can setup a DNS server for your LAN to use that will resolve your domains to LAN IP's.

As thefekete said, its all about the IP address your ftp server is using. If ftp.mydomain.com resolves to the domain of the ftp server, then it should work. If mail.mydomain.com or [www.mydomain.com](www.mydomain.com) also resolve to the same server, then those can be used as well.

---

### Post by mbeach on 2008-08-19
great responses thefekete.

---

### Post by The Titan on 2008-08-20
> **thefekete said:**
> 1. To have a specific virtual host respond to multiple names, use the ServerAlias directive after the ServerName directive. For example:
```

ServerName     yourdomain.tld
ServerAlias    www.yourdomain.tld
ServerAlias    dev.yourdomain.tld
ServerAlias    anotherdomain.tld

```
It seems you can only use hostnames for the values. If can only access the server from the lan, a work-around would be to add the domains/sub-domains to /etc/hosts on your workstation pointing to the LAN IP of your server. Assuming your server is at 192.168.0.23:
```

192.168.0.23  domain.com
192.168.0.23  www.domain.com
192.168.0.23  ftp.domain.com
192.168.0.23  svn.domain.com
192.168.0.23  etc.domain.com

```
This will bypass external DNS lookups for these domains and automatically resolve them to the IP you specify. Apache should then see the request being for svn.domain.com, rather than 192.168.0.23.

2. I'm assuming that you have an svn, ftp and other services running on the same IP as your apache server. Unless you have web apps to interface these services, you don't want apache answering those requests.

Per your example, ftp.domain.com will resolve to your IP address. The only thing that differentiates this from an http request is the port number. Apache only listens on port 80 (by default). FTP clients will send the request to port 21, which will go to your ftp server automatically.

However, if you need apache to answer these requests, you need to do [port based virtual hosts]("http://httpd.apache.org/docs/1.3/vhosts/examples.html#port").
This was very much the answer i was looking for!  Thank you very much, up and running!

---

