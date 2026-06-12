---
title: "cloud init &amp; vlan"
date: 2017-02-03
forum: Ubuntu Cloud and Juju
---

### Post by Greem84 on 2017-02-03
[FONT=arial][SIZE=2]Hi,

Using cloud init, I want to bring up a vlan (sub-interface on my VM) but the during the boot process the "vlan-raw-device" parameter is not save into /etc/network/interfaces.d/50-cloud-init.cfg.](*,)

Note that, I can bring up the interface manually using "[COLOR=#454545]vconfig add ens3 203[/COLOR] && [COLOR=#454545]ip link set up ens3.203" once the instance is booted but I would like to make it persistent.[/COLOR][COLOR=#454545]
[/COLOR]
Do you have any solution?


======================

Here is the content of "meta-data":

[/SIZE][/FONT][FONT=arial][SIZE=2]instance-id: vm1[/SIZE][/FONT]
[FONT=arial][SIZE=2]local-hostname: vm1[/SIZE][/FONT]
[FONT=arial][SIZE=2]runcmd:[/SIZE][/FONT]
[FONT=arial][SIZE=2] - [ modprobe, 8021q ][/SIZE][/FONT]
[FONT=arial][SIZE=2]network-interfaces: |[/SIZE][/FONT]
[FONT=arial][SIZE=2]  #[/SIZE][/FONT]
[FONT=arial][SIZE=2]  auto ens3[/SIZE][/FONT]
[FONT=arial][SIZE=2]  iface ens3 inet manual[/SIZE][/FONT]
[FONT=arial][SIZE=2]  #[/SIZE][/FONT]
[FONT=arial][SIZE=2]  #[/SIZE][/FONT]
[FONT=arial][SIZE=2]  auto ens3.203[/SIZE][/FONT]
[FONT=arial][SIZE=2]  iface ens3.203 inet dhcp[/SIZE][/FONT]
[FONT=arial][SIZE=2]  vlan-raw-device ens3
  #
  #

======================

Here is the content of "/etc/network/interfaces.d/50-cloud-init.cfg" once the instance is booted:

[/SIZE][/FONT][FONT=arial][SIZE=2]jonathan@ubuntu-jo2:~$ cat /etc/network/interfaces.d/50-cloud-init.cfg[/SIZE][/FONT]
[FONT=arial][SIZE=2]# This file is generated from information provided by[/SIZE][/FONT]
[FONT=arial][SIZE=2]# the datasource.  Changes to it will not persist across an instance.[/SIZE][/FONT]
[FONT=arial][SIZE=2]# To disable cloud-init's network configuration capabilities, write a file[/SIZE][/FONT]
[FONT=arial][SIZE=2]# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:[/SIZE][/FONT]
[FONT=arial][SIZE=2]# network: {config: disabled}[/SIZE][/FONT]
[FONT=arial][SIZE=2]auto lo[/SIZE][/FONT]
[FONT=arial][SIZE=2]iface lo inet loopback[/SIZE][/FONT]
[FONT=arial][SIZE=2]
[/SIZE][/FONT]
[FONT=arial][SIZE=2]auto ens3[/SIZE][/FONT]
[FONT=arial][SIZE=2]iface ens3 inet manual[/SIZE][/FONT]
[FONT=arial][SIZE=2]
[/SIZE][/FONT]
[FONT=arial][SIZE=2]auto ens3.203[/SIZE][/FONT]
[FONT=arial][SIZE=2]iface ens3.203 inet dhcp

======================


Thanks

[/SIZE][/FONT]

---

