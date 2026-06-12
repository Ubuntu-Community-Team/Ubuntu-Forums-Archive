---
title: "got Apache2 to work!!!"
date: 2011-05-25
forum: Server Platforms
---

### Post by us11csalyer on 2011-05-25
I can see my website from any computer. (laptop using mcdonalds internet, in-laws internet, ect)
I gave up on the bind9 since I'm a complete noob. Here is my only problem.

I registered [www.mywebsite.com](www.mywebsite.com) on godaddy.com

How do I direct [www.mywebsite.com](www.mywebsite.com) to apache2 on my pc?

---

### Post by volkswagner on 2011-05-25
At godaddy.com login to your control panel > manage domains > pick your domain > edit dns entry and point your a record to your ip address (external ip from your isp).  This will work until your ip address changes (for dynamic address). 

If your isp provides a static ip, you are all set.  If your isp provides a dynamic ip, you will need a dynamic service such as no-ip, dynDns or similar.

---

### Post by us11csalyer on 2011-05-25
My IP is dynamic but the funny thing about it is I had the same IP for as long as I can remember. The last time it changed was when I upgraded my service to 30d/5u

I think I may have kept the ip for so long because my computer runs 24/7.

---

