---
title: "Server Monitoring?"
date: 2008-07-15
forum: Server Platforms
---

### Post by davidshq on 2008-07-15
Is anyone familiar with a server monitoring solution that offers a slick GUI for keeping tabs on server cpu/memory/disk/network utilization? Preferrably also with email/sms notification features. Finally, it would be awesome if it was hosted like mon.itor.us (which unfortunately, doesn't seem to have a linux agent).
David.

---

### Post by promodus on 2008-07-15
Zabbix :)

---

### Post by davidshq on 2008-07-15
Thanks. I like it. However, I think its a bit overkill for my situation. I'm looking to monitor at most 20 servers in all likelihood. Preferably the solution would be hosted (i.e. a saas application).
David.

---

### Post by windependence on 2008-07-16
Nagios (maybe too much for what you need)

GKrellm  [http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

Big brother (free edition) [http://www.deadcat.net/](http://www.deadcat.net/)

There are others also.

-Tim

---

### Post by umate on 2008-07-16
munin is pretty good, thats what i use. its really easy to setup aswell.

---

### Post by promodus on 2008-07-16
He's looking for a "Software As A Service" where it's hosted elsewhere. As google has their docs & spreadsheet online apps, he's looking for something similar but for monitoring.

---

### Post by windependence on 2008-07-16
That would take hardware level access from the web app to your server. I don't think anyone in their right mind would want to do that. :)

-Tim

---

### Post by unixbills on 2008-07-16
Hobbit (Big Brother)

We use both nagios and hobbit.  I like hobbit because I just leave a browser open to it and the entire left side of the screen is the color of your general condition - should be greeen.  So I have other windows open on top and just a little 1/2" edge of the hobbit screen shows.  When something goes red/yellow/purple it is easy to spot.  The entire left edge of my monitor goes red.  You can't miss it and you don't need to check it.  If I am at my desk I catch this before the email or sms message 99% of the time.

Note that if you install the hobbit-client with apt-get it will ask the address of the server but regardless of what you put "127.0.0.1" goes in /etc/default/hobbit-client and needs to be edited.

---

### Post by windependence on 2008-07-16
> **unixbills said:**
> Hobbit (Big Brother)

We use both nagios and hobbit.  I like hobbit because I just leave a browser open to it and the entire left side of the screen is the color of your general condition - should be greeen.  So I have other windows open on top and just a little 1/2" edge of the hobbit screen shows.  When something goes red/yellow/purple it is easy to spot.  The entire left edge of my monitor goes red.  You can't miss it and you don't need to check it.  If I am at my desk I catch this before the email or sms message 99% of the time.

Note that if you install the hobbit-client with apt-get it will ask the address of the server but regardless of what you put "127.0.0.1" goes in /etc/default/hobbit-client and needs to be edited.

I'll second that. I have used this one in a very large data center and it works great!

-Tim

---

