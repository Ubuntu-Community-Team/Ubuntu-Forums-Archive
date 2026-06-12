---
title: "Postfix Address Rewriting"
date: 2010-03-15
forum: Server Platforms
---

### Post by scroome on 2010-03-15
Hi, 

We currently use sendmail and it rewrites incoming mail addresses so 
that mail to 


<first>.<last>@domain.com is delivered to mailserver1.domain 
<anycombination>@domain.com is delivered to mailserver2.domain 


Does anyone know how this can be done in postfix ? 


TIA

---

### Post by KB1JWQ on 2010-03-15
transport_maps can do it; man 5 transport for more information on this.

---

