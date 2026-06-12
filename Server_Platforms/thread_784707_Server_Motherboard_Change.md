---
title: "Server Motherboard Change"
date: 2008-05-06
forum: Server Platforms
---

### Post by jq6429 on 2008-05-06
Hi I'm very new to this Software and learning. One of my Servers Motherboards failed on me and I replaced the Motherboard and now when I load the ubuntu server up I can not get the Internet or Access to my fileserver. What direction should I go to troubleshooting this problem. I'm clueless I know that is why I'm asking this question. Any Help would be great!

---

### Post by dacool25 on 2008-05-07
I'd start with the basics.  Are you getting an IP Address?  Did your hostname change with the new NIC?

---

### Post by jq6429 on 2008-05-09
The only thing that I believe changed was the ip address because I'm using the intregated Nic card on the Motherboard. Is it possible it could have been Hard Coded. How and where do I check if it has been Hard Coded from the other Motherboard?

---

### Post by MJN on 2008-05-09
Post the output of **ifconfig -a** then we see where things stand with your networking.
 
Mathew

---

