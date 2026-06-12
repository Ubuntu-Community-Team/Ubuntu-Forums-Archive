---
title: "Ubuntu as SAN OS?"
date: 2010-11-02
forum: Server Platforms
---

### Post by tlsarles on 2010-11-02
I am looking for an OS or distro that can be configured as a SAN host. I want to get two identical boxes, and have them setup as a storage cluster.

a filesystem will need to stay in sync between the two nodes, and one should transparently take the place of the other if one goes down. I have been looking at buying actual SAN servers, but the cost is insane. Is there an open source solution that will do this? Free with the option to purchase support is what I am looking for.

---

### Post by BobVila on 2010-11-02
Have you taken a look at FreeNAS? I'm not sure about the active/passive standby stuff, but I've used it in VMs to make pretend iSCSI SANs in the past.

---

### Post by tlsarles on 2010-11-02
FreeNAS does do RSYNC, but this is not a real time sync. Also, I don't believe it will do a transparent failover.

It would work to do a sync on a regular interval, and then re-point my VM server in the event of a failure. That will have minimal downtime. However, my goal is a zero downtime system.

---

### Post by Fire_Chief on 2010-11-02
On a different track, you could try using the GlusterFS Storage Platform. [http://www.gluster.com/products/index.php]("http://www.gluster.com/products/index.php")
You can use it for free with registration. Not sure if it does iSCSI but it does do NFS, CIFS, etc.
The only minor caveat is the hosts have have 64-bit CPUs so older commodity hardware is out.

Cheers!

---

### Post by tlsarles on 2010-11-02
I do like the Gluster idea. It seems nobody is interested in the market I am aiming for; small business. One large enough to want a high availability solution, but not one that can spend $30k on storage alone.

Gluster = $10k/server/year

Another solution that looked awesome was :
[http://www.nexentastor.org/](http://www.nexentastor.org/)

But this solution ended up being closer to 15k worth of licensing for a 2 node cluster.... which i understand if these were huge systems, but I'm looking at something in the ballpark of a 2U, 8 drive, single proc supermicro type system. I can't reasonably expected to pay that sort of cost to support that scale of a system.

---

### Post by BobVila on 2010-11-02
Gluster's pretty neat, as is TahoeFS. I'm not sure you'll find any FOSS tools that will have the all the features of a traditional SAN that you're looking for. I guess there's a reason they're so damned expensive  :( 

I agree with you, though. There isn't much attention paid to the small/medium business that covets HA, but can't spend on some of the outlandish stuff that enterprises can. I'm guessing the market isn't large enough to be lucrative.

I get the feeling that you'll end up with a RAID 6 box rsycnd to a backup unless the budget inflates rather substantially.

---

### Post by rubylaser on 2010-11-03
All you need is DRDB and Heartbeat to accomplish a Clustered Fault Tolerant share.  Here's some older directions for Openfiler.
[http://www.howtoforge.com/installing-and-configuring-openfiler-with-drbd-and-heartbeat]("http://www.howtoforge.com/installing-and-configuring-openfiler-with-drbd-and-heartbeat")

---

### Post by rubylaser on 2010-11-03
Cluster Labs has a good example too...
[http://www.clusterlabs.org/wiki/Main_Page]("http://www.clusterlabs.org/wiki/Main_Page")

---

### Post by CRCarl on 2010-11-05
Caveat, I work at Gluster as a Systems Engineer. 

Gluster is licensed with AGPL, it's free to use however you would like to. 

We have a .deb file for easy installation on Ubuntu, [http://download.gluster.com/pub/gluster/glusterfs/3.1/LATEST/Ubuntu/]("http://download.gluster.com/pub/gluster/glusterfs/3.1/LATEST/Ubuntu/").

There is a great mailing list, you can subscribe here - [http://gluster.org/cgi-bin/mailman/listinfo/gluster-users]("http://gluster.org/cgi-bin/mailman/listinfo/gluster-users"). There are lots of Gluster users using Ubuntu.

Documentation is here - [http://www.gluster.com/community/documentation/index.php/Main_Page]("http://www.gluster.com/community/documentation/index.php/Main_Page").

We do offer support contracts, they start at $1000.00/server/year and go up from there depending on the level of support you want. Please let me know if you have any questions, and welcome to the Gluster community!

---

### Post by Fire_Chief on 2010-11-08
Hi CRCarl! Thanks for the info. Does the AGPL version have a web management interface similar to the Storage Platform product? It looks quite slick.

Cheers!

---

### Post by CRCarl on 2010-11-10
Fire_Chief - 
    Both versions of Gluster are licensed with the AGPL, the Storage Platform version is 100% OSS AGPL'ed, have fun! There is a new version coming out shortly, I'll PM you when it does. 

CRCarl
[email]craig@gluster.com[/email]

---

