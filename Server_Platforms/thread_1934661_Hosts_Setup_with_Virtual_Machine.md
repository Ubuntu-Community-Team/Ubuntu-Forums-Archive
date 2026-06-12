---
title: "Hosts Setup with Virtual Machine"
date: 2012-03-02
forum: Server Platforms
---

### Post by the1joker on 2012-03-02
Here's my situation:
I run Ubuntu (latest version), apache2, PHP etc...  on a virtual machine in VM ware. This runs a NAT, or other internal network, now i am able to go to my primary website, which is findable by goign to its local ip in my Internet Explorer in my host machine (this is 192.168.142.3).

Now it worked for a minute, that i could go to [http://ubuntu/](http://ubuntu/) and get the same website, now i need that because i want to start running some subdomains... but as soon as i tried this my IE could find [http://ubuntu/](http://ubuntu/) anymore..
 
Can anyone help me out??
Here's my /etc/hosts file content:

127.0.0.1 localhost
127.0.0.1 hpm.localhost
127.0.0.1 hucon.localhost
127.0.0.1 hun.localhost
127.0.0.1 marios.localhost
127.0.0.1 rdf.localhost
127.0.0.1 sb.localhost
127.0.0.1 sc.localhost
127.0.0.1 mbs.localhost
127.0.0.1 rdff.localhost
127.0.1.1 ubuntu
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

