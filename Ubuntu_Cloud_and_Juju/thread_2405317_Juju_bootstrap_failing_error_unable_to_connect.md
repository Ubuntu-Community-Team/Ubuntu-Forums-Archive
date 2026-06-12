---
title: "Juju bootstrap failing: error unable to connect"
date: 2018-11-04
forum: Ubuntu Cloud and Juju
---

### Post by bryden2 on 2018-11-04
I've installed juju twice now on separate ubuntu desktop machines. I'm following the step-by-step instructions in the documentation here: [https://docs.jujucharms.com/2.4/en/tut-lxd](https://docs.jujucharms.com/2.4/en/tut-lxd)

In both cases I'm getting the following error:

```
juju bootstrap localhost lxd-test              130 &#8629;
ERROR Get [https://10.66.59.1:8443/1.0:](https://10.66.59.1:8443/1.0:) Unable to connect to: 10.66.59.1:8443
&#9581;&#9472;bryden@vallon ~/.local/share/juju                 
&#9584;&#9472;$ juju --version                                   1 &#8629;
2.4.4-bionic-amd64                                       
&#9581;&#9472;bryden@vallon ~/.local/share/juju                    
&#9584;&#9472;$ uname -a
Linux vallon 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
&#9581;&#9472;bryden@vallon ~/.local/share/juju                      
&#9584;&#9472;$ lxc network get lxdbr0 ipv4.address
                                                         
10.66.59.1/24                                            
&#9581;&#9472;bryden@vallon ~/.local/share/juju
&#9584;&#9472;$ lxc config show                                      
config: {}


```

---

### Post by du@dde on 2018-12-04
I had this same issue. The reason was that requests from the container to the host was blocked by a firewall. So try opening tpc/8443.

You can also test this by adding --keep-broken to your bootstrap command. This will leave a container running. Enter the container by running "lxc exec juju-<someting> -- /bin/bash". From there, you can do a "curl -k https://10.66.59.1:8443" to the host. At first it fails, but after opening the port it should succeed. When that request is successful, your juju bootstrap should work as well.

---

