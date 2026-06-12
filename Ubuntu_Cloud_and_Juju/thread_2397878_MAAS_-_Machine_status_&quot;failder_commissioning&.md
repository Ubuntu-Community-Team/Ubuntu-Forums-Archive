---
title: "MAAS - Machine status &quot;failder commissioning&quot;"
date: 2018-08-04
forum: Ubuntu Cloud and Juju
---

### Post by tello83 on 2018-08-04
Hi,
I have installed KVM and MAAS and I want deploy a machine but continue to get the status Failed commissioning.
I think the problem is the subnet configuration but I don't fine a clear error into log, do you have any idea to find that?
I have configured the subnet so
[LIST]
[*]Range my actual DHCP is 192.168.3.1/99
[*]Range reserved to MAAS is 192.168.3.100/150
[*]Bridge for virt 192.168.122.1/255
[/LIST]

The following actual configuration

**[SIZE=4]Page Subnets[/SIZE]**
[TABLE="class: u-no-margin--top, width: 1400"]
[TR]
[TH]Fabric[/TH]
[TH]VLAN[/TH]
[TH]DHCP[/TH]
[TH]Subnet[/TH]
[TH]Available IPs[/TH]
[TH]Space[/TH]
[/TR]
[TR="class: vs-repeat-before-content"]
[/TR]
[TR="class: vs-repeat-repeated-element ng-scope"]
[TD]fabric-0[/TD]
[TD]untagged[/TD]
[TD]Enabled[/TD]
[TD]192.168.3.0/24[/TD]
[TD="class: ng-binding"]41%[/TD]
[TD](undefined)[/TD]
[/TR]
[TR="class: vs-repeat-repeated-element ng-scope"]
[TD]fabric-1[/TD]
[TD]untagged[/TD]
[TD]Enabled[/TD]
[TD]192.168.122.0/24[/TD]
[TD="class: ng-binding"]74%[/TD]
[TD](undefined)[/TD]
[/TR]
[/TABLE]
**Fabric summary**
Name: fabric-0
Description:
Rack controllers node1,
[B][SIZE=4]
VLANs on this fabric[/SIZE][/B]

[TABLE="class: p-table--mobile-card p-table-expanding, width: 1400"]
[TR]
[TH="class: col-3"]VLAN[/TH]
[TH="class: col-5"]Subnet[/TH]
[TH="class: col-2"]Available[/TH]
[TH="class: col-2"]Space[/TH]
[/TR]
[TR="class: ng-scope"]
[TD="class: col-3"]untagged[/TD]
[TD="class: col-5"]192.168.3.0/24[/TD]
[TD="class: col-2 ng-binding"]41%[/TD]
[TD="class: col-2"](undefined)[/TD]
[/TR]
[/TABLE]


**Subnet summary**

Name 192.168.3.0/24
CIDR 192.168.3.0/24
Gateway IP 192.168.3.1
DNS 
Description network
Managed allocation Help: Disabled
Active discovery Disabled
Fabric fabric-0
VLAN untagged
Space (undefined) 

**[SIZE=4]Static Route[/SIZE]**
[TABLE="class: p-table-expanding, width: 1400"]
[TR]
[TH="class: col-3"]Gateway IP[/TH]
[TH="class: col-4"]Destination[/TH]
[TH="class: col-2"]Metric[/TH]
[TH="class: col-3"][RIGHT]Actions[/RIGHT]
[/TH]
[/TR]
[TR="class: ng-scope"]
[TD]No static routes have been added to this subnet.[/TD]
[/TR]
[/TABLE]

[SIZE=4]**Reserved**[/SIZE]

[TABLE="class: p-table-expanding, width: 1400"]
[TR]
[TH="class: col-2"]Start IP Address[/TH]
[TH="class: col-2"]End IP Address[/TH]
[TH="class: col-1"]Owner[/TH]
[TH="class: col-1"]Type[/TH]
[TH="class: col-3"]Comment[/TH]
[TH="class: col-3"]Actions[/TH]
[/TR]
[TR]
[TD="class: col-2 ng-binding"]192.168.3.1[/TD]
[TD="class: col-2 ng-binding"]192.168.3.99[/TD]
[TD="class: col-1 ng-binding"]maas[/TD]
[TD="class: col-1 ng-binding"]Reserved[/TD]
[TD="class: col-3 ng-binding"][/TD]
[TD="class: col-3"][RIGHT]*Edit** [I]Remove*[/I][/RIGHT]
[/TD]
[/TR]
[TR]
[TD="class: col-2 ng-binding"]192.168.3.100[/TD]
[TD="class: col-2 ng-binding"]192.168.3.150[/TD]
[TD="class: col-1 ng-binding"]MAAS[/TD]
[TD="class: col-1 ng-binding"]Dynamic[/TD]
[TD="class: col-3 ng-binding"]Dynamic[/TD]
[TD="class: col-3"][RIGHT]*[I]ve*[/I][/RIGHT]
[/TD]
[/TR]
[/TABLE]

