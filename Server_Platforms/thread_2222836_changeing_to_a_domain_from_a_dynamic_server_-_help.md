---
title: "changeing to a domain from a dynamic server - help."
date: 2014-05-08
forum: Server Platforms
---

### Post by ulao2 on 2014-05-08
So I have a dyndns.org account that is free and now is charging. So I decided to buy a domain name. When I type in my old dyndns name it is set to point to my ip, as it should. So I set my domain up to do the same thing. but if I do:
[http://0.0.0.0(my](http://0.0.0.0(my) ip)/ some how the ip changes to my old dyndns.org domain. Also if I put in my new domain the same things happens. Looks like my new domain is in the dns pools. 

 I'm just about cretin linux is doing this as nothing else would know of my ip in the revers fashion like that. So somewhere in my config I must have set my domain to dyndns.org. I need to find this and change it I think?

To illustrate in text.

type in [http://here.dyndns.org](http://here.dyndns.org) goes to [http://here.dyndns.org](http://here.dyndns.org)
type in [http://(my](http://(my) ip address ) goes to [http://here.dyndns.org](http://here.dyndns.org)
type in my new domain name goes to [http://(my](http://(my) ip address ) the to [http://here.dyndns.org](http://here.dyndns.org)

did a grep in /ect and found nothing.

---

### Post by ulao2 on 2014-05-08
resolved by redirecting the dyndns to domain.

---

### Post by volkswagner on 2014-05-08
You should be removing dyndns from the equation.

I sounds like you already have some sort of redirect occurring on the server.

Once you cancel the paid services with dyndns.org, won't your "fix" stop working?

Check inside your webroot for an .htaccess file which may be doing the redirect.

You can check to see if you have any dyndns entries in your webroot by using grep.

```
sudo grep -R "dyndns" /var/www/webroot/directory
```

Or perhaps you added it to apache configs.

```
sudo grep -R "dyndns" /etc/apache2
```

---

### Post by ulao2 on 2014-05-09
yeah dyndns and my domain both pointed to the same ip, once I change that the problem was gone. Thx for the tips I checked the server over well, all if fine. Yes when I stop the dyndns service anything on the net with that old dyndns link will be dead. I have gone in to many forums and updated what I can. I guess its just like anything else, things change in life.

---

