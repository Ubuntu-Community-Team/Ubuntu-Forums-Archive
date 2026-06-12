---
title: "UEC Accessing Mediawiki demo appliance"
date: 2010-04-17
forum: Server Platforms
---

### Post by Sivaa on 2010-04-17
Hi
     I have downloaded the Mediawiki demo appliance from UEC store.  I have installed it and also it is running.  
 
    I would like to know how to access the mediawiki demo appliance.  I tried accessing it as
 
  [http://<<public](http://<<public) ip address>>/mediawiki but is not accessible.  Please advise.
 
Cheers
Siva

---

### Post by wickwire on 2010-04-28
Hi there,

I'm also having trouble with this.

Running all of this inside my LAN, euca-describe-instances verbose shows the instance as "running", I'm using MODE=SYSTEM so it gets an internal IP address from my router, I can ping the IP address but when I try to access the MediaWiki - read somewhere to be http://<instance_ip_addr>/mediawiki - I can't even get a hint that an Apache is listening... Even http://<instance_ip_addr> won't go anywhere.

Have you managed to solve this?

---

### Post by wickwire on 2010-05-01
Hi,

got it work, finally!!

One of the harddrives started failing with bad sectors so I had to replace it, and while at it, the new ubuntu 10.04 came out!

Previous UEC installation was with 9.10, so decided to start from scratch.

the same 2 machines, one as the cluster, another as the node

With 10.04, similar installation process for the cluster, but then for the node, no user/password was asked - it used the credentials from the previously installed, already running cluster.

Also, the cluster configured the cloud's own DHCP management during installation, so I set it to use IPs from 192.168.88.200-192.168.88.220, outside my LAN router range.

Cluster and node up and running, went on to the store downloaded and installed the media wiki appliance demo, then logged onto the cluster and started an instance for it.

Once the instance had **running** status, took the IP registered to it **192.168.88.200**

(used euca-describe-instances to check the instance status)

and then tried to access the mediawiki on my laptop, 3rd machine in the LAN, but not registered in the cloud:

[http://192.168.88.200/mediawiki](http://192.168.88.200/mediawiki)

and it FAILED

went back to the cluster via ssh and:

euca-authorize default -P tcp -p 80 -s 0.0.0.0/0

then back to the laptop and Vista/Firefox and

[http://192.168.88.200/mediawiki](http://192.168.88.200/mediawiki) WORKED!

:D


Hope you haven't given up already and if still stuck, this may help you as well.

Next: bundling my own cloud images

---

