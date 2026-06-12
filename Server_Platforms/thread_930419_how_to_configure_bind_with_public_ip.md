---
title: "how to configure bind with public ip"
date: 2008-09-26
forum: Server Platforms
---

### Post by sins on 2008-09-26
Hi Friends,
 Please help to solve this problem
 I am using ubuntu 7.10,with a pubilc ip and also a private ip (192.168.0.10)
 here i configured bind for the local network (192.168.0.10 as dns server) its working properly  but i want to configure this for the public ip.
Then what changes i should apply and how to add additional domains to my dns server bcoz i am using this dns server for web hosting.

Advanced thanks for all replys...

---

### Post by sins on 2008-09-26
hmmm....
nobody is thr to help me....

---

### Post by Robstarusa on 2008-09-26
Sins>

The best way to learn about this is to go to [http://www.isc.org](http://www.isc.org) and look at the bind documentation.  Specifically you probably want to use "views" and then the "listen-on" directive (I believe in the named.conf options).  I believe it is called named.conf.local in ubuntu.

With views, you can return different responses based on the query hosts IP, subnet, etc.

If you can't figure it out, post here again & I will make a little more in-depth post when I have more time and my notes in front of me.

---

### Post by sins on 2008-09-26
thanks for the reply,
but still i am helpless with my probs.want more help..
its usgent for me....

Thanks.............

---

### Post by RealPSL on 2008-09-27
Your question is really not clear so I am going to take a guess at what you are looking for and recommend that you read about stealth DNS servers. If the answer is not clear after reading [this page]("http://www.zytrax.com/books/dns/ch4/index.html") please try to give us more details on what you are trying to accomplish.

---

### Post by sins on 2008-09-29
Friends i am afraid on it..
can anyone give ur email id for a remote solving of my issue..
Thanks to all...

---

### Post by sins on 2008-09-29
exactly what i want is.....

-> I need to create a domain nameserver: ns1.mydomain.com and assign static ip to on this server.
-> I then need to (using godaddy.com) point mydomain.com to those nameservers
   (with the assinged static ip)
->  I then need to create mail.mydomain.com and point it to those nameservers(ie mta machine is in my local network)
-> Finally i want know how do i point some other domains (for webhosting) in my ns1.mydomain.com machine.

Pls help me

advanced thanks...

---

### Post by RealPSL on 2008-09-30
Thanks for the explanation. The first step is pretty standard and is covered [here]("http://doc.ubuntu.com/ubuntu/serverguide/C/dns-configuration.html"). Review the section on primary master. Now you will need a secondary name server as well preferably on a different network. That is also covered in the above link. 

If you do not know how to set a static address then you can get that [here]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html").

The godaddy changes are pretty straight forward you just have to provide them the IP addresses of the DNS servers you are going to use for each domain.

Mail exchanger records are covered [here]("http://www.zytrax.com/books/dns/ch8/mx.html").

---

### Post by Alpha01 on 2008-09-30
> **sins said:**
> exactly what i want is.....

-> I need to create a domain nameserver: ns1.mydomain.com and assign static ip to on this server.
-> I then need to (using godaddy.com) point mydomain.com to those nameservers
   (with the assinged static ip)
->  I then need to create mail.mydomain.com and point it to those nameservers(ie mta machine is in my local network)
-> Finally i want know how do i point some other domains (for webhosting) in my ns1.mydomain.com machine.

Pls help me

advanced thanks...

Why would you want to run your own nameserver? I wouldn't recommend your site relying on the single nameserver to do the resolving for it.

---

### Post by sins on 2008-10-03
hiiiiiiiiiiiii..
atlast i made it as working......
sincere thanks for all who helped me...

if anyone hav doubts in its configuration contact me....

thanks to allllllllllllll

---

### Post by sins on 2008-10-03
once again thanks to alll...

---

