---
title: "iptable installation"
date: 2009-08-24
forum: Security
---

### Post by Shawn_K370037 on 2009-08-24
Do I need to install iptable firewall from the command line? Where should the archive be located in the usr directory? should it be in the root directory? Should I unpack it and designate a folder and remember the pathway to it or leave it unpacked? Do I use the apt utility or the dpkg one? By the way, I am not intimidated by the root usr because I am not some rookie at this either so if that works better please let me know.

---

### Post by cariboo on 2009-08-24
Iptables is installed by default. To administer it, I would suggest using gufw, it is in the repositories. If you want to check what rules have been setup, open a terminal and type:

```
sudo iptables -L
```

The default setup should look something like this:

```
hain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

