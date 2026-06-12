---
title: "how to calculate the transfer data of many virtual hosts?"
date: 2008-06-05
forum: Server Platforms
---

### Post by crixtiano on 2008-06-05
I have many virtual hosts in my ubuntu server.

I need calculate the transfer data of all http, smpt and pop3 access.

How to do that?

Thank you.

Cristiano Meira Magalhaes

---

### Post by hyper_ch on 2008-06-06
how do you calculate it for a single vhost?

---

### Post by crixtiano on 2008-06-06
hyper_ch,

I don't know, I don't calculate nothing ;)

But I really need to know do that.

Thank you.

Cristiano M. Magalhaes

---

### Post by hyper_ch on 2008-06-06
well, you can pipe your server through a router with logging and then you have the total traffic passing through...

or you could counts how much each individual vhost uses and add it up together....

Do you want to measure http traffic only or also ftp, ssh, whatever?

---

### Post by crixtiano on 2008-06-06
http, smtp and pop3 is more important, but It'd be very nice if I can do that control with other services.

Please, can you show me a way ?


Thank you.

Cristiano

---

### Post by hyper_ch on 2008-06-06
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

bandwidthd seems to be able to do that

---

### Post by crixtiano on 2008-06-06
hyper_ch, 

thank you for try to help me, but I think you didn't understand me.

I have a server (with 1 only IP address).

In this server I have many virtual domains:

domain1.com
domain2.com
domain3.com
...

Postfix , dovecote and Apache work with them. I need to calculate how many bytes in/out using each domain.

I knew the page you send me. Thank you for send me. But the tools in page calculate the values per IP and not per domain.

If you have another idea, please, tell me. 

:-)

Thank you very much again.

Cristiano

---

### Post by hyper_ch on 2008-06-06
how did you create those virtual hosts?

---

