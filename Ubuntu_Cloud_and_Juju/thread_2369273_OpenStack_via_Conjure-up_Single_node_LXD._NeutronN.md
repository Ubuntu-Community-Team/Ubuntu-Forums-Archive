---
title: "OpenStack via Conjure-up Single node LXD. Neutron/Networking confusion."
date: 2017-08-21
forum: Ubuntu Cloud and Juju
---

### Post by sirtcp on 2017-08-21
Hi. 

Actually i am confuse a bit with neutron settings. i can not understand how it is working. how can i access the the lxd instances that i am creating inside the nova compute. i mean through outside world. 
when i see the horizon status i can see the IPs attached to the instances. please see the below details. 10.3.3.5 and 10.99.0.14


[TABLE="class: table table-striped datatable tablesorter tablesorter-default, width: 1190"]
[TR="class: table_column_header tablesorter-headerRow"]
[TH="class: sortable anchor normal_column tablesorter-header, align: left"]Instance Name
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]Image Name
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]IP Address
[/TH]
[TH="class: normal_column tablesorter-header sorter-false, align: left"]Size
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]Key Pair
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]Status
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]Availability Zone
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]Task
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]Power State
[/TH]
[TH="class: sortable normal_column tablesorter-header, align: left"]Time since created
[/TH]
[TH="class: actions_column tablesorter-header sorter-false, align: left"]Actions
[/TH]
[/TR]
[TR="class: ajax-update status_up odd"]
[TD="class: multi_select_column, bgcolor: #F9F9F9, align: center"]
[/TD]
[TD="class: sortable anchor normal_column, bgcolor: #F9F9F9"]fit1[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]trusty-lxd[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]
[LIST]
[*]10.3.3.5
[/LIST]
[/TD]
[TD="class: normal_column, bgcolor: #F9F9F9"][m1.tiny]("https://10.24.166.69/horizon/project/instances/#")[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]office-pc-ykhan[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]Active[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]nova[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]None[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]Running[/TD]
[TD="class: sortable normal_column, bgcolor: #F9F9F9"]2 days, 19 hours[/TD]
[TD="class: actions_column, bgcolor: #F9F9F9"][Create Snapshot]("https://10.24.166.69/horizon/project/images/7f226e1c-b652-47ce-88a1-e51a0f59b1d4/create/")[[FONT=FontAwesome][/FONT]]("https://10.24.166.69/horizon/project/instances/#")
[/TD]
[/TR]
[TR="class: ajax-update status_up even"]
[TD="class: multi_select_column, bgcolor: inherit, align: center"]
[/TD]
[TD="class: sortable anchor normal_column, bgcolor: inherit"][fitness]("https://10.24.166.69/horizon/project/instances/b6e83ff4-f738-41a3-9cb4-75cd8b70383b/")[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]xenial-lxd[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]
[LIST]
[*]10.99.0.14
[/LIST]
[/TD]
[TD="class: normal_column, bgcolor: inherit"][m1.tiny]("https://10.24.166.69/horizon/project/instances/#")[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]office-pc-ykhan[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]Active[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]nova[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]None[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]Running[/TD]
[TD="class: sortable normal_column, bgcolor: inherit"]4 days, 17 hours[/TD]
[TD="class: actions_column, bgcolor: inherit"][Create Snapshot]("https://10.24.166.69/horizon/project/images/b6e83ff4-f738-41a3-9cb4-75cd8b70383b/create/")[[FONT=FontAwesome][/FONT]]("https://10.24.166.69/horizon/project/instances/#")
[/TD]
[/TR]
[TR]
[TD="colspan: 12"]Displaying 2 items[/TD]
[/TR]
[/TABLE]

However when list  at nova compute "lxd list" there is no IP address assigned to any of the instances. nor i can ping the above IPs through any node. such as nova compute , neutron and juju bootstrap node. 
 

+-------------------+---------+------------------+------+------------+-----------+
|       NAME        |  STATE  |       IPV4       | IPV6 |    TYPE    | SNAPSHOTS |
+-------------------+---------+------------------+------+------------+-----------+
| instance-00000001 | RUNNING |                  |      | PERSISTENT | 0         |
+-------------------+---------+------------------+------+------------+-----------+
| instance-00000002 | RUNNING |                  |      | PERSISTENT | 0         |
+-------------------+---------+------------------+------+------------+-----------+

Actually i have 5 nodes available in production and i want to deploy openstack in customize and not via conjure-up autopilot and for i have installed single node lxd openstack for testing. however the confusing part is neutron or networking components.

i can not access any of the horizon displayed IPs from outside work, even when i ifconfig on neutron and Juju bootstrap node i can not see any similar IP assigned to the instances in horizon status. nor in nova-compute instances. can you guys please make it easy for me to understand what is going on. 

and how can i assign public or private IP separately to the instances.

Thanks,
MYK

---

