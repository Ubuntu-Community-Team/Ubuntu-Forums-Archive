---
title: "Ubuntu Server 20.04.1 cloud-init, firewalld and &quot;Ordering cycle found&quot;"
date: 2020-08-14
forum: Server Platforms
---

### Post by rufus-ebonhawk on 2020-08-14
Hello we have found an issue on Ubuntu 20.4. with cloud-init and firewalld.

We provision new server with cloud-init autoinstall. After apt install firewalld an "Ordering cycle found" appears at boot time. See picture.

If we remove cloud-init everything is fine. If we remove firewalld everything is fine. Both together results in this systemd boot problem.

Does anyone has a glue what happens? 

[ATTACH=CONFIG]286702[/ATTACH]

---

### Post by rufus-ebonhawk on 2020-08-22
Hello :-) Really no one? Is it too unusal using firewalld with Ubuntu? We are forced to use Ubuntu, coming from CentOS.

---

### Post by LHammonds on 2020-08-22
I use Ubuntu Server and have been for years...but never utilize init.d nor firewalld so I have zero experience related to that.  Sorry.  Maybe someone else can help but don't expect a dozen quick responses since that "seems" like a very specific scenario.

Would you consider using ufw for managing firewall rules or iptables directly?   I use a bash script to manage my firewall rules.  [Example](https://hammondslegacy.com/forum/viewtopic.php?p=826#p826).

LHammonds

---

