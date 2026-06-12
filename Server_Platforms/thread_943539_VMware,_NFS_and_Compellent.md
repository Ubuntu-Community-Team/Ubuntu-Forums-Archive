---
title: "VMware, NFS and Compellent"
date: 2008-10-10
forum: Server Platforms
---

### Post by scuba8 on 2008-10-10
Hi,

I am playing with some ideas for my company's DR VMware enviroment.  Being a bank and living in the current financial crisis means creative ideas that are cost 0 as all budgets have evaporated. 

I have a compellent SAN in my DR and compared to production i dont have a redundant FC switch config just 2 FC ports on the back of a single SAN controller. So at most i can run 2 ESX servers direct attached over FC to the SAN controller.

I've read some interesting results when using NFS for VM datastores.

So the config im gonna test is ubuntu server acting as the NFS mount point, connect this server to the compellent for the data volume (getting the benefits of snapshots, SAN replication etc)then map 3 or 4 ESX servers via NFS to this Ubuntu server for the VMDK datastore.

What im hoping to gain is the ability to use all the tools ie vmotion snapshots etc and still get a reasonable performance point compared to a pure FC enviroment.  Plus be able to double the amount of ESX servers avaiable in DR.

I've read that Netapp using NFS and their WAFL filesystem scales really well for this kind of enviroment.

So as im no linux expert, any suggestions to get the most from this.  should I be using XFS instead of EXT3 etc etc

Im also wondering is it possible to map my RDM volumes (NTFS) to the ubuntu server and make these available to the ESX hosts

Any ideas or pointers i would be interested in hearing. Or is this gonna fall on its face

---

### Post by chrisj_0 on 2008-10-10
VMWware will work pretty well over NFS for a few low IO guests.
The real question is how much IO do you need? And do you need more IO than processor for your DR site?

You said that you won't be able to connect more than 2 vmware servers to your SAN via FC, but how may vmware servers do you need? 2 VMWare servers with less than 10 guest per server should run pretty well on well tuned NFS server. But all 10 would have to be pretty low IO. As soon as you put a few DB, exchange, high volume file server there your performance would tank.
You'd get a little better performance with a dedicated ISCSI SAN than using NFS. 

The numbers above are all based on the way your SAN is currently setup. the more spindles you have the better performance you'd get.
I'd go with the 2 vmware servers connected to FC and then just put less RAM on each to get them all on the pair of servers.

---

### Post by promodus on 2008-10-10
My idea, while it may not suite exactly to your needs, it's just an idea.

2 machines for storage: stor1, stor2

stor1 has it's own raid array, md0
stor2 has it's own raid arary also, md0

stor1
DRBD then mirrors to
stor2

Using heartbeat to create a virtual IP address between machines

Lastly each machine using LVM on top of DRBD
to do snapshots, and on that LVM have files dedicated as iSCSI targets for vmware.

Now for the hosts... use heartbeat to stop / start vmware on either side to connect to that virtual IP.

[IMG]http://www.promodus.net/failover.png[/IMG]

---

### Post by PilotJLR on 2008-10-10
When you said "WAFL scales really well" I really took notice.  :-)
Sure, it has pro's and con's. But it will hit a brick wall around 50 TB total capacity. It's a good system if you are okay with its limitations.

What you're doing is kinda a form of DIY storage virtualization. The best case here would be a real storage virt system, like SVC with FCoIP bridges for replication. That would also be really, really expensive.

Your idea will most certainly work only IF you create a new LUN on the compellent for this volume. You can't present an exising VMFS, since Ubuntu won't be able to use it. So if you can providing a new LUN, format to XFS or ext or whatever, then it will work.
NFS performance is good. It may or may not be the bottleneck, depending on your backend disk configuration on the compellent. Remember to do redundant paths on this NFS server!

For RDM, I'm not aware of a way to pass these through with linux.

Vmotion, DRS, HA all work fine with NFS datastores. You will lose some things, like the ability to use VCB or implement SRM.

---

### Post by scuba8 on 2008-10-13
Good morning,

Thanks for the great reply's

I'm going to set this up today and do some tests.  I'll let you know how it works out.

I agree that this is not an ideal solution for high IO and I would not use a solution like this in production, here i have setup the traditional dual fabric, dual controller FC etc, but thats too costly for DR.  Keeping in mind as well my budget has been 100% cut so its existing equipment or nothing so that equates to having spare servers sitting around.

When I said WAFL scales well (from White papers I've read) what I meant is in the way that it allows for a higher IO over NFS when its accesed by more than one ESX server than say NFS on EXT3.  Unfortuantly I'm taking that opninion on advice and not my own testing. Its interesting you put the cap of 50TB on this, you must be working with a large amount of data to hit that, we arent that large more like 15 - 20TB.

---

### Post by apadula on 2008-10-16
For your RDM's, you could try using iSCSI target software on the Linux server, like this one: [http://iscsitarget.sourceforge.net/](http://iscsitarget.sourceforge.net/).

From it's wiki, it appears that you can export a device file as an iSCSI lun straight to a client.  ESX has a built in software initiator that could then talk to the target and look at the RDM through the Linux server.

I've never tried this, so I'm not sure if it works or not, but it's worth a shot as it looks free.

You could also use this to present all of your storage and not use NFS at all, that way you still get to use VMFS.

Openfiler has an iSCSI target built into it too, could use that on your Linux server instead of a regular distribution.

---

### Post by windependence on 2008-10-16
> **chrisj_0 said:**
> VMWware will work pretty well over NFS for a few low IO guests.
The real question is how much IO do you need? And do you need more IO than processor for your DR site?

You said that you won't be able to connect more than 2 vmware servers to your SAN via FC, but how may vmware servers do you need? 2 VMWare servers with less than 10 guest per server should run pretty well on well tuned NFS server. But all 10 would have to be pretty low IO. As soon as you put a few DB, exchange, high volume file server there your performance would tank.
You'd get a little better performance with a dedicated ISCSI SAN than using NFS. 

The numbers above are all based on the way your SAN is currently setup. the more spindles you have the better performance you'd get.
I'd go with the 2 vmware servers connected to FC and then just put less RAM on each to get them all on the pair of servers.

I agree with Chris here, iSCSI would give you a bit more performance, but you will be surprised how well NFS will work for you and I think you will also be surprised at the I/O performance. It should be better than you expect.

Also, VMware has memory page sharing so you need a lot less RAM than you think on each VM. We have run some Windoze 2003 servers with just 256 MB of RAM. Of course, you don't want to run a database on that. :)

-Tim

---

### Post by scuba8 on 2009-08-06
Well in the end this didnt work out so well.

I have done testing using iscsi and openfiler for data stores and this works reasonably well considering its free and running on old hardware.  But not good enough for production but i think that was the limitation of the hardware used for testing.

The ultimate end to this is that we actually managed to get new hardware, so one server is all we need now in DR and 2 FC ports suffices.

Thanks for all the help to those who replied

Br

Stevo

---

### Post by windependence on 2009-08-06
In a production environment, you would want to have hardware RAID on your SAN, and have a good number of spindles for decent throughput. You would also want to either trunk some gigabit ethernet lines or use fiber or another large data pipe to the server. My SAN uses three gigabit nics, trunked together to the server.

-Tim

---

