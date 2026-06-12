---
title: "Error: No registration token found in the Cluster database"
date: 2023-11-27
forum: Ubuntu Cloud and Juju
---

### Post by saschac-dev on 2023-11-27
After following the tutorial of the openstack install [https://ubuntu.com/openstack/install](https://ubuntu.com/openstack/install) I see myself now confronted with the problem that when i try using the  command "sunbeam cluster bootstrap" and tip in the Management Network i  get the output Error: No registration token found in the Cluster  database. I tried it with specific roles like that --role control --role  compute --role storage and with --accept-default nether worked out. I  am a newcomer in the Openstack area and there is not a mention of a  database to install in the tutorial so I am not sure if there is  something what I am missing at that point.

 I have a testing environment where i work on a Proxmox Virtual Environment 8.0.3 The three notes for the openstack are Vms with the in the tutorial recommend specs of
 
[LIST=1]
[*]physical machine running Ubuntu 22.04 LTS
[*]a multi-core amd64 processor (ideally with 4+ cores) a minimum of
[*]32GiB of free memory
[*]200 GiB of SSD storage available on the root disk
[*]a least one un-partitioned disk of at least 200 GiB in size
[/LIST]
 and a virtual Opensense Firewall to manage the to network interfaces

---

### Post by sublethalrose on 2024-03-07
I had the same error and was resolved after starting over the process with default options (mainly the IPs), I hope this helps.

---

