---
title: "Desktop ubuntu server installed DNS ?"
date: 2008-04-13
forum: Server Platforms
---

### Post by mraiur on 2008-04-13
Hi i installed ubuntu 7.10 desktop for server usage and i done everything so far i bout a domein but dont know how to make publick name servers so i can associate the domein to the computer becouse i dont like the idia for a frame redirect .
i installed from the instructions here -> [http://www.howtoforge.com/perfect_setup_ubuntu704_p2]("http://www.howtoforge.com/perfect_setup_ubuntu704_p2")
Can enyone give me information how can i make such a ting ? thx all i will go to sleep no its 5 in the morning here ... good night all :) and goodbye for now :)

---

### Post by p_quarles on 2008-04-14
Moved to Server Platforms.

---

### Post by hyper_ch on 2008-04-14
at the place where you bought the domain you will need to add nameservers.... this sort of requires one or two static IP addresses... depending where you bought the domain and what tld it is.

Basically you will create entries at the place where you bought the domain like this:

ns1.YOURDOMAIN.com   -->  [www.xxx.yyy.zzz](www.xxx.yyy.zzz)  (IP 1)
ns2.YOURDOMAIN.com   -->  aaa.bbb.ccc.ddd (IP 2)

If you follow that perfect HowTo guide, you will setup a complete system with nameservers. So you will then only require your domain there.

---

### Post by mraiur on 2008-04-17
Hi. 
I managed to configure the domein but how can i make subdomeins that uses different sites ... i mean i managed to make some but they where only visible from the server from the domein i can only see 1 no mather what sub-domein i type...
Can you give me some gidence.

---

