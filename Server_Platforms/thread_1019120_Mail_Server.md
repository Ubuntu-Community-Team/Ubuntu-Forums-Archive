---
title: "Mail Server"
date: 2008-12-22
forum: Server Platforms
---

### Post by Diverted Income on 2008-12-22
What is a simple to setup mail server to run on an Ubuntu Server? Small user list. Mostly local. Looking for advice.

---

### Post by spiderbatdad on 2008-12-22
I'm not sure simple and mailserver go together unless you're an expert. mailservers are hard to set up and need security, virus protection, spam filtering...
Try this for starters: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by windependence on 2008-12-23
Much easier would be Zimbra or Citadel. These are packages that have all the stuff you need for your mail server. Otherwise as SBD said, you will have to mess with lots of ugly stuff. 

-Tim

---

### Post by Diverted Income on 2008-12-23
> **windependence said:**
> Much easier would be Zimbra or Citadel. These are packages that have all the stuff you need for your mail server. Otherwise as SBD said, you will have to mess with lots of ugly stuff. 

-Tim

Are these command line interfaces only or GUI also? My ISP started blocking dynamic ip from hitting their mail server. Thats ok, but I have a couple NAS devices that report to via email and I sure miss that feature. That is why I was thinking something simple that would relay that to a SMTP server with credentials. The NAS boxes don't offer that. All they want is to spit it to a server with no authentication. I understand why the ISP did it, just want my notifications back. Any ideas?

---

### Post by Bachstelze on 2008-12-23
Setting up a mail relay with no authentication is bad, bad, bad. It basically means anyone can send mail through your server, which is obviously something that could put you in a lot of trouble.

Are the NAS boxes on the same LAN that your to-be mail server? If so, you would just need some IP-based filtering, and it would be simple to configure Sendmail or Postfix to do just that.

---

### Post by Tipo on 2008-12-23
This may be a dumb answer, but it seems like Ubuntu server comes with a mail server?: [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/mailserver]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/mailserver")

> Ubuntu Server Edition comes with an easy to set up mail server. To install it, just select it at the end of the server install process or launch the tasksel command on an already installed server. 
:-k

---

### Post by windependence on 2008-12-23
> **Diverted Income said:**
> Are these command line interfaces only or GUI also? My ISP started blocking dynamic ip from hitting their mail server. Thats ok, but I have a couple NAS devices that report to via email and I sure miss that feature. That is why I was thinking something simple that would relay that to a SMTP server with credentials. The NAS boxes don't offer that. All they want is to spit it to a server with no authentication. I understand why the ISP did it, just want my notifications back. Any ideas?

Both of these can be GUI configed from a browser.

The problem you are having is there is really no "mailserver" app per se, you have to build it from pieces and it can be daunting for someone new to it, or even for an old hack like me. :) I don't have time to mess with setting up postfix and courier, and spamassassin and clamAV, etc. These two packages integrate all of that into one nice configurable package.  When I set up e-mail for a client, I can't spend days setting stuff up, they want it to work right now, so I use these nice packages.

-Tim

---

### Post by Diverted Income on 2008-12-24
Yes the NAS boxes are on the LAN. Could I set this up to be a local mail server only then? That way i wouldn't need to set up rules and all the security, right????

---

### Post by windependence on 2008-12-24
Yes, you certainly could but the security is pretty much built in, and they tell you exactly what ports to open. It's really not that hard. I would just switch off the firewall in Ubuntu and use an externa; hardware firewall. It's easier and also a better solution.

-Tim

---

### Post by Diverted Income on 2008-12-31
Ok, so which package should I start with? Sorry, I have only been running this stuff for a few months. Thanks!

---

### Post by windependence on 2009-01-01
Well I like Zimbra, but if you you want to run other stuff on the box, it's a no go as Zimbra wants to be the only thing on the machine. Running it in a VM works great and there are even pre-built VMs you can download for that. Otherwise, Citadel should work while other things are loaded on the machine.

-Tim

---

### Post by Diverted Income on 2009-01-01
I'll pull it down and give it a try. I do need to run other services so I appreciate the info!

---

