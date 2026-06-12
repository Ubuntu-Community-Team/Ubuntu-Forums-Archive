---
title: "Ubuntu 14.04 LTS Server unattended installation with preseed - Network issues"
date: 2014-12-16
forum: Server Platforms
---

### Post by chrisgibbs on 2014-12-16
Anyone have any ideas how i can preseed a ubuntu 14.04 unattended installation and use eth1? I currently have it configuring the network for the 2nd NIC but after it gets a DHCP lease it then stops and prompts to continue as no default gateway is set. Our provisioning network doesn't have a gateway... eth0 is the primary port with the default GW (and is unavailable during provisioning). The provisioning network instead relies on a proxy server to grab content from mirrors.

Using PXELiuux to pass in:
auto=true netcfg/get_gateway=10.250.0.10 netcfg/dhcp_timeout=30 netcfg/choose_interface=eth1 BOOTIF=00:0c:29:70:70:80 

Any ideas?

---

### Post by TheFu on 2014-12-16
Just a thought, but have you looked at **cobbler**?

---

### Post by chrisgibbs on 2014-12-16
As far as I was aware cobbler is just a provisioning tool to manage the bits and pieces of provisioning. i.e. it still uses kickstart / preseed as the unatented format for installations of CentOS / Ubuntu.

We are currently using Foreman for our provisioning tool, kind of like cobbler.

This however does not solve my issue.

---

### Post by koenn on 2014-12-19
Couldn't you just have the dcp-server supply a fake gateway address (eg an unused adress on your provisioning subnet) ? 
Then the installer will probably mark the "setting up the network" as done, and the fake address isn't going to do any harm as long as the system doen't need anything from outside the prov subnet (which you've already arranged for by having a proxy to the repo's).

---

### Post by chrisgibbs on 2014-12-21
Unfortunately that is not going to solve my issue. When the server is built, the provisioning network is still there for out-of-band puppet runs.

The default gateway on the provisioning network will get in the way of the production network.

---

