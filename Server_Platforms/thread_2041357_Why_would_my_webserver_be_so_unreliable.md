---
title: "Why would my webserver be so unreliable"
date: 2012-08-12
forum: Server Platforms
---

### Post by monkthemighty on 2012-08-12
I have a ubuntu server that is acting as a router. It also passes the websites to an other server the has the websites on it. Some the websites have been up and down for the passed two weeks. I had a bind set up on the router and that was going down all the time so I set it on a free dns hosting. On intodns it says that the dns servers are unreachable. Now when I look at whatsmydns.com it reports that all the websites are pointing to the right ip. We have about 7 websites. All of them but one are hosted on the other ubuntu server the other one is hosted on a windows server the one on the windows server is always up. The router has 3 ip addresses I use two different ip addresses for the websites. The one ip has the websites that are on the windows server and the other ip address is used for the websites on the ubuntu server. The server is using Apache to pass the traffic down to the other ubuntu server. I am quite new to this sort of thing. I just need some where to start. The only thing that had really changed on the router is updates. If I could just find a place to start it would be really great thanks.

---

### Post by SeijiSensei on 2012-08-12
If you have seven websites, I'm guessing this is more a business than a personal server.  

It's always much easier to host sites on servers that are directly on the Internet.  Either host them on the router box, or rent a virtual server from a provider like [Linode]("http://www.linode.com/").  

If you have a business-class IP account with a static address, see if your provider will give you a six-host IP subnet.  Then you can put the web server in the public space on one of those addresses and give the router a different address in that space.

---

### Post by monkthemighty on 2012-08-12
I don't think we can get an IP for every website. we have the 3 but why would I need an ip for each website. It was working before but for some reason it is having problems now. 

When i look at netstat and use grep to find 80 I dont see it on the list. I have started apache and made sure port 80 was in ports.conf. What could cuse this

---

### Post by SeijiSensei on 2012-08-12
No, you don't an IP for every website, just one for the server. After that you can use name-based virtual hosting in Apache.

On my server "netstat -avn | grep :80" returns the LISTEN line for the httpd daemon.

If you don't see anything listening on port 80, then you need to look at /var/log/apache2/error.log to see what's wrong.

---

### Post by monkthemighty on 2012-08-12
when i run netstat -avn |grep :80 I get 
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
is that all I need for apache to run right?

---

### Post by SeijiSensei on 2012-08-13
Well, it means that the daemon is listening on port 80 of all the interfaces ("0.0.0.0:80").  Whether Apache is correctly configured is an entirely separate question.  It sounds like your current system uses [mod_proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") to forward requests for the various sites back to the server(s) behind the firewall, which Apache calls a "reverse" proxy.  You should check the <VirtualHost> definitions for each site to make sure they have the correct ServerName (and, optionally, ServerAlias) directives for the various name-based hosts. 

Also check to make sure that the proxy is forwarding the requests back to the correct server IP address(es). Are the machines where the sites reside configured with static IP addresses?  That's pretty much mandatory for servers unless you use DHCP "reservations" to assign the server's IP based on its network adapter's MAC address.

---

