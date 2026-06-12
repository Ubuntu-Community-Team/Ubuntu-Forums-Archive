---
title: "how to access second virtual host w/o using port numbert?"
date: 2009-03-08
forum: Server Platforms
---

### Post by cje on 2009-03-08
I have 2 virtual host;
1. default; for some web pages - using /var/www
2. "second"; for some other web pages - using /var/www2 and port 81

The problem is that I have the WPMU installed in www2 which do not allow me using port number.....

Anyone who has a suggestion on how to solve this w/o doing to big changes in virtual host?

Thanks for any suggestions

---

### Post by mrsteveman1 on 2009-03-08
What is WPMU?

---

### Post by cje on 2009-03-08
wpmu= multi user wordpress
mu.wordpress.org

FYI: a standard wordpress installation do accept the use of ports

---

### Post by JeppeM on 2009-03-09
Wouldn't using domains be good enough? you can read more [here]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html"). Otherwise, you can use another port then 81 perhaps?

---

### Post by cje on 2009-03-09
Thanks for your link and suggestion.

Anyway, using port (81) is not accepted by WPMU - so that's no solution in this case.

Further, using domain is not possible from LAN... as far as I know my ISP router.

---

### Post by volkswagner on 2009-03-09
> **cje said:**
> I have 2 virtual host;
1. default; for some web pages - using /var/www
2. "second"; for some other web pages - using /var/www2 and port 81

The problem is that I have the WPMU installed in www2 which do not allow me using port number.....

Anyone who has a suggestion on how to solve this w/o doing to big changes in virtual host?

Thanks for any suggestions

You may want to further explain.  Do you want the two sites on different ports?

Are you using individual vhost files?

Post your config. files (httpd.conf, ports.conf, vhost info.)

---

### Post by cje on 2009-03-09
I doesn't have access to the vhost files now but I'll try to give you some more or better explanation than above. 

First, everything is working fine from WAN. It's only WPMU which doesn't accept the use of port# from LAN. I doesn't have any problem with a "standard WP installations" on site2 or "n".

Before I had the need of accessing the site from LAN I was just using "<virtualhost *>" in all of my virtual host files. But, as I needed the LAN browsing possibility I added the port#.

So, my basic need is: 
how do I set up several VirtualHosts w/o using port# and with LAN browsing possibility... if possible?

My file info bellow
------------------------------------------

httpd.conf is empty
ports.conf listen to 80, 81, 82, 8080, 443

My Vhost files are similar to this - I may give you some more exact details later today if you wish.  

000-default
<virtualhost *>
DocumentRoot /var/www
...

001-site1
<virtualhost 192.168.10.2:81>
ServerName [www.site1.com](www.site1.com)
ServerAlias site1.com *.site1.com
DocumentRoot /var/www2/site1 
...

001-site2
<virtualhost 192.168.10.2:82>
ServerName [www.site2.com](www.site2.com)
ServerAlias site2.com *.site2.com
DocumentRoot /var/www2/site2 
...

---

### Post by volkswagner on 2009-03-09
I am still not sure if you want different ports.  Is your preference to use port 80 for all non-ssl sites?

To get named virtual hosts working you should add the following to httpd.conf

NameVirtualHost *


If you want all hosts to use port 80, after adding the above you can change all your vhost files to use <VirtualHost *>

Your problem with LAN vs WAN may be related to the router and NAT, and not your config files.  If NAT is enabled on the router, it may cause sites not avail. inside the LAN?

---

### Post by cje on 2009-03-09
Thanks for your suggestions.

Yes, port80 is preferred for all non SSL sites.
And, yes again - the ISP router doesn't allow browsing using domain name...

---

### Post by Brazen on 2009-03-09
You only have two options, either use multiple domain names or multiple ip addresses.  You should be able to use multiple domain names on you LAN by setting up a DNS server.  Setting up a local dns server is a bit complicated, but there is some good documentation in the server guide at help.ubuntu.com.

Using multiple IPs would be much easier.  All you have to do is set up the virtual ip addresses in your interfaces file and then define your virtual hosts based on ip addresses rather then defining them all with "*".

You define virtual ip address in the interfaces file, just like the address on your regular physical interface, but you define multiple virtual interfaces by appending ":#" to the physical interface name ( # represents an incrementing integer starting at 0 ).  So if your physical interface is eth0, you can add another ip addresses to it by defining a virtual interface eth0:0.

---

### Post by cje on 2009-03-09
Thanks a lot for your solution, Brazon. 
I didn't either thought about DNS server or multiple ip's. 
I'll give it a shot.

---

