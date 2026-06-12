---
title: "Mail server and more"
date: 2005-08-08
forum: Server Platforms
---

### Post by Mugendai on 2005-08-08
I'm trying to set up this Ubuntu box to match, and hopefully beat this Windows box that is full of expensive software.

I want to get these things set up, these ways:

web, (Apache2 is already set up and running, I was already using that in Windows)

mail, trying to match Kerio Mail Server, which means, POP/IMAP, SMTP, SSL, SpamAssassin, Anti-Virus, and a very good webmail.
I've got the POP/IMAP(Courier), SMTP(Postfix), SSL, SpamAssasin, and Anti-Virus(ClamAV) part going. 
What I've been working on is getting a nice webmail going.  The main thing I am wanting from the webmail is tha ability to configure per user dropmail style content filtering.  Kerio let users configure filter rules that could check any of the headers for whatever, with rules like, begins with, ends with, and contains, as well as check the mail size, and attachment status.  It could also reject the mail, returning it to the sender(or some form of response to the sender).
I would really like to get an equivelent system set up.

router/firewall, again I am trying to matcha  Kerio product, Winroute Firewall.
KWF has a GUI admin system that I can access from across the network(important since I dont plan on being near the server for admin[have TightVNC already]).  It is a  very nice system allowing me to control all aspects of the fw/router, including DHCP server, DNS forwarder, statistics of connections, who is connected how, and it has a very nice rule set.  I love the way it's rule system works.  There is one kind of rule.  You can set it's source(which can be an interface, host network, range, user), destination, source port, destination port(ports can be set as protocals, port ranges, and can be set as TCP, UDP, ICMP, any and TCP/UDP), behavior(permit, drop, deny), nat(you can have it nat source or destination, or both addresses, to specific addressess, addresses of interfaces, and it supports DNS lookups), packet inspector(for things that need special handling, like HTTP[if you wanna filter/proxy it], ftp[to deal with port mode source address nating], etc.), and logging options.  Oh and I can simply enable/disable the rules if I need too, without actually deleting them.
I really like the idea that I can say, if the packet comes from here, to there, then route it here.  I could have two packets on the same port NATed differently based on origiona source/destination.  And could configure whether or not to dump the packet at the same time, with one rule.
It also has an HTTP transparent proxy that I can inspect webpages for content with, and remove content I dont want, as well as cache content.
Also has some nice spoofing prevention.

ftp, my current FTP on windows doesnt even do all that I want done(Filezilla).
I want to be able to throttle trafic, have symlinks followed, make virtual, not system users, permit for resuming of downloading and uploading, control the permissions of access for all paths, and be able to set path rules using atleast wildcards, if not full on syntax matching(ex. "/ftproot/dropboxes/*/upload" ).  Oh and I would liek to be able to see who is on, doing what, see statistics and be able to kick/ban people from some admin system.

hotline, (you prolly never even heard of this, and it shouldnt be a problem to get setup)

a dynamic dns updater, really the only domain I want to update is my main domain, which is a real domain, served by NameCheap, the updater would need to be compatible with that.  But I think even in this case, with a lil help I should be able to do it with a cron job, cause all it actually does to do the update is access a URL.  I just type in this web address including my domain, password key thing, and the new address, and it is updated like that.


Any input on any of this stuff would be very very much welcome.  The most important parts to me are the mail, and and router/firewall.  I'de love to be able to admin these things graphically(especially the firewall), but I would be willing to forgoe that for text files, if the text files are just as easy/powerful.

---

### Post by nocturn on 2005-08-09
[QUOTE=Mugendai]
What I've been working on is getting a nice webmail going.  The main thing I am wanting from the webmail is tha ability to configure per user dropmail style content filtering. 
[/quote]

I do not know Kerio or the features of most webmails, but if you search freshmeat.net, you'll find many options.

> 
router/firewall, again I am trying to matcha  Kerio product, Winroute Firewall.
KWF has a GUI admin system that I can access from across the network(important since I dont plan on being near the server for admin[have TightVNC already]).  It is a  very nice system allowing me to control all aspects of the fw/router, including DHCP server, DNS forwarder, statistics of connections, who is connected how, and it has a very nice rule set.  I love the way it's rule system works.  


