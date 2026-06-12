---
title: "Iptables, forward all traffic from interface to FW"
date: 2017-09-18
forum: Security
---

### Post by Drenriza on 2017-09-18
Hi all

**Context**
I have configured a physical server with XenServer 7 that runs CentOS.
In this setup i am running a virtual FW within the XenServer that is my firewall and router solution for all the VM's and the XenServer itself.

What i would like, is to connect the XenServer's eth1 interface directly to my WAN
and foward _all_ traffic received on eth1 from the XenServer to the FW01 VM so that this VM can handle _all_ security threads.

**The question**
The XenServer runs standard iptables, and i would like to make a rule that states the following
"all TCP & UDP traffic received on eth1, forward to 192.168.1.1"

As i am used to working with iptables through shorewall i am not quite sure how to format / write this rule directly in iptables,
and are hoping for some help with this.

I have looked a bit at the following links for inspiration, but can't quite figure it out.
Also my FW VM does all Network Address Translation required for clients, so i am also thinking that i dont need the MASQUERADE statement as shown below
in the XenServer iptables.
[https://gist.github.com/tzermias/5408466](https://gist.github.com/tzermias/5408466)
```

sudo iptables -A FORWARD --in-interface eth0 -j ACCEPT
sudo iptables --table nat -A POSTROUTING --out-interface wlan0 -j MASQUERADE

```

[https://serverfault.com/questions/846675/iptables-forward-all-traffic-to-remote-host](https://serverfault.com/questions/846675/iptables-forward-all-traffic-to-remote-host)
```

iptables -t nat -A PREROUTING -i br0 -s ! 192.168.0.2 -p tcp -j DNAT --to 192.168.0.2:1234
iptables -t nat -A POSTROUTING -j MASQUERADE

```

**Xtra**
Also if anyone has experience with creating such a solution in XenServer i would be VERY interested in hearing how you implemented this.

Thanks in advance to all!
Kind regards

---

### Post by Drenriza on 2017-09-18
So i've been playing around with the rules and made the following

```

-A INPUT -d public-IP/32 -p tcp -j ACCEPT
-A INPUT -d public-IP/32 -p udp -j ACCEPT

-A FORWARD -p tcp -j DNAT --to-destination 192.168.1.1
-A FORWARD -p udp -j DNAT --to-destination 192.168.1.1

```

Anyone with thoughts on these new rules in regard to what i am trying to archive?

---

