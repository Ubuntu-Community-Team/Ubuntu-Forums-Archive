---
title: "Internet access control.."
date: 2006-02-06
forum: Server Platforms
---

### Post by bushtor on 2006-02-06
Hi,

In a high school dorm we have installed wireless networks providing Internet access for the students in their spare time.  However if they get too creative (hacking other's sites etc) we need a way to track down the offender.

We have other Ubuntu servers in our network so I hoped to use also one Ubuntu box  as proxy and internet access control / logger.  

What is the best solution to identify each computer or user in this scenario?

Logon before getting access to the internet or some kind of MAC address checking?

Thanks for comments and suggestions

regards

Tor

---

### Post by dudus on 2006-02-06
There was something like this at a company I worked. I wasn't involved on the project but they were running squid. I think the MAC addres checking is enough as it's more transparent and less boring.

---

