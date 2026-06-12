---
title: "Can't view apache on Internet"
date: 2009-03-28
forum: Server Platforms
---

### Post by Spikerok on 2009-03-28
Error: I could not see your service on 92.23.91.16 on port (80)
Reason: Connection timed out

getting this error on [http://www.canyouseeme.org/](http://www.canyouseeme.org/). 
can view sites using lan ip

need help on how to fix this problem, allow me and others to view sites on server.

i'm not sure what type of info needed.

---

### Post by m3bik on 2009-03-28
Are you behind a firewall?

You might need to set up port forwarding on your router. Which would allow internet connections on port 80 to be forwarded to your local server...

---

### Post by Spikerok on 2009-03-28
im using ISPConfig

---

### Post by Spikerok on 2009-03-28
im not sure how to do it, ill have a look. don't mind if some one can help me on how to do it, my router is SpeedTouch

i have disabled firewall, still dont works

---

### Post by Spikerok on 2009-03-28
hmm.. i managed to unblock it

---

### Post by Spikerok on 2009-03-28
now i need to set up my domains some how.. because currently it dont works

---

### Post by Cope57 on 2009-03-28
Site is a good start, but that is not my IP... err wait, I am using a proxy, never mind. :D

Btw, check out [Markup Validation Service]("http://validator.w3.org") and fix the code.

---

### Post by m3bik on 2009-03-28
What kind of internet connection do you have? If you have a dynamic IP address (one that changes each time you connect to the internet) I'd recommend either [www.dyndns.com](www.dyndns.com) or [www.no-ip.com](www.no-ip.com)

Both companies provide either free or paid services. If you want to pay money, they can manage your domains for you... If you choose the free option, you're limited to a subdomain off of one of their domains...

BUT, there's a work-around. If you have a domain name registered, use a service like [www.zoneedit.com](www.zoneedit.com) to manage your DNS. You can use a CNAME entry to point your domain name (yourdomain.com) and any subdomain (sub.yourdomain.com) to your free account with either service. Your server would then recognize the domain and subdomain(s), not the free account address.

---

