---
title: "Samba error"
date: 2007-10-25
forum: Server Platforms
---

### Post by gubemton on 2007-10-25
Hi,

We set up Samba as a PDC, all is working well without any problems.
Howeven when i was checking out some logs i ran into this in log.nmbd

```
[2007/10/25 09:46:54, 0] nmbd/nmbd_browsesync.c:get_domain_master_name_node_status_fail(486)
  get_domain_master_name_node_status_fail:
  Doing a node status request to the domain master browser at IP 83.82.xxx.xxx failed.
  Cannot get workgroup name.
[2007/10/25 09:46:54, 0] nmbd/nmbd_browsesync.c:get_domain_master_name_node_status_fail(486)
  get_domain_master_name_node_status_fail:
  Doing a node status request to the domain master browser at IP 172.16.152.1 failed.
  Cannot get workgroup name.
[2007/10/25 09:46:54, 0] nmbd/nmbd_browsesync.c:get_domain_master_name_node_status_fail(486)
  get_domain_master_name_node_status_fail:
  Doing a node status request to the domain master browser at IP 172.16.88.1 failed.
  Cannot get workgroup name.
```
83.82.xxx.xxx is eth0 which is our external address
172.16.152.1 & 172.16.88.1 are vmnet1 & vmnet 8 which are virtual ccards from VMWare

Samba is set to only work on our local subnet so i find this rather odd...
```
	interfaces = 10.53.172.1/255.255.255.0
	bind interfaces only = Yes
```

Any idea's why these messages appear and how to get rid of them?

---

### Post by gubemton on 2007-10-26
Nobody?? :confused:

---

