---
title: "No Access Using FQDN except when on the server."
date: 2012-11-08
forum: Server Platforms
---

### Post by deljones on 2012-11-08
Hi 

I have a small server with Wordpress, Zenphoto, Piwigo and ownCloud. Everything has been working fine but I did something list night, can't remember what but now if I try to access my site(s) using the FQDN I get a "File not found error" in the browser, no error number just the text.

If I try to access my sites(s) within my LAN using the ip address of the server everything works fine. No problem

Sounds like port forwarding?  No. Port forwarding is ok. Used a port checker and other services FTP etc work find using the FQDN inside and outside the LAN.

BUT if I sit at the server itself and use the FQDN it works!!

It would suggest a corrupt config file somewhere. I have spent the morning looking for a resolution. I managed to solve one problem which was the client was trying to download rather than show the index.php file but now Im left with this FQDN problem.

My install was with LAMP so my understanding is that the usual config files are not created or used? I might be wrong.

Ive multiple posted this but it was in error so sorry to all if Ive broken the rules. I didn't mean to.

Ive seen this problem on the internet and have tried all the fixes but with no joy..:(

Can anyone out there help?

Kind regards

Del

---

### Post by SeijiSensei on 2012-11-08
1)  I presume you have a domain registered somewhere and your nameserver has an A record for "host.domain.name" pointing to the public IP address of the firewall?

2)  In your Apache specification for the virtual host what do you have for ServerName?  Is it identical to the name people will be using from outside?  If the site has multiple names, you might need a ServerAlias directive as well.

---

### Post by deljones on 2012-11-08
Hi thanks for your response...

1. No. I just have a dynDNS entry to my public IP address (conistonmedia.webhop.net) which is normally the index page in var/www

2. The ServerName is the host name IBM which is the name I gave the machine when I built the box.

/etc/hosts:
127.0.0.1       localhost.localdomain localhost
127.0.1.1       IBM

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

/etc/hostname
IBM

Its all a bit frustrating.. Its a case of a little knowledge. So Im doing my best :)

Del

---

### Post by SeijiSensei on 2012-11-09
I can see [http://conistonmedia.webhop.net](http://conistonmedia.webhop.net) from here.

---

### Post by deljones on 2012-11-10
Hi...

Sorry I have been away since I last posted and have nly come back online. Finally my problem has been solved. It was a simple matter of a router reset.... :)

Not wanting to get into a spat with anyone online but I would like to point out that not only am I grateful to people who help me on forums I do actually thank them even if they have not been able to help me directly. This is a free and open community so we should all be grateful to each other...

So sorry if you have taken offence but I have no ideal what you are referring to in your last post. Maybe you should show some courtesy in back referencing what you are talking about. If you have any doubts about my manners please see all my posts.

In the meantime I would like to thank you for your help and advice, I have been away since I last posted and not been able to reply as quickly as you think I should have done

Kind regards

Derek Jones

---

### Post by SeijiSensei on 2012-11-10
> **deljones said:**
> So sorry if you have taken offence but I have no ideal what you are referring to in your last post.

That's my signature, Derek.  It was not directed at you.  It is just a general request for common etiquette.  You'll notice it is at the bottom of all my posts, including the other one in this thread.  Anything below that short line near the bottom of a posting is a signature.

I got tired of posting long answers to questions here then never seeing the questioner appear again.  It's been a rather persistent problem since I joined. I suspect some people post the same question on multiple sites, get an answer somewhere, and neglect to tell the rest of us.  Other people are just plain rude.

Sorry if you took it personally!

---

### Post by deljones on 2012-11-10
Doh.....

Im a dope.......

Sorry.......

Del

---

