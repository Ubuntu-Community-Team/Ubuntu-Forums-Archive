---
title: "Two web servers, one external IP"
date: 2012-04-25
forum: Server Platforms
---

### Post by OliverHaslam on 2012-04-25
OK, background:

I have a host machine with two virtual machines running. My Ubuntu VM is my web host, running Apache etc and powering oliverhaslam.com.

I also have a VM running Windows Server 2008 R2 and Exchange 2010. This obviously has a web interface which is accessible from localhost/owa.

I now want that web-based Exchange interface to be accessible via oliverhaslam.com/owa but that obviously gets picked up by the web server that I have my domain pointing to, which is the Ubuntu VM.

So, the question is thus: how do I have one domain/external IP and have it point to two distinct virtual machines with two different internal IP addresses?

I presume this is possible using Virtual hosts, but I'm not sure. Alternatively I could migrate the entire web server duties to Windows, but I'd obviously rather not.

Cheers :)

---

### Post by haqking on 2012-04-25
> **OliverHaslam said:**
> OK, background:

I have a host machine with two virtual machines running. My Ubuntu VM is my web host, running Apache etc and powering oliverhaslam.com.

I also have a VM running Windows Server 2008 R2 and Exchange 2010. This obviously has a web interface which is accessible from localhost/owa.

I now want that web-based Exchange interface to be accessible via oliverhaslam.com/owa but that obviously gets picked up by the web server that I have my domain pointing to, which is the Ubuntu VM.

So, the question is thus: how do I have one domain/external IP and have it point to two distinct virtual machines with two different internal IP addresses?

I presume this is possible using Virtual hosts, but I'm not sure. Alternatively I could migrate the entire web server duties to Windows, but I'd obviously rather not.

Cheers :)

setup port forwarding on your router (that depends on your router)

And have one go to one IP and the other to other IP

Default web requests are on 80 obviously, and on other change port and then specify it in domain name such as:

domain.com:8080

Peace

---

### Post by OliverHaslam on 2012-04-25
> **haqking said:**
> setup port forwarding on your router (that depends on your router)

And have one go to one IP and the other to other IP

Default web requests are on 80 obviously, and on other change port and then specify it in domain name such as:

domain.com:8080

Peace

Cheers. There is that, but ideally I'd like to keep everything on port 80.

---

### Post by SeijiSensei on 2012-04-25
Can the virtual servers see each other?  If so, you could try using Apache's [mod_proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") to forward connections to /owa over to Exchange.

---

### Post by OliverHaslam on 2012-04-26
> **SeijiSensei said:**
> Can the virtual servers see each other?  If so, you could try using Apache's [mod_proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") to forward connections to /owa over to Exchange.

They can indeed, all the machines are basically acting as real machines when it comes to the network. Each has its own internal IP.

---

### Post by a2j on 2012-04-27
> **SeijiSensei said:**
> Can the virtual servers see each other?  If so, you could try using Apache's [mod_proxy]("http://httpd.apache.org/docs/2.2/mod/mod_proxy.html") to forward connections to /owa over to Exchange.

This. Also [pound]("http://www.apsis.ch/pound") could do it.

---

