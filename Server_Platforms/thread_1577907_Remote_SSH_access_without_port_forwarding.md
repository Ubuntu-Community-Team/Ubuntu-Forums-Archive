---
title: "Remote SSH access without port forwarding"
date: 2010-09-19
forum: Server Platforms
---

### Post by dyous87 on 2010-09-19
My business rents an office in a building with shared Internet access. I don't have access to the main router and firewall but my company's network is a subnet on the main network. I am connecting a server that I will install Ubuntu on within my subnet. I want to use the server for file backups and sharing between my companies computers. I would also like to be able to remotely ssh into the server from home but since I do not have access to the main router I wanted to know if there is anyway at all that I would be able to ssh in without forwarding port 22 on the main router?

Any help would be greatly appreciated.

Best Regards,
David

---

### Post by windependence on 2010-09-19
Unless you run IPv6 you need NAT and thus port forwarding.
 
-Tim

---

### Post by dyous87 on 2010-09-19
Well my server will also have an ip6 address so how would I do it with ip6?

---

### Post by windependence on 2010-09-19
It's not that simple. To use the IPV6 address you will need a scope:global address and most likely the IPV6 address your machine assigned is a scope:link address or a scope:site address and can't be seen from the outside.
 
I am no IPV6 guru by far, the best I can suggest is start reading and see how to give your machine a global address so you can ssh to it through the firewall. Here are some places to start:
 
[http://www.enterprisenetworkingplanet.com/netsp/article.php/3634596/Getting-Around-IPv6.htm](http://www.enterprisenetworkingplanet.com/netsp/article.php/3634596/Getting-Around-IPv6.htm)
 
[http://www.zdnet.com/blog/btl/using-ipv6-watching-the-dancing-turtle/5166](http://www.zdnet.com/blog/btl/using-ipv6-watching-the-dancing-turtle/5166)
 
[http://www.networkworld.com/newsletters/lans/2010/042810-ipv6-tutorial.html](http://www.networkworld.com/newsletters/lans/2010/042810-ipv6-tutorial.html)
 
HTH
 
-Tim

---

### Post by dyous87 on 2010-09-19
windependence thanks for your help!I learned a great deal about how ipv6 works with those links. Sadly since by isp's don't support it yet it doesn't seem to be an option.

I actually found a solutions using reverse ssh tunneling.

Using the following command:

```
ssh -R 19999:localhost:22 sourceuser@source.com
```

I was able to bind ssh to a remote server. SSH'ing to the remote server I am then able to ssh into my office server.

Thanks again for your help!

David

---

