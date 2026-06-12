---
title: "can't ssh in"
date: 2009-05-02
forum: Security
---

### Post by stleric on 2009-05-02
I'm presently running 9.04 and am having trouble gaining access via ssh.  I installed ssh-server and changed/verified the config file to allow X11 forwarding, disallow root login and set UseDNS to 'no'.  I have not explicitly installed any security packages (firewalls,
IDS and the like).

There are two subnets associated with my department and I can access the ubuntu box from machines in either of those subnets.  However, I can't seem to access my machine from any other address such as subnets from other departments or (most importantly) from my home machine, which connects via DSL.  These failed connection attempts don't show up in auth.log.  I can see no reason why ubuntu should be allowing/denying access like this.

Here's the kicker, I replaced ubuntu with freebsd, I could then access the computer from anywhere, as I'd expect.  As near as I could tell, both OSes were set up the same wrt to sshd (sshd_conf, hosts.allow, hosts.deny).  This tells me that ubuntu is somehow restricting network access, that it's not happening elsewhere in the network infrastructure (and ubuntu is being kind of sneaky about it).

If anyone can tell me what's ubuntu doing, how do I make it stop or where I should look next I'd very much appreciate it.

TIA,
eric

---

### Post by The Cog on 2009-05-02
If you can connect to the machine from directly connected subnets, but not from remote (routed) networks, then maybe youer machine is missing a default route, or the default route is pointing on the wrong direction. Use the command route and see where its default route says its gateway is.

---

### Post by stleric on 2009-05-02
Just did it.  The gateway that's associated with the default destination is what I would expect it to be.  There are also two other destination entries, one says 'link-local' and the other looks like a super-net.

The other odd thing which I neglected to mention earlier is that if I'm at home or elsewhere, I can get to the ubuntu box indirectly via an intermediate machine.  Once I do that, I can then log in directly to the ubuntu box (even if I'm no longer logged in via the indirect path).  This effect seems to be temporary.

eric

---

### Post by The Cog on 2009-05-03
That sound very odd. It makes me think maybe it's an ARP issue, but I can't think how it might come about. My next move if I had the problem might be to use wireshark on the Ubuntu machine to see if I can see anything odd. See if the connect requests from home are even arriving at the Ubuntu machine.

---

### Post by stleric on 2009-05-03
Do you know whether or not the ubuntu developers built sshd with tighter security options than other garden variety ssh servers?

Also, do you know whether a default installation of ubuntu comes with some kind of firewall installed and activated?

This all pertains to 9.04 desktop/workstation distribution BTW.

Regards,
eric

---

### Post by cariboo on 2009-05-04
There is a firewall installed by default, but no rules are set by default. To check if some how some rules have been set, Open a terminal and type:

```
sudo iptables -L
```

you should get a result that looks like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

To create firewall rules, ufw is installed by default, or if you need or want a gui, gufw is in the repositories.

---

