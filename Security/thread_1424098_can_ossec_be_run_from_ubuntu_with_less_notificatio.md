---
title: "can ossec be run from ubuntu with less notifications to mail only intrusions"
date: 2010-03-07
forum: Security
---

### Post by swimfish on 2010-03-07
can ossec be run from ubuntu with less notifications to mail only intrusions.

i really dont wish to be notified of every single thing that goes on in my system.  i only want to be notified of intrusions and anything else that would be of serious concern.  can anyone tell me what setting i can do to achieve the goal in mind ?

thank you

---

### Post by swimfish on 2010-03-07
gufw GUI for ufw, have some ports open but behind a closed port dd-wrt router with pnp enabled for other comps.  is my comp safe from internet intrustions ?

---

### Post by cariboo on 2010-03-07
IF you are behind a router, and you have no services running, there really isn't any need to enable the firewall on your system, even if you are running servers, unless the ports are forwarded to the router, there is no need.

---

### Post by Kinstonian on 2010-03-07
Check out the [manual](http://www.ossec.net/main/manual/configuration-options/#alerts_options).  I think you want to bump up the email_alert_level so only higher priority generate an email.

---

