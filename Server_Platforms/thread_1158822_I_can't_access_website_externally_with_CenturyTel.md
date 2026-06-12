---
title: "I can't access website externally with CenturyTel"
date: 2009-05-14
forum: Server Platforms
---

### Post by thinktyler on 2009-05-14
#sudo apt-get install apache2

changed port from 80 to 8085, 8000, 9091

Can access "it works!" from localhost

added ports to firewall for all of these ports, including dmz

I'm pretty sure the router 2wire gateway and it seems to be blocking access somehow.

Would setting up a proxy help in this case?

Is there any way an ISP could be blocking these random ports. I'm thinking this is strictly a router issue. 

I can't substitute the router because I live in an apartment where internet is included and I don't have the "PPOE?" name and password.

I'm at a lost, and I doubt anybody can help me, but It's worth a shot. Thanks.

---

### Post by a9k3d on 2009-05-14
The good news is that CTel doesn't block ports to home DSL (at least here).

Your problem may be that there is another router between yours and the internet - ie the apartment complex's router. There may be one line coming in, being spilt up to different buildings (yet another router).

Goto [http://ipchicken.com/](http://ipchicken.com/) to find out what your real external IP is. On CTel it will change every couple days unless you pay extra for a fixed IP.

Use that external IP to test access - have someone you know outside your apartment complex try accessing your server. This will tell you if you're working. Checking from the LAN side can fail for other reasons.

Some routers will not let you loopback from LAN->WAN->LAN - so if you ask for your external IP from the LAN side, the request goes into the router and then it gets mixed up because the request is for the external WAN connector. Yes these routers are super lame and hopefully getting rare. The one I found was fixed with a software update.

If you're up for your external friend but not internally, you can add your domain names to your /etc/hosts file with the internal IP address of your server.

---

### Post by thinktyler on 2009-05-15
Holy mother oley, your my hero, a saint and truly a gift from God. Please give me your paypal address so I can send you money. Heavens to bitsy! 

Awesome as hell, wwahooooooo! Long live the king!

---

