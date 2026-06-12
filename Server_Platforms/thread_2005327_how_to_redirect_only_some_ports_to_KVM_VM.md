---
title: "how to redirect only some ports to KVM VM?"
date: 2012-06-17
forum: Server Platforms
---

### Post by Dwigatjel on 2012-06-17
Hello all.
I have a trouble trying to redirect only some of ports to VM.
Host is running some services, that need to be available and on VM there is a special service, so that I need to redirect ports 10040-10060 both TCP and UPD to that specyfied VM. I have a look at: [https://help.ubuntu.com/12.04/serverguide/network-configuration.html#bridging](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#bridging) but I dont want to allow full access to VM.
Bests, Dwigatjel
EDIT: SOLUTION:
> iptables -t nat -I PREROUTING -p tcp --dport 80 -j DNAT --to-destination 10.0.0.1:80
iptables -t nat -I PREROUTING -p tcp --dport 22 -j DNAT --to-destination 10.0.0.2:22
iptables -I FORWARD -m state -d 10.0.0.0/24 --state NEW,RELATED,ESTABLISHED -j ACCEPTI just add this to rc.local

---

