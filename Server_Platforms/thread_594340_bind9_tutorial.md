---
title: "bind9 tutorial?"
date: 2007-10-27
forum: Server Platforms
---

### Post by SilverTab on 2007-10-27
I just installed bind9 and webmin on my VPS but I never had to manage DNS before so I have really no idea what to do next..

Is there any tutorials out there that could help me? Basically my only goal is to have my GoDaddy domains point to my VPS...

I dont even know if I need bind9 to do it, but I know the VPS provider do NOT provide DNS info so I have to set up my own...

I have 2 ips, webmin and bind9...what do I do next??

Any help would be appreciated! :)

---

### Post by dantrevino on 2007-10-28
> **SilverTab said:**
> I just installed bind9 and webmin on my VPS but I never had to manage DNS before so I have really no idea what to do next..

Is there any tutorials out there that could help me? Basically my only goal is to have my GoDaddy domains point to my VPS...

I dont even know if I need bind9 to do it, but I know the VPS provider do NOT provide DNS info so I have to set up my own...

I have 2 ips, webmin and bind9...what do I do next??

Any help would be appreciated! :)

You dont need bind9.

GoDaddy will let you add an "A" record to point your domain to the IP address of your VPS.  24-48 hours for DNS to update, and you're set.

dan

---

### Post by SilverTab on 2007-10-28
> **dantrevino said:**
> You dont need bind9.

GoDaddy will let you add an "A" record to point your domain to the IP address of your VPS.  24-48 hours for DNS to update, and you're set.

dan

does this mean I only have to set my nameservers to my VPS ip addres and I'm set? or do I have to set this up differently?

---

### Post by SilverTab on 2007-10-28
Ok I think I figured it out....

I added an A record (@) that points to my ip address...

Now what should I set the nameservers to? (at godaddy)... the parked domain nameservers?

---

### Post by HermanAB on 2007-10-28
Anyhoo, if you wish to clue up on DNS, see [http://www.tldp.org](http://www.tldp.org)

---

