---
title: "alert when server goes down?"
date: 2007-08-28
forum: Server Platforms
---

### Post by tocleora on 2007-08-28
Hello, is there any way I can set up something on a 2nd machine that monitors my web server and sends me a text message on my phone as well as an e-mail to another e-mail address if it goes down?

---

### Post by tocleora on 2007-08-28
Hello, is there any way I can set up something on a 2nd machine that monitors my web server and sends me a text message on my phone as well as an e-mail to another e-mail address if it goes down?

---

### Post by jlintz on 2007-08-28
Yes,  check out nagios, [http://nagios.org](http://nagios.org).  Need to configure snmp on your machine or you could just use the ping plugin.  It will take a little reading to configure nagios but it's worth it.

---

