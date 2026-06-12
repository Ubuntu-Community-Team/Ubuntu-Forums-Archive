---
title: "Ubuntu Server Cluster or mirror environment"
date: 2008-03-05
forum: Server Platforms
---

### Post by theonegod on 2008-03-05
I run several Ubuntu LAMP servers as production and Development Apache environments. I run them all in VMs. It is becoming hard to get time to bring down the production VMs for the purpose of backing them up via copying the VM folder.

One potential solution that I thought of was to have 2 mirrored or clustered (not sure which term would be accurate here) VMs that are essentially clones of each other much like a raid 1 situation. Then all I would have to do is bring down one of the servers for the backup and there would be no downtime. 

What would be the correct terminology for what I am trying to do and does anyone know the best way to get it done?

---

### Post by faulkes on 2008-03-05
> **theonegod said:**
> 
What would be the correct terminology for what I am trying to do and does anyone know the best way to get it done?

fail-over would be the correct terminology, as you want one server
to take over if another server is down, doing the exact same job.

The over-arching terminology though is generally referred to as 
load-balancing.

Depending on the -server version you are currently at, there is the balance
project (for Hardy), I'm not sure what exists for 7.10 or 7.04, however it 
should build for those platforms.

[http://packages.ubuntu.com/hardy/admin/balance](http://packages.ubuntu.com/hardy/admin/balance)

There is a link to the vendor/maintainer of the package on that page.  That 
is one solution among *many* possible ones.

Noting that this doesn't take into account replication of content (such as 
if you store it in a mysql database, or just the flat files)

Faulkes

---

### Post by HermanAB on 2008-03-06
Well, if it is only two, then you can do it with your DNS.

---

### Post by paradexes on 2008-03-21
I am looking for a similar config as well. Except I am trying to do this with a cups/samba server. I want to have one pointer URL and have it failover to the other servers in the cluster as needed.

---

