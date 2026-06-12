---
title: "How do I work with internal IPs and virtual hosts?"
date: 2009-04-22
forum: Server Platforms
---

### Post by TCarr on 2009-04-22
I have a Ubuntu 8.04 Server LTS LAMP server running in VMWare. I am using this as a test system and want to keep it contained in my own home network. I have a LinkSys Wifi router, and DSL. Can't afford a static IP.

In the LAMP server, I have

/var/www/public_html/mysite.com
/var/www/public_html/mysite2.net
/var/www/public_html/thesite.org

for example. Each has an entry in /etc/apache2/sites-enabled. Thing is, the server address is 192.168.x.x (let's use 192.168.1.100 as an example here, since I don't remember the actual address). The server hostname is cgi2.

I would like to map IPs like 192.168.1.200 for cgi2.mysite.com, 192.168.1.201 for cgi2.mysite2.net, and 192.168.1.202 for thesite.org for example. But I do not want it looking on the internet to do that. I want to be able to go to say, [http://cgi2.mysite.com/](http://cgi2.mysite.com/) and it display in the browser window the page: /var/www/public_html/mysites.com/index.html and show [http://cgi2.mysite.com/](http://cgi2.mysite.com/) in the browser address bar.

I believe I'm trying to do what's called an "internal DNS server"? 

Is there a way to do what I'm asking. I don't want those outside the internet to access these sites. They are just internal. Also I don't want to lose the ability to access the internet so I can do apt-get's. 

Any help would be appreciated.

---

### Post by Iowan on 2009-04-22
Maybe not related at all, but I found [this]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") page on name-based hosts.

---

### Post by daboroe on 2009-04-22
estenially this is something I want to do. exactly the same and have been researching it a little bit. The link/page that was given by Iowan looks like it should work. Currently I am not on my Ubuntu Machine but it looks like it should work.

---

### Post by TCarr on 2009-04-22
Unfortunately, directions on that page don't help. If I try to go to any domain in the server, I get my OpenDNS page saying it couldn't find the page.

---

