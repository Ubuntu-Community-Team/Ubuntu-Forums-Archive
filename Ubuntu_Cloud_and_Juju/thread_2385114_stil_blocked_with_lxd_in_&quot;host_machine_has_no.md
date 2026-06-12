---
title: "stil blocked with lxd in &quot;host machine has no available device in space(s)&quot;"
date: 2018-02-16
forum: Ubuntu Cloud and Juju
---

### Post by dbouwyn.thales on 2018-02-16
Hello,

I'm up (update/upgrade) on xenial

I'm trying to deploy a ceph-mon on infra1.maas with command
juju deploy --bind openstwork --to lxd:1 --config ceph-mon.yaml ceph-mon

It is still blocked and I really don't know/understand how to make it work !

the status show

App       Version  Status   Scale  Charm     Store       Rev  OS      Notes
ceph-mon           waiting    0/1  ceph-mon  jujucharms   20  ubuntu  


Unit        Workload  Agent       Machine  Public address  Ports  Message
ceph-mon/0  waiting   allocating  1/lxd/0                         waiting for machine


Machine  State    DNS             Inst id  Series  AZ         Message
0        started  X.X.X.X  capbwh   xenial  openstack  Deployed
1        started  192.168.13.4    qgfq33   xenial  openstack  Deployed
1/lxd/0  down                     pending  xenial             host machine "1" has no available device in space(s) "openstwork"



I had a machine infra1.maas with interfaces like

[COLOR=#111111][FONT=Ubuntu]eno1

Physical
fabric-1
untagged
192.168.13.0/24 (mngtsub)
192.168.13.4 (Auto assign)
[RIGHT]View actions[/RIGHT]


[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
enp1s0

Physical
fabric-3
untagged
192.168.14.0/24 (openstwork)
(Unconfigured)
[/FONT][/COLOR]







And a fabric like

**fabric-3**

Delete fabric

[COLOR=#111111][FONT=Ubuntu]**Fabric summary**

Edit
Namefabric-3DescriptionRack controllers[maasmaster]("http://192.168.12.67:5240/MAAS/#/node/controller/phsmc6")

**VLANs on this fabric**


[TABLE="width: 1440"]
[TR]
[TH="class: table__header table__column--15, align: left"]VLAN[/TH]
[TH="class: table__header table__column--50, align: left"]Subnet[/TH]
[TH="class: table__header table__column--10, align: left"]Available[/TH]
[TH="class: table__header table__column--25, align: left"]Space[/TH]
[/TR]
[TR="class: table__row table__row--no-hover ng-scope"]
[TD="class: table__column--15"][untagged]("http://192.168.12.67:5240/MAAS/#/vlan/5004")[/TD]
[TD="class: table__column--50"][192.168.14.0/24 (openstwork)]("http://192.168.12.67:5240/MAAS/#/subnet/13")[/TD]
[TD="class: table__column--10 ng-binding"]100%[/TD]
[TD="class: table__column--25"][openstwork]("http://192.168.12.67:5240/MAAS/#/space/5")[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]

---

### Post by acneteng on 2018-05-23
Did you create the space juju prior to the deploy.  juju add-space [COLOR=#111111][FONT=Ubuntu]openstwork 192.168.14.0/24.[/FONT][/COLOR]

---

