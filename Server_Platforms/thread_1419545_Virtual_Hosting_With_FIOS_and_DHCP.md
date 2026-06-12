---
title: "Virtual Hosting With FIOS and DHCP"
date: 2010-03-02
forum: Server Platforms
---

### Post by cantdrive55 on 2010-03-02
I have a Ubuntu 9.04 server setup at home that I use as a personal webserver. I'm looking at building a site for a client but want to be able to use their domain name to point to my server instead of having them pay for shared hosting. I've looked into virtual hosting and have come up with these two hosts files but when I enable them both only site 1 seems to work. My IP changes every time the power goes out which is only about once a month but I still have my IP updated with no-ip.

I entered my current IP into my DNS records on namecheap but site1 still only shows up. If I try going to site2 it doesn't do anything. Do I just need to wait for the DNS to propagate?

```
<VirtualHost *:80>
	ServerName site1.net
	ServerAlias www.site1.net
	ServerAdmin xxx@xxx.com
	DocumentRoot /home/xxx/site1/
	</VirtualHost>

```

```
<VirtualHost *:80>
	ServerName site2.net
	ServerAlias www.site2.net
	ServerAdmin xxx@xxx.com
	DocumentRoot /home/xxx/site2/
	</VirtualHost>

```

---

### Post by noway2 on 2010-03-02
Your host declarations are fine.  The problem is with your dynamic IP address update.  I am not familiar with no-ip, but you will want to see if there is a way for the client(?) to update multiple sites.  Basically, each time your IP changes, both web sites need to be updated with the dns hosting provider.

Personally, I use dyndns, but I let my router perform the update.  Unfortunately, only one of the sites updates automatically,  When I detect the change, I need to log in and manually update the other one.  I don't know if ddclient, which may work for you too, will do multiple hosts.

---

### Post by cantdrive55 on 2010-03-02
I woke up this morning and it seems to be working! :)

The only other question I have is, when someone goes directly to my IP it comes up with site1. Is there any way for it to display nothing? Or maybe just timeout?

---

### Post by stlsaint on 2010-03-02
port forwarding will solve it going to your site. Just remove any ports being forwarded to your private ip. Then only those using your lan will see your site using your private ip. Nobody outside your lan will see your site.

---

### Post by cantdrive55 on 2010-03-02
I tried disabling all my port forwarding but that prevented me from getting to the sites at all. I have a dlink router setup with a virtual host port forward to my machine on port 80.

---

### Post by guessswh0 on 2010-03-26
The first thing is probably used because it is the first virtual host being declared in your file.  It appears that you are doing name-based virtual hosting.  If the user trying to connect to the web site does not provide a name (a domain name) but instead provides the IP address, Apache on your server obviously then cannot used name based VHost"ing" to make the differentiation on which website it should load.  Therefore, it will load the first entry in the configuration.

If you were to switch the order of them, it should then load [www.site2.com](www.site2.com)

The only way it will load a different site based on the IP address entered is if you are performing IP based virtual hosting.

---

