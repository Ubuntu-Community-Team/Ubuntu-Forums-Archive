---
title: "Configuring BIND with something easier than VI?"
date: 2009-02-18
forum: Server Platforms
---

### Post by doublearon on 2009-02-18
Hey guys, I'm setting up a new web server and my goal is to host more than one site on it. I'm wondering though, is there an easier way to configure BIND than just a text editor... like maybe a browser based user interface? It seems like there has to be a nice utility out there for this kind of thing other than, say, WHM.

Thanks in advance for your suggestions.

---

### Post by Iowan on 2009-02-18
I like **nano**, but it's still just a text editor.

---

### Post by doublearon on 2009-02-18
Sure, text editors are plentiful.. but I was hoping there's something out there that's easy to use like Cpanel, or WHM, but open source.

---

### Post by cariboo on 2009-02-18
You don't need dns services for web hosting, you setup the dns when you register your domain names. Why run an extra service when you don't need to.

Jim

---

### Post by doublearon on 2009-02-18
> **cariboo907 said:**
> You don't need dns services for web hosting, you setup the dns when you register your domain names. Why run an extra service when you don't need to.

Jim

Thanks for your reply Jim! I have just one static IP address, but I have a few domains I want to host. I'm not very savvy when it comes to dns, but I was under the impression that I could only setup one domain name per IP address through my domain registrar. Am I right?

---

### Post by shizzy-t on 2009-02-18
I think what cariboo907 is saying is that you could use a 3rd party DNS provider.  Like noip.org or easydns.  It would cost a little bit but they have an easy web-based interface for setting up name resolution.

---

### Post by Iowan on 2009-02-18
Dunno if it'll help, but [here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is an article on name-based virtual hosts.

---

### Post by cariboo on 2009-02-18
From Wikipedia:
> By allowing the use of unique alphabetical addresses instead of numeric ones, domain names allow Internet users to more easily find and communicate with web sites and any other IP-based communications services. The flexibility of the domain name system allows multiple IP addresses to be assigned to a single domain name, or **multiple domain names to be services from a single IP address**. This means that one server may have multiple roles (such as hosting multiple independent websites), or that one role can be spread among many servers. One IP address can also be assigned to several servers, as used in anycast networking.

When you use a 3rd party DNS provider you can register more than one domain per ip address as quoted above.

Jim

---

### Post by windependence on 2009-02-18
> **shizzy-t said:**
> I think what cariboo907 is saying is that you could use a 3rd party DNS provider.  Like noip.org or easydns.  It would cost a little bit but they have an easy web-based interface for setting up name resolution.
No, this is not what he was saying. Your domain REGISTRAR like Godaddy, Network Solutions, etc. usually has a DNS control panel which is where you configure your DNS for you domains such as the 'A' record, cname, and mx records. It is totally not necessary to run your own DNS server to host your web site.

As for hosting many domains on one IP, you need to configure name based virtual hosting in Apache to do this. 

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

[http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting](http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting)

[https://help.ubuntu.com/8.10/serverguide/C/httpd.html](https://help.ubuntu.com/8.10/serverguide/C/httpd.html)

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

There are many, many more tutorials on the web. If you need help, let us know.

-Tim

---

### Post by cteneyck on 2009-02-18
To answer your question i use webmin. its open source and will configure all Dns and virtual hosting. or you could use isp config for multible vhosts. im not sure but i think that isp config will configure bind dns for you

---

### Post by windependence on 2009-02-18
> **cteneyck said:**
> To answer your question i use webmin. its open source and will configure all Dns and virtual hosting. or you could use isp config for multible vhosts. im not sure but i think that isp config will configure bind dns for you

It sure will, but it's definitely not necessary.

-Tim

---

### Post by HermanAB on 2009-02-18
I have to second webmin and virtualmin.  Not as slick as cpanel, but it works.

The alternative is to install Mandriva or Suse, which have wizards for it all.

Cheers,

Herman

---

### Post by windependence on 2009-02-19
I actually agree with Hermann. Even as much of a CLI zealot as I am, I still use VirtualMin for quick setup of my commercial clients.

-Tim

---

### Post by sefs on 2009-03-23
ISPConfig was problematic for me on 8.04 with the MyDNS Server eating up the cpu.  I just installed virtualmin and I have to admit its sweet so far.  Just what Dr. Cassandra ordered.

---

### Post by BkkBonanza on 2009-03-23
While I know there are reasons to run your own DNS - for a situation with only a few sites/names it makes far more sense to just use the DNS that is usually provided by your registrar nowadays. 

To do DNS yourself properly for a start you should be running two servers preferably in two seperate locations. Some hosting companies will set you up with 2 ips and run it on one machine but that is actually worse than just using your name registrar's dns. On smaller machines or vps accounts there is just no need to waste valuable memory and cpu cycles doing dns. (Bind uses a lot of ram and on a vps I'd recommend setting up tinydns)

If you don't have access to good DNS control free from your registrar then transfer the domains to one that does. Or use a third party, like Sitelutions or Zonedit. I use name.com but there are so many now and you can try out the domain control panels before you move names or buy names.

---

### Post by Francewhoa on 2009-06-29
I wrote a how-to handbook at [http://ubuntuforums.org/showthread.php?t=1197883](http://ubuntuforums.org/showthread.php?t=1197883)
It covers installing BIND, Virtualmin, Webmin & Usermin.

---

### Post by windependence on 2009-06-30
I know you're trying to get the word out but cross posting is bad web etiquette.

-Tim

---

