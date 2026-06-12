---
title: "(OpenStack) Bootstrapping Juju onto machine .. Unlimited loading"
date: 2023-06-29
forum: Ubuntu Cloud and Juju
---

### Post by korea1 on 2023-06-29
[COLOR=#000000][FONT=&quot]https://microstack.run/docs/single-node
[https://ubuntu.com/tutorials/install-openstack-on-your-workstation-and-launch-your-first-instance#2-install-openstack](https://ubuntu.com/tutorials/install-openstack-on-your-workstation-and-launch-your-first-instance#2-install-openstack)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Running the 'sunbeam cluster bootstrap --accept-defaults' mentioned in the single-node quickstart post results in infinite loading.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]It runs fine on Ubuntu Server 22.04, but the problem only occurs on Ubuntu 22.04 Desktop. Installing the Desktop environment on Ubuntu Server 22.04 causes the same symptoms as Ubuntu 22.04 Desktop.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]'DEBUG Running command /snap/openstack/201/juju/bin/juju bootstrap sunbeam sunbeam-controller juju.py:288' is still loading when debugging with the 'sunbeam -v cluster bootstrap --accept-defaults' -v flag.[/FONT][/COLOR]

---

