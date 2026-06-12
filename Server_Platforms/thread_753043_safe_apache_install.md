---
title: "safe apache install"
date: 2008-04-12
forum: Server Platforms
---

### Post by kaurman on 2008-04-12
Hi!

I am planing to learn some PHP and because of that it would be good if I could test my applications locally.

If i install php5 and apache2 from synaptic, am I safe? My logic says that there should be no way of someone from the outside connecting to my pc (except Lan)... Still, I'd feel better if someone would confirm it.

My doubts actually seem silly, but I just have to ask:)

---

### Post by gbjazzman on 2008-04-12
If you are on a NAT behind a router, the only way that I'm aware of anyone who isn't on your lan access the apache server is if port 80 was routed to your server at the router.

I think there is also a way to only allow access to port 80 from localhost in iptables. Unfortunately, my iptable-fu isn't all that great.

---

### Post by andguent on 2008-04-13
Agreed. If you have any good router for your Internet connection, then no one can get to you except for anyone else at your place.

To fully test, try using ShieldsUp from [www.grc.com](www.grc.com) and let it do a port scan of your connection. If it doesn't see port 80 open, then no one else will see it open either.

And no, I wouldn't consider this a silly question. What I would consider silly is to expose your web server to the Internet because you don't know what you are doing, not bother to learn how to secure it properly, and hope you don't get hacked. :) You appear to be doing much better than that, I would call it 'an intelligent level of paranoia' long before I would call it silly. :)

---

### Post by kaurman on 2008-04-13
Hi!

Thank you very much for your answers.

My 80 is stealth, but I still have a few questions. AFAIK opening or closing ports actually depends on my ISP. So what happens if my ISP should for whatever reason open port 80? 

Am I automatically exposed to the world then? As I understand from what gbjazzman said, I'd be exposed only if I would manually define in my local router that all requests sent to 80 would be directed to my pc?

If that's the case, then I'd like to know, what happens to the request when 80 is open but my local router doesn't have any instructions on directing it to a specific computer.

All the best,

K

---

### Post by andguent on 2008-04-14
I would agree with gbjazzman above. By default, any router should block everything coming in unless you specifically allow it. Your ISP technically can block incoming web server traffic too if it wants. I don't think most do.

The ultimate answer is: you are safe, you have things configured fine. That will change only if you start playing with port forwarding on your router, or if you get a virus infected windows computer. :)

---

### Post by FakeOutdoorsman on 2008-04-14
You can prevent Apache from listening to any incoming connection attempts by editing: /etc/apache2/ports.conf.

change:
Listen 80

to:
Listen 127.0.0.1:80

This makes Apache listen only to your local machine.

---

### Post by kaurman on 2008-04-15
Hi!

Thank you all for your answers.

K

---

