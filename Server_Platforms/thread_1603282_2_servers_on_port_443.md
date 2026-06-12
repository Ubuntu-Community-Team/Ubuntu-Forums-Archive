---
title: "2 servers on port 443"
date: 2010-10-22
forum: Server Platforms
---

### Post by rizla3066 on 2010-10-22
hello everyone, i could do with some help with running 2 ssl servers.
 
i already have a ssl server set up running on port 443 but i would like to add another ssl enabled server. how would i go about this and would the second server also be running on 443 or would it need another port config?

---

### Post by arrrghhh on 2010-10-22
You'd need another port, or if you're using apache you can use a virtualhost...

---

### Post by perspectoff on 2010-10-22
If both servers on physically on the same computer (i.e. at a single LAN IP address), then Apache2 virtual hosts are sufficient. There is lots of documentation regarding virtual hosting on the Apache wiki (see [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/) ). (There are many, many options, so this forum is not a good place to recreate the Apache wiki.)

However, if the two servers are on two different computers on the LAN (i.e. each at a different LAN IP address), then you will need a specialized type of virtual hosting called proxied hosts (aka reverse proxies).

In reverse proxies, the first computer has a "proxied host" virtual host file which refers any port 443 traffic meant for the second server to the second computer.

All port 443 traffic is initially routed from the router to the first computer, who then passes any traffic for the second server on.

Tutorials for reverse proxies are available at:

[http://ubuntuguide.org/wiki/Apache2_reverse_proxies](http://ubuntuguide.org/wiki/Apache2_reverse_proxies)

or

[http://kubuntuguide.org/Apache2_reverse_proxies](http://kubuntuguide.org/Apache2_reverse_proxies)

The tutorials use port 80, but, of course, the concept is the same. Merely use port 443 (or both).

---

### Post by rizla3066 on 2010-10-22
thanks for the quick reply, i should have give more info before
 
i am running ubuntu 9.10 with apache2, openssl
 
i have just been looking at the virtual hosts bit and know i should be adding something similer to;
 
[FONT=Courier New]NameVirtualHost *:443

<VirtualHost *:443>
[/FONT][FONT=Courier New]ServerName [www.domain.tld](www.domain.tld)
ServerAlias domain.tld *.domain.tld
DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:443>
[/FONT][FONT=Courier New]ServerName [www.otherdomain.tld](www.otherdomain.tld)
DocumentRoot /www/otherdomain
</VirtualHost>[/FONT]

 
but which config should i be editing now? 
apache2.config
ports.conig
httpd.config

---

### Post by SeijiSensei on 2010-10-23
Unless there's been some change recently, in the past you could not host multiple secure servers on one IP address the same way you can for insecure servers.  As I recall it has to do with matching the server's certificate to its registered hostname and IP address, but it's been a while since I've looked into this.

Instead you need a separate IP address for each secure server.  You can use Linux's method of creating multiple virtual interfaces to keep all the servers on one box.  Use eth0 for the first address, then eth0:0 for the next, eth0:1 for the third, etc.  Then use <VirtualHost IP:443> to define each host with its unique address.  You'll need separate certificates as well, of course.

---

### Post by Ryan Dwyer on 2010-10-23
Yes, what SeijiSensei said.

The request headers sent from the client are already encrypted, and they contain the hostname (eg. site.com). Apache needs the hostname in order to decrypt the request, so it can't do it. That's why it must use a unique IP address - it knows encrypted requests to a specific IP address must be for a certain hostname.

---

### Post by tbohaning on 2010-10-23
I beleive that if you have a wild card certificate with multiple host names assigned then having multiple SSL clients on a single IP should work fine.

---

### Post by BkkBonanza on 2010-10-24
Yes, I have used a wildcard with multiple hostnames on a single IP. But that's only for different subdomains. You should try setting a specific IP in the VirtualHost statement rather than using *. This may help as I have seen it work with multiple IPs on a single SSL port even though it is not supposed to. 

There is now support for SSL with multiple names on a single IP but it's rather obscure. You can google for it but if I recall in the end it usually isn't much use as it's poorly supported. 

I have run multiple domains on a single IP with SSL but I'm not sure now if Apache will do it or if it's because I use Nginx. However, it is true that it is not supposed to work. You will find that using * for IP in the statement definitely won't work - it must at the very least be tied with a specific IP value.

---

