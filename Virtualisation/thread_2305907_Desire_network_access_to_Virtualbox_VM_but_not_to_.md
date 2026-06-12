---
title: "Desire network access to Virtualbox VM but not to host"
date: 2015-12-10
forum: Virtualisation
---

### Post by sampsonats on 2015-12-10
I have an Ubuntu 14.04 VM running in Virtualbox on an Ubuntu host.

I'm using NAT for the VM.  Everything works fine but I want to _**turn off network access to the host**_ but allow access to the VM.

Is it possible to do this?

Thanks!

---

### Post by SeijiSensei on 2015-12-10
Yes.  Use "bridged" networking rather than NAT.  With this method the VM gets an IP in your local network and is directly visible.  Then you could disable access by adding an iptables rule to the host:
```

/sbin/iptables -P INPUT -j DROP

```
That rule would block all connections to the VM host.

---

### Post by sampsonats on 2015-12-10
Excellent!  I'm using UFW and am not familiar with iptables.  Would you happen to know if I can block the host's access to the network with UFW?

---

### Post by sampsonats on 2015-12-10
By the way, my host has another interface on the local network.  I'm afraid the '[COLOR=#000000][FONT=Ubuntu Mono]/sbin/iptables -P INPUT -j DROP' rule might break this second interface.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-12-10
As far as I know, UFW is simply a tool to create iptables rules.  I'll leave it to you to find the corresponding UFW syntax, or someone else here might chime in.  I write firewall rulesets from scratch with iptables.

If you don't want to deny all access, then you can use 
```
/sbin/iptables -A INPUT -i eth0 -j REJECT
```
to block traffic arriving on the eth0 interface.

---

### Post by sampsonats on 2015-12-10
Perfect!  Much appreciated!

---

### Post by SeijiSensei on 2015-12-10
I will mention one caveat.  This might not work since the VM presumably actually needs to use the host's interface to receive inbound traffic.  If you try this and find you cannot reach the VM, then maybe this rule will work better:
```
/sbin/iptables -A INPUT -d 10.10.10.10 -j REJECT
```
which blocks traffic to the 10.10.10.10 address rather than the entire interface.

---

