---
title: "Couldn't load balancing by mod-jk"
date: 2012-03-27
forum: Server Platforms
---

### Post by boypopping on 2012-03-27
hello

I have connect APACHE with 2 TOMCAT by mod-jk.
but I have a mistake

I did follow the instruction [http://blogs.encodo.ch/news/view_article.php?id=18](http://blogs.encodo.ch/news/view_article.php?id=18)
and when i restart APACHE, the problem occur:
[IMG]http://i217.photobucket.com/albums/cc238/boy_popping/111.png[/IMG]
I checked file httpd.conf, line 2 is:
```
JkWorkersFile /etc/apache2/workers.properties
```

there are not mistake, i confirmed.
and i thought it had error at "worker.properties"

and worker.properties

> workers.tomcat_home=/usr/share/apache-tomcat-6.0.35
workers.java_home=/usr/lib/jvm/java-6-sun
ps=/

worker.list=loadbalancer,status
worker.worker1.port=8009
worker.worker1.host=worker1
worker.worker1.type=ajp13
worker.worker1.lbfactor=1

#setup node2
worker.worker2.port=8009
worker.worker2.host=worker2
worker.worker2.type=ajp13
worker.worker2.lbfactor=1

#setup the load-balancer
worker.loadbalancer.type=lb
worker.loadbalancer.balance_workers=worker1,worker2
worker.loadbalancer.sticky_session=True
#worker.loadbalancer.sticky_session_force=True

# Status worker for managing load balancer
worker.status.type=status

I don't know where is mistake....Plz help me...
plz direction me config load balancing between 2 TOMCAT with 1 APACHE succesful.

I need load balancing for when one TOMCAT die, APACHE direct other TOMCAT replace.

---

### Post by boypopping on 2012-03-27
```
annt@ubuntu:~$ tail -f /var/log/apache2/mod_jk.log 
[Tue Mar 27 19:56:36 2012] [8923:3458201408] [info] service::jk_lb_worker.c (1453): All tomcat instances failed, no more workers left (attempt=1, retry=1)
[Tue Mar 27 19:56:36 2012] [8923:3458201408] [info] service::jk_lb_worker.c (1464): All tomcat instances are busy or in error state
[Tue Mar 27 19:56:36 2012] [8923:3458201408] [error] service::jk_lb_worker.c (1469): All tomcat instances failed, no more workers left
[Tue Mar 27 19:56:36 2012] [8923:3458201408] [info] jk_handler::mod_jk.c (2615): Service error=0 for worker=loadbalancer
[Tue Mar 27 20:00:24 2012] [8975:36509504] [info] init_jk::mod_jk.c (3183): mod_jk/1.2.28 initialized
[Tue Mar 27 20:00:24 2012] [8975:36509504] [error] uri_worker_map_ext::jk_uri_worker_map.c (506): Could not find worker with name 'jk-manager' in uri map post processing.
[Tue Mar 27 20:00:24 2012] [8975:36509504] [error] uri_worker_map_ext::jk_uri_worker_map.c (506): Could not find worker with name 'jk-status' in uri map post processing.
[Tue Mar 27 20:00:24 2012] [8976:36509504] [info] init_jk::mod_jk.c (3183): mod_jk/1.2.28 initialized
[Tue Mar 27 20:00:24 2012] [8976:36509504] [error] uri_worker_map_ext::jk_uri_worker_map.c (506): Could not find worker with name 'jk-manager' in uri map post processing.
[Tue Mar 27 20:00:24 2012] [8976:36509504] [error] uri_worker_map_ext::jk_uri_worker_map.c (506): Could not find worker with name 'jk-status' in uri map post processing.
```

this is file log mod_jk

plz...help  me

---

### Post by hawkmage on 2012-03-27
I use mod_proxy_ajp.  It is much easier to configure.

Using something like this:
```
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so

<Location /> 
    ProxyPass balancer://tomcat/ stickysession=JSESSIONID 
</Location>

<Proxy balancer://tomcat> 
   BalancerMember ajp://server1:9050 route=managed1 smax=5 max=20 ttl=120 retry=300
   BalancerMember ajp://server2:9050 route=managed2 smax=5 max=20 ttl=120 retry=300
   BalancerMember ajp://server3:9050 route=managed3 smax=5 max=20 ttl=120 retry=300
</Proxy> 
```

---

### Post by boypopping on 2012-03-29
> I use mod_proxy_ajp.  It is much easier to configure.

Using something like this:
 	Code:
 	LoadModule proxy_module modules/mod_proxy.so LoadModule proxy_ajp_module modules/mod_proxy_ajp.so LoadModule proxy_balancer_module modules/mod_proxy_balancer.so  <Location />      ProxyPass balancer://tomcat/ stickysession=JSESSIONID  </Location>  <Proxy balancer://tomcat>     BalancerMember ajp://server1:9050 route=managed1 smax=5 max=20 ttl=120 retry=300    BalancerMember ajp://server2:9050 route=managed2 smax=5 max=20 ttl=120 retry=300    BalancerMember ajp://server3:9050 route=managed3 smax=5 max=20 ttl=120 retry=300 </Proxy>


Hello
I solved this problem, just uncomment this line
JkWorkersFile /etc/apache2/workers.properties
everything run ok ^^

---

