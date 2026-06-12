---
title: "is there anyway that I can redirect a website address?"
date: 2009-05-14
forum: Server Platforms
---

### Post by kustomjs on 2009-05-14
Hey Guys
I just wanted to know if there is anyway that I can redirect a website address say my mail server is on a different machine and my web server is on a other machine is there anyway that I can redirect it say from kustomjs.com to mail.kustomjs.com from one computer to other computer?

like this say from webserver from kustomjs.com (when somebody wants to access the webmail) re-directed to mail.kustomjs.com on a mail server for webmail only.

also the mail server and webserver is on same external IP but on 2 different internal ip addresses.

---

### Post by 3L33T on 2009-05-14
http uses port "80" by default.  In your router/firewall, use portforward to forward incoming tcp/80 to someserver.com (server 1).  If you want to also allow http access to a second server in your LAN, configure that http server to listen to another tcp port, say 77777, and in your router/firewall use portforward to forward incoming tcp/77777 to mail.someserver.com (server 2).

Use mail.someserver.com:77777 to access http server 2.  In fact, you can just do someserver.com:77777 to access server 2.

Use someserver.com to access server 1.

HTH

---

### Post by kustomjs on 2009-05-14
well see what I wanted to do is when you type in mail.kustomjs.com it would take you right to the webmail and I already know how to change the ports on apache but what I want to do is when somebody types into mail.kustomjs.com go directly to the webmail login page.

there is should be someway that you can have mod redirect from webserver under virtual hosting be directed to mail.kustomjs.com when somebody types in the web address.

can i setup like this under my webserver subdomain like:
mail.kustomjs.com pointing to my internal IP address?

---

### Post by justatemptest on 2009-05-14
> **kustomjs said:**
> 
can i setup like this under my webserver subdomain like:
mail.kustomjs.com pointing to my internal IP address?

No! Look for mod_proxy for apache.

---

### Post by kustomjs on 2009-05-14
hows this mod_proxy going to work?

---

