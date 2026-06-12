---
title: "filtering MAC address in ufw"
date: 2010-02-10
forum: Security
---

### Post by jpflorido on 2010-02-10
Dear list,
I've read that Ubuntu 9.10 allows to filter, not only IP addresses, but also MAC addresses through the UFW firewall.
I would like to allow access trough SSH only to a couple of MAC addresses, but don't know how to do it.
For IPs it is something like this:
sudo ufw allow from <ipaddress> to any port <port number>
But, I couldn't find any tips for MAC addresses.

Any suggestions?
Thanks,
Javier

---

### Post by Wiley_Linux on 2010-02-10
Hi jpflorido,

The only way that I know how to do it is using the iptables command. Try this command:

sudo iptables -A INPUT -p tcp --destination-port 22 -m mac --mac-source <Mac_address> -j ACCEPT

<Mac_address> = your Mac address.

Actually, iptables is the real firewall and ufw is only a interface to configure the iptables. I don't know if there is a way to do it using ufw, maybe other user knows it.

Good luck!

---

### Post by jpflorido on 2010-02-11
Thanks Wiley, I'll try with iptables,
Javier

---

