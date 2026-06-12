---
title: "Cluster Question (Disk vs Diskless nodes)"
date: 2011-04-05
forum: Server Platforms
---

### Post by withoutfences on 2011-04-05
Hi everyone;

I'm going to try setting up very small cluster @ home just for the purpose of doing it and understanding how it all works.

Now what I have is 6 Dell Optiplex 280's, I'm going to use one of them as the Head Node and the rest as cluster nodes (so yeah very small at 5 nodes)

I'm just at the point where I finished setting up the head node running 10.10 with Ubuntu Desktop (i've read that having a gui makes monitoring and admin somewhat easier).

Now for my 5 nodes i'm in a bit of a mixed boat.  Should I go diskless or disk on each of the nodes?  It's worth mentioning that each node will only have 1GB of RAM (that is all that was available to me).  This cause me to wonder if I do a network install if too much ram will be used during netboot, vs having a HD in each machine and install the os on there (plus I gain some swap space with the drives.)

Looking for some thoughts on diskless vs diskbase nodes, from anyone that has done the same.

Thanks and I look forward to hearing from you.

Cheers,
Gary

---

### Post by Fire_Chief on 2011-04-05
Overall, a disk solution is simpler to setup and test with when your node count is small.

A diskless solution will require additional network services to be configured (DHCP, PXE, TFTP) plus you'll need to build your bootable image (if you want it to be customized). This does require more work up front but is very handy with larger deployments (50+ systems). You'll also want to verify that the workstations will do network booting (PXE boot) properly.

Don't worry about the resource usage when the system is net booting, it's only temporary. Once the OS loads, the system resource usage is the same regardless of net boot or local boot.

There are many different types of clusters out there and each serves some specific purposes. What kind of cluster are you looking to build?

Cheers!

---

### Post by withoutfences on 2011-04-05
Hi and thanks for your reply;

Well, my goal is to attempt an installation of BOINC for seti@home, just to see if it works, beyond that I'm not sure.

I guess the answer is High Performance or Load Balancing cluster.

I'll give disk based a shot first and see how it goes, get my head wrapped around clustering, and then once I'm more comfortable with it, I'll use the same 6 machines for a diskless setup and see how that goes.

also another quick question.  Ubunutu Server for the nodes I'm assuming is the best solution, since they dont' need X or anything like that?

thanks again for all of your help.

Cheers,

---

### Post by Fire_Chief on 2011-04-05
So in general, BOINC does not operate in a traditional cluster environment. It primarily supports groups of individual PCs each running a BOINC client crunching its own data blocks. There are guides to configuring a farm of these and using BOINCView to monitor all of them but this is not really a cluster per se.

See here [http://www.boinc-wiki.info/Creating_a_diskless_cluster]("http://www.boinc-wiki.info/Creating_a_diskless_cluster")

You can create a head node to proxy the communication from your farm nodes back to the BOINC servers if desired though this seems excessively complicated.

I did run across this clustering concept though...[Kerrighed clustering]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide"). Pretty interesting idea.

EDIT: Yes, Ubuntu Server would be ideal for this since it does not run a GUI by default.

Cheers!

---

### Post by withoutfences on 2011-04-05
Hey Chief;
 
Yes I am aware that BOINC is not traditionally a cluster piece of softwar since it is by it's very nature clustered with all the end users.
 
My objective is to have the head node download the data bit, and then delegate it out to the cluster, for decreased processing time (which leads me to a load balancing style cluster). Reason...I dunno sounds cool and I can impress my friends at dinner parties :). Oh and that kind of mess moderatly anoys my wife which has merit also.
 
I'll let you know how it is going...I'm considering starting a launchbox for it, just so if it is successful, there is some record of it.
 
Cheers,

---

