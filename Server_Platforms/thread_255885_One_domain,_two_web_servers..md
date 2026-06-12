---
title: "One domain, two web servers."
date: 2006-09-12
forum: Server Platforms
---

### Post by dickohead on 2006-09-12
Hey Guys,

I currently have a web server setup on my domain name which works great. I've now attached a second web server to my network and can access it locally fine. However, when not on my network (with port forwarding setup etc) I am unable to contact the second server.

The first server has port 80 forwarded to it.
The second server has port 8080 forwarded to it with /etc/apache2/ports.conf configured accordingly.

I can locally connect to port 8080 on my domain and get the web pages, but not remotely (where I am currently).

So.... I have hopefully narrowed the problem down to one of two things:

The fully qualified domain name on server2 is causing problems (currently unset)
Apache2.conf on server1 needs a virtualhost setup so that I can access the second server via a subdomain of the real domain name. ie:

VirtualHost server2.domain.com
Address server2.local.ip.address
Port 8080

Something like the above? I have tried figuring out VirtualHosts, but without knowing if that is my problem, I am unsure of what to expect.

The DNS and mx record for my domain name are held by another company, so any requests made to my domain name, get forwarded to my static IP address.

I am having trouble with this in terms of how the two web servers would communicate through my domain name, so even a link to a quick overview would be fantastic!!!

[/end brain dump]

---

### Post by Randomskk on 2006-09-12
I'd guess you need to do something like:
[http://domain.com:8080](http://domain.com:8080)

As far as I'm aware, you can't use DNS to have server2.domain to point to a different port. With one IP, you get one server and one domain name.

I don't see why you want two servers, though - just one can manage server1 and server2.
However, if server2's on port 8080, the best way to access it is just
[http://you-ip:8080](http://you-ip:8080) or domain.com:8080.

---

### Post by dickohead on 2006-09-12
that's what I have been doing. So there is no reason why having two machines one IP address at two different ports shouldn't be working?

I have this:

domain.com:80 - main web server
domain.com:8080 - new web server

I am slowly migrating to a new server, going to run one for files, one for web.

Maybe port 8080 is blocked by my ISP or something....

Thanks mate! I'll keep trying and when I find out what's wrong I'll report back.

I'll also get a diagram done to highlight the setup further.

Cheers,

Dickohead.

---

### Post by dickohead on 2006-09-12
Update:

Port 8080 is not blocked by my ISP. I think this is an apache config issue since I can access it locally just fine, but not remotely.

I have attached a very dodgey picture to highlight what I want to do eventually.

Two servers running off one domain name, one of them will be domain.com the other will be subdomain.domain.com, one running on port 80, the other on 8080 (or 81, 82 etc etc). The reason for this is that one will contain web pages, blogs, galleries etc, and the other will be used for remote connection to personal files via HTTP and FTP.

I have not setup any subdomains or virtual hosts as yet, all I am trying to do right now is get my apache server to show pages remotely on port 8080.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=15643&stc=1&d=1158113964[/IMG]

---

### Post by chrisfay on 2006-09-13
I am confused as to why you need a second server for this. If you have your subdomain's DNS records pointing to your IP running Apache, all you need to do is setup a virtual host with the root directory you want to server files from. There is no need to utilize another port let alone an entirely seperate server. 

Users can then get their files via the subdomain using ftp or whatever you want to do within the same Apache server on the same port. 

All you would need to do is add something like this to your /etc/sites-enabled/000-default page:

<VirtualHost *>
DocumentRoot /var/www/subdomainfolder/
ServerName sub.domain.tld
<Directory "/var/www/subdomainfolder/">
allow from all
Options -Indexes
</Directory>
</VirtualHost>

Obviously replace 'subdomainfolder' with the document root of your subdomain and replace sub.domain.tld with your subdomain.

> I can locally connect to port 8080 on my domain and get the web pages, but not remotely (where I am currently).
Can you access your server running on port 80 from outside your network?

> The fully qualified domain name on server2 is causing problems (currently unset)
If you don't have the FQDN set on Apache you will get log errors but it shouldn't effect access to the server. I had these errors until I added the ServerName directive but it did not effect anything. 

> Apache2.conf on server1 needs a virtualhost setup so that I can access the second server via a subdomain of the real domain name.

If you still decide to configure both servers, which seems unneccessary, you do not need to add anything to server1 in order to access anything on server2. All requests for internet traffic on port 8080 will go directly to the server listening on that port; assuming you add 8080 to your browser request. ie [http://xxxx.xxxx.com:8080/](http://xxxx.xxxx.com:8080/) otherwise they will default to port 80/server1.

---

### Post by dickohead on 2006-09-13
Redundancies, backups, server performance, network load etc etc. Many many reasons why I want two servers. But the biggest reason is so I can seperate the different bits of my network more easily. So the same server that does LDAP and Samba will serve out public_html folders via apache, and the server that has phpmyadmin, gallery2 and the main website is done on another machine. 

I know I could always setup some symlinks with samba across servers and have only one apache machine... which is a good idea having learnt from the above (thanks for that), but right now I am running two machines.... I will just do it via samba symlinks, but I was trying to migrate from one to the other and then have one as a live redundancy.

I also don't have access to my DNS informartion, it's hosted elsewhere, as my servers never had guaranteed service. But with my migration that should change and I can learn about BIND!

Thanks for the virtualhost info above too, that will come in really handy!!!

---

### Post by dickohead on 2006-09-14
I set my DNS hosting up with zoneedit.com and now everything is working as expected. I also discovered that my ISP does in fact block port 8080 despite them telling me otherwise.

Thanks for all your help!

---

