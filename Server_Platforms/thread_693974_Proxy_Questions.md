---
title: "Proxy Questions"
date: 2008-02-11
forum: Server Platforms
---

### Post by Holmes89 on 2008-02-11
Firstly I have Squid installed on my ubuntu server and had the proxy server working yesterday. Now it won't allow me to connect saying that the proxy is refusing access. I have http_access allow all set so I can connect from another building. I also have the port opened and routing to 3128 so it connects to my computer. So now today it won't allow me to connect at all. How do I fix that?

My second question is: Is there a way to log who accesses my proxy, what website they visited, essentially gathering as much information that I can so I can pinpoint who is using it?

My final question is how to I couple my proxy with a webpage to look like this: [http://www.youhide.com/](http://www.youhide.com/)

Any help would be appreciated. Thanks in advance.

---

### Post by k_grdn on 2008-02-11
Hi,

For monitoring activity check out SARG.

Have you checked the squid service/daemon is running?

ps -ef|grep squid

Run squid –k check to check for errors

Start the daemon in debug mode and check for errors.

Look for this line in squid.conf: 

acl MyNetworks src 

Place your network after src.

Regards,

k_grdn

---

### Post by Holmes89 on 2008-02-11
I get aclPArselpData: Netmask masks away part of the specified IP '192.168.0.1/24' what does that mean? Other than that nothing works still, it was very strange, it worked yesterday no problem.

---

