---
title: "NIC Bonding issue....I think"
date: 2010-09-29
forum: Server Platforms
---

### Post by Solignis on 2010-09-29
Hi there I have recently gone back to Ubuntu Server 10.04.1 from Openfiler due to a long list of issues.

I loaded iscsi-target and ifenslave.

iscsi-target works great!

Where my problem lies is with the ifenslave and when I restart the networking services.

When I do /etc/init.d/networking restart

I get this output:

root@san01:/etc# /etc/init.d/networking restart
 * Reconfiguring network interfaces...
ssh stop/waiting
ssh start/running, process 1163
SIOCADDRT: No such process
Failed to bring up bond0.

But the odd thing is bond0 responds to a ping from a remote machine and the system says the interface is up.

Can someone give me some insight, I can provide any config files and required.

False alram!!

I removed the gateway line from the interfaces file and the error stopped showing.

---

