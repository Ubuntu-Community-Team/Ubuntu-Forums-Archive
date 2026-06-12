---
title: "Wordpress/Apache and ip adresses"
date: 2010-09-29
forum: Server Platforms
---

### Post by SRX84X on 2010-09-29
Hi

I recently set up a web server with wordpress, forwarded the ports and created a dynamic ip address so i can access the server from outside. However from outside when i click on one of the posts the site in the address bar changes from the dyndns address to the internal ip address ex. 192.168.*.*

Can someone help me figure out how to configure the Apache server so it doesn't redirect to the internal ip addresses. 


Thanks,

SR

---

### Post by CharlesA on 2010-09-29
Does wordpress ask for your domain name?

I know when I've installed forum software before that it asks for the domain name and will redirect you there instead of using the internal ip address.

---

### Post by SRX84X on 2010-09-29
> **CharlesA said:**
> Does wordpress ask for your domain name?

I know when I've installed forum software before that it asks for the domain name and will redirect you there instead of using the internal ip address.

Thanks for the replay, it turns out one of the settings was put to 192.168.*.* instead of the dns address, now it works. 

Thank you

---

