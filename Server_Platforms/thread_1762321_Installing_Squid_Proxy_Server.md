---
title: "Installing Squid Proxy Server"
date: 2011-05-19
forum: Server Platforms
---

### Post by racheleson on 2011-05-19
Hi!
    I have finished connecting my clients to internet using the server.Now, I am planning to install a proxy server into my system. How should I do that? What are the configuration files needed? Any help please!...







weak24

---

### Post by Lars Noodén on 2011-05-19
In Firefox, you can get to the proxy configuration by the following menus:

Edit-> Preferences-> Advanced-> Network -> Connection Settings

---

### Post by SeijiSensei on 2011-05-19
Do a Google search for "squid transparent proxy".  You'll get lots of help.

---

### Post by elico on 2011-05-19
it's fariy simple in ubutnu.
just choose the performance version 2.7 or version 3 that has some more capabilities about content management...
then follow by small settings to allow your lan users to use the squid.
and if you do want it to be transparent then it will be quiet simple.
try to look at more specifics in:
[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

and:
[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

and this is old but almost the same jut skip the AV and CONTENT FILTERING part and use the wpad in the case you dont want to use transpatrent proxy.
[http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

---

