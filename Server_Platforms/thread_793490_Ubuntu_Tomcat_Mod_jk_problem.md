---
title: "Ubuntu Tomcat Mod_jk problem"
date: 2008-05-13
forum: Server Platforms
---

### Post by Kismet on 2008-05-13
Hello,
   Currently our deployment is 1 Ubuntu 7.10 machine running Apache. And 2 Tomcat Nodes running on Centos 3.5. 

Everything WORKS FINE!!.

Now everything else on site has been migrated to Ubuntu, the DB, development machines, backup DB, etc.

So I'd like to upgrade the tomcat node to Ubuntu also. 

So I copy the JVM, the webapp, and tomcat directly over to a new Ubuntu 8.04/7.10 Machine. When I do that tomcat starts up and runs fine. I can connect directly to it via ip:8080. However when I add it to the workers list, it loses sessions. A user will log in, click around for awhile, and then it will fail, and roll them over to a Centos Node. 

Now when I have just 1 Ubuntu tomcat node running and Apache directing to it, it works. When I have more than 1 Ubuntu node, or Ubuntu/Centos Nodes, the Ubuntu node fails to keep sessions.

```
# workers.properties 
#

# In Unix, we use forward slashes:
ps=/

# list the workers by name

worker.list=loadbalancer
worker.maintain=10
# ------------------------
# First tomcat server
# ------------------------
worker.tomcat1.port=8009
worker.tomcat1.host=10.10.10.46
worker.tomcat1.type=ajp13

worker.tomcat1.socket_timeout=300  
worker.tomcat1.socket_keepalive=true
worker.tomcat1.connection_pool_size=50
worker.tomcat1.connection_pool_minsize=10
worker.tomcat1.connection_pool_timeout=600
worker.tomcat1.redirect=tomcat2



#
# Specifies the load balance factor when used with
# a load balancing worker.
# Note:
#  ----> lbfactor must be > 0
#  ----> Low lbfactor means less work done by the worker.
worker.tomcat1.lbfactor=1


# ------------------------
# Second tomcat server
# ------------------------

# This first rule means to inherit all non-overwritten properties from tomcat1
worker.tomcat2.reference=worker.tomcat1

worker.tomcat2.host=10.10.10.47
worker.tomcat2.redirect=tomcat1





# ------------------------
# Load Balancer worker
# ------------------------

#
# The loadbalancer (type lb) worker performs weighted round-robin
# load balancing with sticky_session sessions.
# Note:
#  ----> If a worker dies, the load balancer will check its state
#        once in a while. Until then all work is redirected to peer
#        worker.
worker.loadbalancer.type=lb
worker.loadbalancer.sticky_session=True
worker.loadbalancer.balance_workers=tomcat1,tomcat2
worker.loadbalancer.retries=10
#
# END workers.properties
#

```


There is the workers.properties.

Here is an excerpt from the mod_jk.log

```

[Tue May 13 17:52:11.608 2008] [8736:3059768208] [info] ajp_send_request::jk_ajp_common.c (1265): (tomcat1) all endpoints are disconnected
[Tue May 13 17:52:11.608 2008] [8736:3059768208] [info] ajp_service::jk_ajp_common.c (2085): (tomcat1) sending request to tomcat failed,  recoverable operation attempt=1

```

It's driving me nuts, I've been working on it for hours. :( 

If I can't find the problem, soon, I may have to switch back to Centos, as everything works fine with it.

---

### Post by Kismet on 2008-05-14
No ideas?

---

