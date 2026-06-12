---
title: "How to setup vhost and dns"
date: 2008-04-25
forum: Server Platforms
---

### Post by breezey on 2008-04-25
I just setup DNS server on my Ubuntu 8.04 that I use to run Apache2, PHP, MySQL. Setup was successful and I can access the server by hostname from another machines (both Linux and Windows box). dig and nslookup both seems to show correct result.

Now I am trying to setup vhost so that I can access websites hosted on my server by domain names.

Let's say my server's hostname is **myserv.com**
I want to access my websites on that server by
**web1.myserv.com** and **web2.myserv.com**

After creating the vhost I can access web1.myserv.com from local machine... but I can't access it from another machine. I guess I need to edit my DNS zone or something... anyone can help? Thank you.

---

### Post by Rohan Kapoor on 2008-04-25
DNS takes about 24-48 hours to update, so it could be that your sub-domain has not been updated into DNS systems yet. Try waiting and see what happens.

---

### Post by breezey on 2008-04-25
thanks for your reply darth-vader. But this is an intranet... shouldn't I expect to resolve immediately?

---

### Post by Rohan Kapoor on 2008-04-25
your welcome on the reply. What are your other systems that you are trying to access from. What Browser?

What is used for DNS

---

### Post by breezey on 2008-04-25
I am trying to access it from another Ubuntu box and Windows Vista.

I use Bind9 for DNS... is that what you meant? Thanks.

---

### Post by breezey on 2008-04-25
I figured that I should update my DNS zone file /etc/bind/zones/myserv.com.db and add a CNAME entry... I did that but it doesn't help

---

### Post by terazen on 2008-04-25
Do your internal devices do lookups directly off your dns server?  Can they ping web1 and web2?

---

### Post by adamos on 2008-04-26
add a web1.yourserver.com as an ns extra record and assign it the ip of your webserver and then the virtual host will do the job.

---

### Post by breezey on 2008-04-26
I got it... it was my vhost file that caused the problem... but i don't understand why that could be a problem.

Before, I set it up like this
```
<VirtualHost web1.myserv.com>
...

```
It worked only after I changed it to
```
<VirtualHost *>
ServerName web1.myserv.com
...

```

---

