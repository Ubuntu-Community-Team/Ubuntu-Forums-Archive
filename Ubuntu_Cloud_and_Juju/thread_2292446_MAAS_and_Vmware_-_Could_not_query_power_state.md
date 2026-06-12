---
title: "MAAS and Vmware - Could not query power state"
date: 2015-08-28
forum: Ubuntu Cloud and Juju
---

### Post by przemyslaw.trzeciak on 2015-08-28
Hello everyone, this is my first post on this formum:P

I installed the current version of MAAS (MAAS Version 1.8.0 + bzr4001-0ubuntu2) with python-pyvmomi on Ubuntu 14.04.
However, I have a problem with commissioning a VMware Virtual machine in the MAAS server and I cannot determine the power status of virtual machines.
When I add the chassis in the MAAS server and declare the power type as VMWare, in addition to the address information and log in I get the following information in the log (maas.log):

maas.power: [ERROR] XXX: Could not query the power state: vmware failed with return code 1: # 012 [Errno 2] No such file or directory ": //'192.168.1.88 ': // sdk / vimServiceVersions. xml ".

I checked that VMware delivers to that address the required version information:
[https://192.168.1.88/sdk/vimServiceVersions.xml](https://192.168.1.88/sdk/vimServiceVersions.xml)

<! -
    Copyright 2008-2012 VMware, Inc. All rights reserved.
->
.
.

Any ideas how to make the MAAS server read the correct information about the VMware version?

---

### Post by przemyslaw.trzeciak on 2015-09-14
Hi,
I solved this problem.
Problem was in two spaces:

1. I have inserted the wrong information of connection with VMware. It should look like this:
Add Chassis ->
Power type: VMware -> 
Host: FQDN ->
Username: user@domain ->
Password: xxx.

2.Vmware and place machine in catalogue. In our environment, machines are stored in directories. MAAS can not read inside directories and can get to the machines in the main tree.

Regards.

---

### Post by hpcre1 on 2015-12-29
Hello,

I did not understand the second issue you explained. how to put a VM in catalogue in VMware ?

---

