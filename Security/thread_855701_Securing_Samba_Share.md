---
title: "Securing Samba Share"
date: 2008-07-10
forum: Security
---

### Post by Locutus_of_Borg on 2008-07-10
I just yesterday set up Windows XP in vmware-server, got it connected to the internet, and installed and configured samba to share files between the host and guest.

In order to connect from the XP guest to the Linux host, I needed to first stop iptables. Now I have iptables back on and nothing can connect. I believe I can just add ports 445/tcp, 139/tcp, 137/udp, and 138/udp to allow for the INPUT chain, but I was wondering if there is anything else I can do to ensure that only the vmware OS can access the Samba share.  The IP's are received through dhcp.  I use NAT to connect the two.  Is there anything else I can add to accomplish this?

I don't want even the possibility of anything else being able to connect through Samba to me.

Thanks.

---

### Post by Locutus_of_Borg on 2008-07-10
Even with those ports allowed, I still cannot connect.

What do I need to allow to let XP guest connect to Samba share on Linux?

Thanks.

---

### Post by k_grdn on 2008-07-11
Hi,

Turn off iptables

Monitor conversation with tcpdump or wireshark

Analise dumps and open corresponding port range for only the subnet of the connecting host, make sure you allow traffic on both input & output chains or use connection tracking.

Securing Samba

No shared passwords (share level security)
Control connecting hosts
listen only on protected interface
Implement tcpd wrappers
Firewall

Regards,

K_grdn

---

### Post by hyper_ch on 2008-07-11
install openssh and use scp/sftp to connect to the host or guest

---

