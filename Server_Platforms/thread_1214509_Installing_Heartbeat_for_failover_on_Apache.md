---
title: "Installing Heartbeat for failover on Apache"
date: 2009-07-16
forum: Server Platforms
---

### Post by muh_atta on 2009-07-16
Hello Gurus

I am looking for a step by step guide for installing and configuring heartbeat HA for Apache fail over on Ubuntu Server.

I have searched Google but no tutorial is guiding the reader to do this from scratch. 
What are pre-requisites for this task etc.

Please guide.

Thanks 
Atta ur rehman.

---

### Post by windependence on 2009-07-16
This is no small project. Heartbeat is enterprise class and it is assumed you have resources like 3 or 4 interfaces available.

You may want to check this out:

[http://www.keepalived.org/](http://www.keepalived.org/)

Also, using virtualization would be much easier to add failover as it is built in to most virtualization technologies.

-Tim

---

