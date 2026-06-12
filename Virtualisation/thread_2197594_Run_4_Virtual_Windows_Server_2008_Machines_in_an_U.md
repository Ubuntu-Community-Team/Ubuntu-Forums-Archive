---
title: "Run 4 Virtual Windows Server 2008 Machines in an Ubuntu Server"
date: 2014-01-04
forum: Virtualisation
---

### Post by RemiemB on 2014-01-04
I don't know if I am posting on the correct area but I work as a junior (very junior) systems admin in a restaurant chain in Mexico. 

We have 4 physical Windows servers scattered around town running special POS and Inventory Managemente Software. I want to know if it is posible to migrate and virtualize those 4 servers onto one physical server in our HQ.

I plan on using Ubuntu Server as the main OS in the physical and backup server.

Any ideas/help?

Thanks!

---

### Post by TheFu on 2014-01-05
PoS is usually tied to specific hardware, so no - doing what you want is probably NOT possible.
As an admin, you should also ask if it is really a good idea.  Do the different locations have VPNs back to the HQ?  That would be the first thing to check/ensure.

As to the inventory management software ... that might be able to be centrally located provided input uses normal hardware that can be virtually attached to remote systems.

Lastly, KVM is the normal way to virtualize VMs under Ubuntu, but there are other choices like Xen which can work for Windows guest VMs too.  I know that lots of places use Xen or KVM to virtualize VMs, but most are NOT 100% Windows.  For mission critical Windows VM stuff, people still tend to use options from either Microsoft or VMware ESXi.

So ... the first thing you should understand fully is which hardware must stay in the remote locations and determine whether that can remotely connect in a secure way back to HQ.  I'd also wonder how consistent the WAN connection is at these different places. Often connections that seem to be great really are not.

---

### Post by SeijiSensei on 2014-01-05
I would be concerned about your creating a "single point of failure" by centralizing the processing on one machine.  Right now, if one location's server goes down, presumably the other locations can continue to function normally.  Centralizing the processing creates the risk of bringing all the locations to a halt.  So whatever hardware you choose needs to be pretty beefy with things like redundant power supplies, RAID, a UPS with a large battery, and the like.  For more fault-tolerance you can use a [clustered]("http://www.tldp.org/HOWTO/Parallel-Processing-HOWTO-3.html") solution with machines designed to come online if the primary server fails.  

You might consider using a virtual server in the cloud as an alternative to a machine in your office.  A [Linode]("https://www.linode.com/") with 8 GB of RAM and 384 GB of storage costs US$160 per month, and you can cancel at any time.  For that you get well over 99% uptimes with reliable power and a large pipe to the Internet.  You can connect your office and the remote locations to the server using [OpenVPN]("http://openvpn.net/") tunnels for security.  (I have no financial interest in Linode; just a satisfied customer.)  To provide a similar degree of reliability on a server in your office will cost you thousands of dollars in hardware.  I just quickly priced a [Dell R320](http://configure.us.dell.com/dellstore/config.aspx?oc=bect133&model_id=poweredge-r320&c=us&l=en&s=bsd&cs=04).  With a redundant power supply, 8 GB of memory, and 2 x 500 GB 7.2K hot-plug SATA drives for Linux software RAID1, it comes in slightly over $1,600.  You'll also need a solid UPS for a few hundred more.  Depending on how much traffic the server will be handling, you might need to upgrade to 15K drives to avoid bottlenecks.  Your data storage needs might be larger than 500 GB, too.  What is the sum of the storage in use across the current locations?

---

### Post by TheFu on 2014-01-05
> **SeijiSensei said:**
> I would be concerned about your creating a "single point of failure" by centralizing the processing on one machine.  Right now, if one location's server goes down, presumably the other locations can continue to function normally.  Centralizing the processing creates the risk of bringing all the locations to a halt.  So whatever hardware you choose needs to be pretty beefy with things like redundant power supplies, RAID, a UPS with a large battery, and the like.  For more fault-tolerance you can use a clustered solution with machines designed to come online if the primary server fails.  

You might consider using a virtual server in the cloud as an alternative to a machine in your office.  A [Linode]("https://www.linode.com/") with 8 GB of RAM and 384 GB of storage costs US$160 per month, and you can cancel at any time.  For that you get well over 99% uptimes with reliable power and a large pipe to the Internet.  You can connect your office and the remote locations to the server using OpenVPN tunnels for security.  (I have no financial interest in Linode; just a satisfied customer.)  To provide a similar degree of reliability on a server in your office will cost you thousands of dollars in hardware.  I just quickly priced a [Dell R320](http://configure.us.dell.com/dellstore/config.aspx?oc=bect133&model_id=poweredge-r320&c=us&l=en&s=bsd&cs=04).  With a redundant power supply, 16 GB of memory, and 4 x 500 GB hot-plug SATA drives for Linux software RAID, it comes in slightly under $2,100.  You'll also need a solid UPS for a few hundred more.

I agree with the redundancy needs, but Linode might not be the best answer to run HVM VMs for Windows under. Is it even possible to get a physical server from the Linode guys?  Doesn't running a Windows VM require access to VT-x extensions and that is only available from physical CPUs?  Generally, I would avoid putting ANY financial transaction servers, like PoS, into the cloud. How would they pass PCI audits?  I simply do not trust shared physical hardware.  OTOH, if you can get a cage in a reputable data center for only your hardware .... THAT is completely different.

I used to believe that redundant hardware INSIDE the same server chassis was a good idea - didn't have a limited budget at that job.  These days, I'm much more likely to buy 2 cheaper systems without any redundancy (except RAID disks) and use careful replication between those systems to limit impacts of any failures or downtime.  Something like GlusterFS with block-level replication between the 2 systems perhaps?

OTOH, it is hard to get all the facts to make a good decision on this from 2k miles away. A business solution usually has subtle additional requirements that a pro can deploy under a formal engagement. ;)

---