You can just use SSH to connect to the Linux server.  The Linux kernel already has a firewall (packet filter) built in, what you need is something to manage/configure it like shorewall (or any alternative, there should be options with a WEB GUI out there)

> 
It also has an HTTP transparent proxy that I can inspect webpages for content with, and remove content I dont want, as well as cache content.
Also has some nice spoofing prevention.


Squid can do this for you, there are extensions to do many types of filtering.

> 
ftp, my current FTP on windows doesnt even do all that I want done(Filezilla).
I want to be able to throttle trafic, have symlinks followed, make virtual, not system users, permit for resuming of downloading and uploading, control the permissions of access for all paths, and be able to set path rules using atleast wildcards, if not full on syntax matching(ex. "/ftproot/dropboxes/*/upload" ).  Oh and I would liek to be able to see who is on, doing what, see statistics and be able to kick/ban people from some admin system.


I cannot help you here, ProFTP used to be nice but I haven't used an FTP server in years (replaced by SSH).


For remote admin to a lot of stuff, look into webmin (also on freshmeat).

---

### Post by Mugendai on 2005-08-09
> many options.
for webmail, so far I have tried SquirellMail and Horde, horde is looking doable

> just use SSH
ehh.. I really dislike the idea of exposing SSH to the net.
I know linux has the iptables/Netfilter.  You are right I am looking for a good configurator, or atleast scripting language to sit on top of it.
So far have tried Shorewall and FirewallBuilder, Firestarter prolly wont do it for me.  I like FBs rule system.  I have only messed with conrfiging shorewall via webmin, and there are parts I deffinetly wish were easier to do.  And I really really wish I could disable/enable rules with it, but alas I cant.

But what I would really like is a highly limited system, basically just a login, that once I log in to, certain ports would then allow me to access them via the IP I logged in from.  I don't like the idea of directly exposing something as powerful as webmin, ssh or VNC to the web.  While all of these would require secure logins, I'm still not keen about it.

> Squid can do this for you
I hope I can get it working without too much trouble.  Haven't gotten to this phase yet, but your tip is another knod toward it, it's what all signs have pointed at for me so far.

---

### Post by deuce868 on 2005-08-09
[QUOTE=Mugendai]ehh.. I really dislike the idea of exposing SSH to the net.
I know linux has the iptables/Netfilter.  You are right I am looking for a good configurator, or atleast scripting language to sit on top of it.
So far have tried Shorewall and FirewallBuilder, Firestarter prolly wont do it for me.  I like FBs rule system.  I have only messed with conrfiging shorewall via webmin, and there are parts I deffinetly wish were easier to do.  And I really really wish I could disable/enable rules with it, but alas I cant.
[/QUOTE]

Look into ssh configuration. You can specify in ssh as well as the firewall iptables rules what IP addresses are permitted to connect. SSH is always the first port I open up to the net, but properly secured because it's the most useful. How else would you get to the box from home on the weekend when things go wrong.  ;-) Plus you can use it with scp to move files back and forth and it's not in plain text like ftp.

---

### Post by Mugendai on 2005-08-12
[QUOTE=deuce868]You can specify in ssh as well as the firewall iptables rules what IP addresses are permitted to connect.[/QUOTE]
What I'de really like is an SSL web page I could log into that would then open the ports to the IP I'm connected with.

You know anything like that?

I might be able to get a php expert friend of mine to make me a lil portal like that.  I suppose all it would need to do is create a rule in iptables to open the port to the IP, then remove it on disconnect.  Prolly has to restart iptables too or something.

I would prefer this method as it means that to the general public, all these vulnerable ports are closed.  And they only open and only to the address I connect from when I login to the portal.  That way, port scans aren't going to turn up these things.

---

### Post by EwwBunToo on 2006-02-08
:) I've been using no-ip for dynamin updates for a while. I also use a smoothwall as a dedicated router/firewall ([http://www.smoothwall.org](http://www.smoothwall.org)) and it supports the dynamic updating for several services... including no-ip... no-ip is free for the basic service ([http://www.no-ip.com)](http://www.no-ip.com)). I've been running FTP, Mail (for several domains), and chat servers for the past couple years using it.

---

