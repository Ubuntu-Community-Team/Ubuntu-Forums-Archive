---
title: "MaaS Region Controller with 2 Cluster Controller"
date: 2014-06-19
forum: Ubuntu Cloud and Juju
---

### Post by riccardo-magrini on 2014-06-19
[COLOR=#333333][FONT=UbuntuRegular]I'd like to realize an infrastructure like this:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]KVM as Hypervisor and 3 VM:[/FONT][/COLOR]

[LIST]
[*]1 VM for Region Controller (RC)
[*]2 VM for Cluster Controller(CC), each one with 2 or more nodes installed
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]Each VM use different Virtual Network 2.2.2.0/24 (RC),3.3.3.0/24(CC) 'n 4.4.4.0/24(CC) configured on virsh-manager[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Why the Region Controller added only one node and the second one no? Both VMs are identical...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I reported the pserv.log[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://paste.ubuntu.com/7668969/](http://paste.ubuntu.com/7668969/)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]thanks a lot[/FONT][/COLOR]

---

