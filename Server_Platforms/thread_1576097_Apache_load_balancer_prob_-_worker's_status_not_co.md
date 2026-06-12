---
title: "Apache load balancer prob - worker's status not correctly identified"
date: 2010-09-16
forum: Server Platforms
---

### Post by derelict888 on 2010-09-16
I have several MTAs (CentOS 5.4, httpd-2.2.3-31.el5.centos) and a couple of web servers (CentOS 5.4, httpd-2.2.3-31.el5.centos.2, tomcat v 6.0.18.0). All web traffic is sent from the MTAs to the webservers using proxy pass like below (set on each of the MTAs);
 
```
<Proxy balancer://clickthrough>
   BalancerMember http://x.x.x.x:80      loadfactor=1 timeout=5
   BalancerMember http://x.x.x.y:80      loadfactor=1 timeout=5
   ProxySet lbmethod=bytraffic
</Proxy>
 
<VirtualHost *:80>
   ProxyPass /balancer-manager !
   ProxyPass /server-status !
   ProxyPass /instats/ !
   ProxyPreserveHost on
   ProxyPass / balancer://[location]/
   ProxyPassReverse / balancer://[location]/
```

After the web traffic is directed from the MTAs to the webservers, the webservers use mod_jk (I think) to grab the traffic and send it to tomcat.
 
Heres the problem, the sites are tomcat webapps and if the tomcat service is running but otherwise unresponsive the balancers do not pick this up. So traffic is still being sent to a webserver even if Tomcat is locked up (but says its still running). Heres my question, how do I get the balancer to be a bit more robust so it catches problems like this?
 
I'm fairly new to load balancing in apache but I was unable to find an answer from manuals and the internet - I'm sure the answer is out there I just don't know where to look  / what to ask. Any help on this or direction on where to look would be much appreciated, thanks.

---

### Post by LightningCrash on 2010-09-19
look up the ping option!

[http://httpd.apache.org/docs/current/mod/mod_proxy.html](http://httpd.apache.org/docs/current/mod/mod_proxy.html)
> Ping property tells webserver to send a CPING  request on ajp13 connection before forwarding a request. The parameter is the delay in seconds to wait for the CPONG reply. This features has been added to avoid problem with hung and busy Tomcat's and require ajp13 ping/pong support which has been implemented on Tomcat 3.3.2+, 4.1.28+ and 5.0.13+. This will increase the network traffic during the normal operation which could be an issue, but it will lower the traffic in case some of the cluster nodes are down or busy. Currently this has an effect only for AJP. By adding a postfix of ms the delay can be also set in milliseconds. 

---

### Post by derelict888 on 2010-09-20
> **LightningCrash said:**
> look up the ping option!

[http://httpd.apache.org/docs/current/mod/mod_proxy.html](http://httpd.apache.org/docs/current/mod/mod_proxy.html)

Thanks for the reply, I knew this thread was a bit of a long shot. Your answer does look promising I'll look into ty.

---

