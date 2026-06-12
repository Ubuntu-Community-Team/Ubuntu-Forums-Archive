---
title: "svr1804-Cloudinit-setting hostname to fqdn"
date: 2019-02-21
forum: Server Platforms
---

### Post by virtualcody on 2019-02-21
using nutanix calm and cloudinit to deploy a server image and set the hostname.  however to get it to properly update MS AD DNS forward and reverse lookups it wants the hostname to be the fqdn. setting that in the cloud-init config file doesnt actually set the hostname to the fqdn though:

#cloud-config
fqdn: <fqdn>
hostname: <fqdn>

any ideas on why the hostname setting being fqdn doesnt actually set the system hostname to the fqdn?

---

