---
title: "Setting up Bind"
date: 2006-10-16
forum: Server Platforms
---

### Post by hosttosucceed on 2006-10-16
I have set up Bind 9 with webmin for hosttosucceed.com using nameservers ns1 and ns2.hosttosucceed.com respectively.  I wish to host a domain called bodyshop.com(example) I registered this with dotster.com and the only option they gave me were setting up the nameservers, so i set them up to ns1.hosttosucceed.com and ns2.hosttosucceed.com.  Now im not sure how to configure bind for bodyshop.com, do i make a master zone or a slave zone for it and set the a address [www.bodyshop.com](www.bodyshop.com) and set that to my ns1.hosttosucceed's IP address?  hosttosucceed.com works, but im not sure how to host other domains using its nameservers

Heres another anaology: anyone know a good tutorial or can explain setting up bind with a domain name and then having that domain name, nameservers, be the nameservers of another domain example hosttosucceed.com ->ns->ns1.hosttosucceed.com, ns2.hosttosucceed.com  bodyshop.com->ns->ns1.hosttosucceed.com,ns2.hosttosucceed.com, how would i go about getting that setup on bind

---

