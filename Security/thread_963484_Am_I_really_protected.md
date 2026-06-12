---
title: "Am I really protected?"
date: 2008-10-30
forum: Security
---

### Post by the8thstar on 2008-10-30
I have gufw enabled, which means that ufw is telling iptables to block any incoming connections. Good.

Now, is there a way to see the traffic by IPs on the computer? like GUI or command line? 

Also, in order to access the Internet, I'm going through another computer running XP (connection is made with an ethernet cable). Am I still protected?

Thanks!

---

### Post by lovinglinux on 2008-10-30
> **the8thstar said:**
> Now, is there a way to see the traffic by IPs on the computer? like GUI or command line? 

Try IPTState.

installation

```
sudo apt-get install iptstate
```

running the program

```
sudo iptstate
```

> **the8thstar said:**
> Also, in order to access the Internet, I'm going through another computer running XP (connection is made with an ethernet cable). Am I still protected?

Yes you are. The firewall will block any incoming connections to your machine if you have selected the deny policy.

---

