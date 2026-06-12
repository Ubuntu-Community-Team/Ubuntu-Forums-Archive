---
title: "How do I test whether network-script is running or not in Xen Dom0."
date: 2010-04-10
forum: Virtualisation
---

### Post by tapas_mishra on 2010-04-10
How do I test whether network-script is running or not in Xen Dom0.
 I have a Debian Lenny Dom0.Running Xen on it and 4 virtual hosts on it.
I am currently setting up a proxy server in Dom0 which DomU's will be able to use.The problem is before I go on to set NAT I wanted to test bridges.

 So I renamed the bridge in /etc/xen/xend-config.sxp 
```

(network-script 'network-bridge bridge=ABCD')

```
 but when I do a reboot or xend restart and do following

 ```

qqeq:/etc/xen# brctl show
bridge name    bridge id        STP enabled    interfaces
eth2        8000.0026b9824238    no        peth2
                            vif1.0
                            vif2.0
                            vif3.0
                            vif4.0
qqeq:/etc/xen# 

 
``` the bridge is not renamed to ABCD above output is showing eth2 which is not even default.
So I doubt that the script network-bridge has not been called so that it renames the bridge or there is some thing else I should look for.

---

