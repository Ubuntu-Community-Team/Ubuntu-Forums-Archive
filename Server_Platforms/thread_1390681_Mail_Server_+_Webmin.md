---
title: "Mail Server + Webmin"
date: 2010-01-25
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-25
If I install the Mail Server from tasksel,my understanding is that installs postfix and dovecot.  I've installed Webmin and have a working LAMP configuration w/ phpMyAdmin.  I've forwarded ports 25, 993 and 995 for secure connections to my server box on the router and setup all appropriate MX records.

What other setup do I need to do to be able to send/receive email?  I have a dynamic IP from Comcast, but use ddclient to update it -- so no problem there.  Any thoughts?

---

### Post by volkswagner on 2010-01-26
You will need to edit the postfix config files.  The setup can be quite involved.  If you plan to host mail for more than one domain you will need to setup virtual mailboxes.  There is a comprehensive how-to provided by [Flurdy]("http://flurdy.com/docs/postfix/").  The how-to does not use dovecot however, it uses courier.

You will also need to use your isp as a smarthost or relay, since you have a dynamic ip address.  Most of the outside world will reject mail from dynamic ip's.

A simple alternative is to install Citadel.  It has a great web interface fro webmail and administration.  Since you are running Apache2, you will need to set up the mod-proxy directive for the web-client called webcit.  This is because webcit is a standalone web server and will conflict with the standard ports of Apache2.

---

