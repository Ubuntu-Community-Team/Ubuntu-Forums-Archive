---
title: "Help with Domain Name and Dynamic IP"
date: 2006-11-15
forum: Server Platforms
---

### Post by Jeeevs2001 on 2006-11-15
Hello all, 

I currently use DynDns to allow me to SSH into my server remotely. Since setting this up I have got my own domain name and would like to 'attach' this to my server. I would like some advice on the best way to do this. My options (I think) are: 

1) to use the custom DynDns service to point my own domain to my dynamic IP - this has a cost. 

2) use web forwarding services offered by my domain name reg company to forward mydomain.com to mydyndnsdomain.com - but not sure that this will work. 

Is there a third option? 

Any advice will be appreciated. 

Jeeves

---

### Post by MJN on 2006-11-15
Sure - delegate your new domain name to [www.zoneedit.com]("http://www.zoneedit.com") (free) and use something like zoneclient ([http://zoneclient.sourceforge.net/](http://zoneclient.sourceforge.net/)) run as a cron job to keep the DNS updated.
 
The benefit that this has over Option 1 is that it doesn't cost, and over Option 2 is that doesn't require unnecessary mutliple/cascading DNS queries (and associated potential for delay/failure).
 
Mathew

---

### Post by Jeeevs2001 on 2006-11-16
Thanks for the info, I will look into [www.zoneedit.com](www.zoneedit.com). 

1 further question, Is it possible to have a web site hosted externally (ie by me ISP) and have people directed to that website, but when I try to ssh in, be directed to my own server? 

This would mean I could keep the website running without my 'home server' having to be on all the time. 

Thanks again 

Jeeves

---

### Post by MJN on 2006-11-16
Of course - just give your PC a different name. For example, [www.yourdomain.com]("http://www.yourdomain.com") would point to your ISP's web server, whilst whatevernameyoulike.yourdomain.com would be configured to point at your machine.
 
Mathew

---

