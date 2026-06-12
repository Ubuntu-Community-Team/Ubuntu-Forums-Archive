---
title: "UEC instances immediately terminate"
date: 2010-02-18
forum: Server Platforms
---

### Post by sticksnleaves on 2010-02-18
I have a new UEC (Ubuntu 9.10) server up and running. I'm running a self contained solution so the cluster and node are on the same machine. I know this isn't ideal but I only have one server. I followed [https://help.ubuntu.com/community/UEC/Topologies]("https://help.ubuntu.com/community/UEC/Topologies") and [https://help.ubuntu.com/community/UEC/CDInstall]("https://help.ubuntu.com/community/UEC/CDInstall"). When I try to run a VM (Ubuntu 9.10 amd64) image it will go from pending to shut-down to terminated. I know others have had this problem but I haven't see any solutions. I'm hoping there might be one out there that I've missed. I'm running on an AMD 64-bit quad core with 8GB DDR3 RAM.

I am not seeing any errors in the logs.

---

### Post by sticksnleaves on 2010-02-18
I found this in my cluster-output.log

23:51:04  WARN AddressUtil               | Found orphaned public ip address: Address [cluster=snl-cluster-1, instanceAddress=0.0.0.0, instanceId=available, name=192.168.1.10, pending=false, state=unallocated, userId=nobody] count=4

Not sure if this means anything.

---

### Post by sticksnleaves on 2010-02-19
Something new I found.

When executing

[PHP]ec2-describe-availability-zones verbose[/PHP]

my nodes don't show up.

In my nc.log I see.

[Fri Feb 19 00:22:47 2010][001960][EUCAINFO  ] looking for existing domains
[Fri Feb 19 00:22:47 2010][001960][EUCAINFO  ] no currently running domains to adopt

I'm thinking it might have to do with my single server configuration. Has anybody successfully installed a cluster and node on the same server?

---

### Post by MilneCat on 2010-11-09
Sorry for trolling an old post, but...

I was having the same problem, but found the thread from gzmask

[http://ubuntuforums.org/showthread.php?t=1458048](http://ubuntuforums.org/showthread.php?t=1458048)  

Basically, I ran the following two lines:  
euca_conf --deregister-cluster <cluster-name> 
euca_conf --register-cluster<cluster-name> <ip-address>

That allowed the nc to find the cluster domain.

Then I ran into the instances immediately terminating and found the following lines in nc.log which explained it:

[Tue Nov  9 09:00:32 2010][002757][EUCAERROR ] libvirt: internal error no supported architecture for os type 'hvm' (code=1)
[Tue Nov  9 09:00:32 2010][002757][EUCAFATAL ] hypervisor failed to start domain
[Tue Nov  9 09:00:32 2010][002757][EUCADEBUG ] doDescribeResource() invoked
[Tue Nov  9 09:00:32 2010][002757][EUCADEBUG ] doDescribeResource() invoked
[Tue Nov  9 09:00:32 2010][002757][EUCADEBUG ] doDescribeInstances() invoked
[Tue Nov  9 09:00:32 2010][002757][EUCADEBUG ] doDescribeInstances() invoked
[Tue Nov  9 09:00:33 2010][002757][EUCAERROR ] libvirt: Domain not found: no domain with matching name 'i-4DAF0882' (code=42)
[Tue Nov  9 09:00:33 2010][002757][EUCAINFO  ] vrun(): [rm -rf /var/lib/eucalyptus/instances//admin/i-4DAF0882/]
[Tue Nov  9 09:00:34 2010][002757][EUCAINFO  ] stopping the network (vlan=10)

Basically, because my server doesn't support hardware virtualization, the nc can't start the hypervisor on it...the NC must be on a machine that supports hardware virtualization...sigh...

---

