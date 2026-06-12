---
title: "Fqdn, mail, dns, I don't really know."
date: 2009-08-20
forum: Server Platforms
---

### Post by fuzzman54 on 2009-08-20
[FONT=Arial]I'm trying to set up email on my server and because I'm a complete n00b, I'm having some trouble. I am using this howto [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) and got stuck when installing "**amavisd-new". **It gave the error

 [/FONT]```
Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
[FONT=Arial]  The value of variable $myhostname is "beast", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
WARNING: Starting amavisd-new failed. Please check your configuration.[/FONT]
```I know that "beast" isn't a fqdn but I don't really know what I should set it to, or if I can actually set it to anything. I have a couple of domain names that are paid for and I could use, but I just have them pointing to my dyndns selfip.com because I don't really know what I'm doing. Could I use my selfip.com address? Or do I have to set up one of my real domains on the server? If I have to set up one of my domains, how do I do that, and is it even possible when the server's ip is constantly changing? And if you need to look at my settings or something, I have Webmin set up and will give you the information for it in a pm.

---

### Post by fuzzman54 on 2009-08-22
?

---

### Post by fuzzman54 on 2009-08-27
?

---

### Post by jay.parnaby on 2009-08-27
When you installed ubuntu did you set a domain name? For example all the machines I run at home run on a domain of home.lan

So in this case I would use machine_name.home.lan as the hostname for configuring postfix.

---

### Post by kustomjs on 2009-08-27
I would use a real domain name if you have one that would be your best route.

---

