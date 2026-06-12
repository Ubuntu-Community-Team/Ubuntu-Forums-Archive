---
title: "SAMBA4 as Domain Controller on VPS"
date: 2015-11-24
forum: Ubuntu Cloud and Juju
---

### Post by marco122 on 2015-11-24
Hi everybody i hope is the right section because there are a lot of it.

i present my problem,

i had configured a Ubuntu Server on a VPS on it i configured samba4 as Domain Controller but i can't add a client(Es Windows) on the domain because i can't reach it.
i had configured the IPV4 setting like this

IP,SUBNET,GW DHCP
DNS the public IP of my VPS

when i try to ping the domain like domain.local it resolve like 192.168.1.100(the internal ip of my vps) but the request gone timed out i think there is a problem with DNS but i can't find any solution.

I hope sombody could help me
Thanks for the time

Greetings Mark

---

### Post by Elizine on 2015-11-27
Here's a link that will help you to add client (Es Windows) on the domain - [https://wiki.samba.org/index.php/Joining_a_Windows_client_to_a_domain](https://wiki.samba.org/index.php/Joining_a_Windows_client_to_a_domain)

---