**[SIZE=4]Machines[/SIZE]**
[TABLE="class: p-table--mobile-card p-table--sortable, width: 1038"]
[TR]
[TH="class: ng-scope"][/TH]
[TH="class: u-align--left, colspan: 2"]FQDN | MAC[/TH]
[TH]Power[/TH]
[TH][/TH]
[TH]Status[/TH]
[TH]Owner[/TH]
[TH="align: right"]Cores[/TH]
[TH="align: right"]RAM (GiB)[/TH]
[TH="align: right"]Disks[/TH]
[TH="align: right"]Storage (GB)[/TH]
[/TR]
[TR="class: vs-repeat-before-content"]
[/TR]
[TR]
[TD="class: ng-scope"][/TD]
[TD="class: u-align--left ng-scope, colspan: 2"]test.maas[/TD]
[TD="class: powerstate u-upper-case--first ng-binding"] on[/TD]
[TD="class: u-hide--small"][/TD]
[TD="class: status u-text--truncate ng-binding"]Commissioning[/TD]
[TD="class: ng-binding"] maas[/TD]
[TD="class: u-align--right u-hide--small p-tooltip p-tooltip--left ng-binding, align: right"]2[/TD]
[TD="class: u-align--right u-hide--small p-tooltip p-tooltip--left ng-binding, align: right"]2.0[/TD]
[TD="class: u-align--right u-hide--small p-tooltip p-tooltip--left ng-binding, align: right"] 1[/TD]
[TD="class: u-align--right u-hide--small ng-binding, align: right"]8.0[/TD]
[/TR]
[TR]
[TD="class: ng-scope"][/TD]
[TD="class: u-align--left ng-scope, colspan: 2"]ubuntuServer.maas[/TD]
[TD="class: powerstate u-upper-case--first ng-binding"] on[/TD]
[TD="class: u-hide--small"][/TD]
[TD="class: status u-text--truncate ng-binding"]Failed commissioning[/TD]
[TD="class: ng-binding"] maas[/TD]
[TD="class: u-align--right u-hide--small p-tooltip p-tooltip--left ng-binding, align: right"]2[/TD]
[TD="class: u-align--right u-hide--small p-tooltip p-tooltip--left ng-binding, align: right"]2.0[/TD]
[TD="class: u-align--right u-hide--small p-tooltip p-tooltip--left ng-binding, align: right"]1[/TD]
[TD="class: u-align--right u-hide--small ng-binding, align: right"]10.7[/TD]
[/TR]
[/TABLE]

Into event machine

[TABLE="class: ng-scope, width: 1400"]
[TR]
[TH="class: col-9"]Event[/TH]
[TH="class: col-3"]Time[/TH]
[/TR]
[TR]
[TD="class: col-9 ng-binding"]Failed to query node's BMC - (maas) - No rack controllers can access the BMC of node: ubuntuServer[/TD]
[TD="class: col-3 ng-binding"]Sat, 04 Aug. 2018 15:36:07[/TD]
[/TR]
[TR]
[TD="class: col-9 ng-binding"]Node changed status - From 'Commissioning' to 'Failed commissioning'[/TD]
[TD="class: col-3 ng-binding"]Sat, 04 Aug. 2018 15:35:47[/TD]
[/TR]
[TR]
[TD="class: col-9 ng-binding"]Marking node failed - Node operation 'Commissioning' timed out after 20 minutes.[/TD]
[TD="class: col-3 ng-binding"]Sat, 04 Aug. 2018 15:35:47[/TD]
[/TR]
[TR]
[TD="class: col-9 ng-binding"]Queried node's BMC - Power state queried: on[/TD]
[TD="class: col-3 ng-binding"]Sat, 04 Aug. 2018 15:22:25[/TD]
[/TR]
[/TABLE]

---

