---
title: "Setting Up a Home server"
date: 2010-07-10
forum: Server Platforms
---

### Post by Brando753 on 2010-07-10
Well, Im trying my best to setup a LAMP + XMPP + BBB server 
:D. Either way it not going to have high loads of traffic so I can get away with multitasking. The problem Im running into is Making virtual Apache sites, and getting them to connect. Here is what makes this task harder then what it may seem :D, Port: 80 blocked so am using Port: 8000, hooked up wireless (I know weird right.), has a router IP of 192.168.1.101 With port forwarding on, network has a real IP of  68.99.xxx.xx, the websites It will host are mundotg.co.cc , txug.co.cc . They are opensource projects :D.
Can someone give me a step to step guide on how to setup a server like this (both the Binddns and apache aspect), I have spent months following other guides online which just didn't work. Thanks so much for any help.

Also Im running ubuntu 10.4 server edition (CLI only) with ssh and webmin available.

---

### Post by Brando753 on 2010-07-11
I truly hate to bump threads but I do need to get this solved. :(

---

### Post by jma89 on 2010-07-11
If you have Webwin that'll be the easiest route. Although I must say I haven't had the best of luck with it.

Just go to the Servers > Apache module and then click the "Create Virtual Host" tab. Change only the port (to 8000, per your first post), document root (Something like /var/www/site1) and server name (Set to [www.whatasite.com](www.whatasite.com) or what have you.)

Apply the changes and it should be working fine. As a note: You may wish to change the default server's doc root to something like /var/www/default. Note, however, that this method of hosting requires the browser to pass along the requested hostname and not just the URI (What follows the ".com") If it doesn't then Apache will just serve up the default site, same as it would if you type in the IP directly.

If you can't get it to work that way you can always edit the directives manually.

In the Apache module of Webmin click "Global Configuration" and "Edit Config Files". You should see (at the bottom of that drop down list at the top) your sites-available. Pick the one that isn't behaving and click "Edit Directives in File" [And resist any Wall-E references.]

Here's what a basic site should look like (Note: The _default_ can be a * to accept connections on all IPs, like it should.)

```
<VirtualHost _default_:80>
DocumentRoot "/var/www/public"
ServerName localserver.whatasite.com
<Directory "/var/www/public">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

Hopefully that'll get you going. Apache can be tame at first, but it an also get downright picky. :-)

PS: I have no affiliation with [www.whatasite.com](www.whatasite.com). I just punched that in as a joke of sorts then noticed it was real. :-P

---

### Post by Brando753 on 2010-07-20
Well I got that far following this guide [http://library.linode.com/lamp-guides/ubuntu-10.04-lucid/](http://library.linode.com/lamp-guides/ubuntu-10.04-lucid/)
however I still have yet to get the DNS to work either on my side or the domain side, So what should I do?

---

### Post by jma89 on 2010-07-28
Sorry for the delay; I had forgotten to come back and check up on the status of this thread.

You should just set up DNS to point to your public IP, or to a redirecting service (so users don't have to specify port 8000 when trying to connect.)

Start simple: Make sure one of the domains is set to your public IP, and try going there by saying domain.com:8000 and see what happens.

If you need a DNS provider, I use dnsexit.com They've worked well for me, and only ask you to put a plain text link on your homepage paying homage to their services. :-)

---

