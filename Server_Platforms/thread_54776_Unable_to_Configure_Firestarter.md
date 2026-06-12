---
title: "Unable to Configure Firestarter"
date: 2005-08-06
forum: Server Platforms
---

### Post by suma on 2005-08-06
Hey there...

I am having trouble configuring Firestarter. So far, I have:

- set outbound traffic to permissive by default  (will have to change this later)
- allowed the DNS service for inbound traffic
- allowed the HTTP service for inbound traffic
- allowed the HTTPS service for inbound traffic

When I apply these rules and start the firewall, I am unable to use my browser.



One other point I'd like some clarification on.... by allowing DNS service for inbound traffic, does that mean:

1) DNS servers can reply to my requests.
2) Anybody on the net can make DNS requests to my computer.
3) Both above options.



Any suggestions would be greatly appreciated,
Suma

---

### Post by suma on 2005-08-06
problem solved - it turns out i needed to enable broadcasts from external network.... it's disabled by default.

also is regards to the other question i asked, i found the answer by testing out different rules.

it turns out that if you add http to the list of incoming services allowed you are letting other people access your computer on port 80. the way to enable http is to allow it in the outgoing services list.

---

