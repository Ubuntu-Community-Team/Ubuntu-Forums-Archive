---
title: "Server download alot of traffic"
date: 2007-06-05
forum: Server Platforms
---

### Post by ferrumhigh on 2007-06-05
Hi there I'm having a problem with my Ubuntu Proxy Server, It uses alot of bandwidth a day... more or less 500MB+. What can be the cause of this, and is there any way of checking what it uses the bandwidth for? Please tell me what can I do.:(

---

### Post by turinglabs on 2007-06-05
ntop or a web stats package like awstats might help you track down where your bandwidth is going. Ntop is nice in that it will show you real-time data. See [https://help.ubuntu.com/community/Ntop](https://help.ubuntu.com/community/Ntop).

---

### Post by ferrumhigh on 2007-06-06
Hi :pthere, thanx for the quick reply.
I'll give it a try! And I'll let you know if it works.

---

### Post by ferrumhigh on 2007-06-06
Can you please tell me where in the menu can I see exactly what I'm looking for. I see alot of traffic on the ethernet, where should I look to see what traffic is coming from where? Ex. Downloads and Uploads to my proxy server.
Thanx :D

---

### Post by turinglabs on 2007-06-06
I don't have ntop running right now, as I recall last I used it, it will show you traffic to or from individual hosts, but the interface takes a bit of getting used to.

---

