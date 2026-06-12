---
title: "DHCP - different IP on every boot"
date: 2006-01-04
forum: Server Platforms
---

### Post by solata15 on 2006-01-04
I have instaled server version but every time I reset my PC I get different IP from DHCP server. Other Win and Lnx systems work without problems.

Difference to default ubuntu install is dhclient3. I have removed package, but now even even network doesnt work...

Any ideas...

---

### Post by kingsidy on 2006-01-04
just a suggestion i do not whether it is relevant or not, but the assignment of ip depends on the lease time. a short lease time would mean that the ip gets changed frequently. I also have a server install but my ip does not change at all after everyboot.

---

### Post by harisund on 2006-01-04
what is your DHCP server? Is it a router? If it is a router, I suggest you go into the router settings and manually configure your server to always get the same ip. (static.) this way your server will still get its ip through dhcp, but the dhcp server will be handing out the same ip everytime. 

Hope I was clear. If not I will try a better explanation again. 
Hari

Oh and reinstall dhclient3. It is needed to get the ip from your router anyway. sudo apt-get install whatever you removed

---

### Post by solata15 on 2006-01-04
Unfortunately DHCP server shouldnt have manual IP. Our policy.
I'll reinstall dhclient3.
Can I set up IP manual on my PC (just for test)?

---

### Post by harisund on 2006-01-04
Hmm... you could set up the DHCP server to hand out just one static ip, to your server alone, and dynamic ip to all the other machines. But if that is strictly against your policy, I don't think I will be able to help you out there. 
You could set a fixed ip in your machine (the testing part) but I am not sure if it would work. Do give it a try though

---

### Post by kingsidy on 2006-01-04
you can set it up so that let's say it assigns new ip every  weeks

---

### Post by solata15 on 2006-01-04
How can I set IP manualy?
Why dhclient3-client package is not in default install and dhcp client works anyway?

---

### Post by solata15 on 2006-01-04
This is it.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=18148](https://bugzilla.ubuntu.com/show_bug.cgi?id=18148)

Can I fix it myself or MUST I wait for 6.* version of ubuntu?

---

