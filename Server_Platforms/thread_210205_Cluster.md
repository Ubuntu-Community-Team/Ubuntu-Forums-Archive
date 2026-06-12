---
title: "Cluster"
date: 2006-07-06
forum: Server Platforms
---

### Post by markbworth on 2006-07-06
I am developing a collection of random computers and I am contemplating the idea of building a cluster. I just wanted to ask what where peoples opinions on how I should go about doing it. What kind of hardware, software, ect. that I should use. What method I should use on building the cluster and all that. Any ideas/resources that you could give me would be appreciated.

Mark

p.s. I don't have any particular reason for building a cluster other than the experience and the fun of it. Call it a hobby I suppose.

---

### Post by ExMachina on 2006-07-06
[QUOTE=markbworth]I am developing a collection of random computers and I am contemplating the idea of building a cluster. I just wanted to ask what where peoples opinions on how I should go about doing it. What kind of hardware, software, ect. that I should use. What method I should use on building the cluster and all that. Any ideas/resources that you could give me would be appreciated.

Mark

p.s. I don't have any particular reason for building a cluster other than the experience and the fun of it. Call it a hobby I suppose.[/QUOTE]

Look at the stone soup project. They have a lot of information on how to do stuff like this and its quite interestign and neat although if you know about clusters i think you would know of stone soup

---

### Post by markbworth on 2006-07-06
I don't know much about clusters hence the fact that I was asking. Honestly I am relatively new to the Linux world (2 months), and it has only been recently that I really have tried to do anything more than email/internet/gaming.

Where is the stone soup project information?

---

### Post by markbworth on 2006-07-06
I found the Stone SouperComputer Project online. Thanks for the suggestion. They have some good information there. If anyone has anything else though it would be appreciated. I would like to hear from other people who have made or tried to make clusters. What kind of problems did you have and how did you fix them?

---

### Post by Glut on 2006-07-07
We've had a lot of success with OpenMOSIX. There are a bunch of live cd's floating around, so hypothetically you just plug them in and away you go.

---

### Post by markbworth on 2006-07-07
Where could I get a live cd for that? I am also probably going to be building a cluster for my work. We do a bit of scientific simulations and need the extra processing power, but we have a small budget so Linux is perfect for it (being free). Can I get OpenMOSIX online? If so where, and if not where could I get a live cd for it?

---

### Post by richardhp on 2006-07-09
I am also very interested in building a Linux cluster out of some old 98 computers I have (finally found a use for them) mainly for acedemic purposes.

I have been reading a little about it and have found some links that might be useful.

[http://www.gdargaud.net/Hack/ClusterNotes.html](http://www.gdargaud.net/Hack/ClusterNotes.html)
[http://www.samag.com/documents/s=9658/sam0505a/0505a.htm](http://www.samag.com/documents/s=9658/sam0505a/0505a.htm)
[http://www.beowulf.org/](http://www.beowulf.org/)
[http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book.php](http://www.phy.duke.edu/~rgb/Beowulf/beowulf_book.php)

As of yet the only problem I have is that I can't seem to find any information on actually installing one.

Do I just install loads of copies of Linux on many machines, then network them all, or is there a specific version of Linux that I have to install to allow me to do parrallel processing?

---

### Post by Tycoon on 2006-07-10
To answer your questions:

I know for a fact in [openMosix]("http://www.openmosix.org") they need to be running the same kernel version... (example 2.4.26)

With openMosix you should beable to install the kernel onto the distribution as long as it supports the 2.4.x kernel.  Easiest way to do this is to just use the .RPM file or convert it using Alien to .DEB.  If all goes well it will roll right on the system and should even update grub for you.  Harder way is to download a vanilla kernel (pure kernel, not a bloated one like shipped with the distribution) and patch it using the correct patch file and compiling it yourself.  Needless to say it can be very tricky as you do have some options you need to manually set while you compile it.  The reason for the vanilla kernel is some distributions put so much crap into the kernels they ship with if you try to patch it will still fail to work correctly.  Believe me I tried with Fedora Core just to see.

That being said openMosix is not very friendly with Ubuntu.  They still don't have the 2.6.x Kernel out for it the last time I checked.  You can get it to work with the old 2.4 kernel, but it will break X (atleast in my experience).  They have a 2.6 openMosix tester's only .RPM out but I could not get it to migrate for the life of me.  Automatic migration wasn't in there, meaning the PIDs spawn off to the cluster automatically.  You had to physically go into the /proc and write to the PID file to migrate and for some reason it was killing all the job still.  I gave up on that.

I'm using [clusterKnoppix Version 3.6]("http://clusterknoppix.sw.be/") right now (runs openMosix in KDE).  It's a live cd, so you just pop it, in reboot, and then start up the server.  Basically just run "openMosix Terminal Server" setup your NIC, IP,... etc.  You can also get it to PXE Boot the other machines if their NICs/motherboards are capable (and the terminal server is configured for that NIC).  Which is extremely nice, being you just run a CDROM or DVD drive in the first machine and the rest can be without a single drive and function!  Downside is that if you lose power or a machine gets reset you'll kill that process and the data will be lost.

That being said I got tired of frequent power losses and decided even having my $70 UPS backup system was not enough.  I hard drive installed clusterKnoppix (special command to write the CD image to the hard drive of a machine so you no longer need the cd to boot).  That let me modify the hard drive contents also, so I could then install the distributed.net client and run it without complete data loss if it was reset (live CDs are strictly read-only).  Downside to that was it seems to have broke my PXE booting capability, so I'm back to booting up with cds again.

That being said I'm running 9 nodes with the total of around $550 invested in my hardware (including 16 port switch, cabling, power strips, towers, and spare parts left).  I'm currently at 7.7 GHz, which does nicely for data crunching.

Depending on the size of your network I would sugguest a nice 10/100 switch.  I scored my 16-port for ~$45 or so from TigerDirect, of course you could use a smaller one if it still fits your needs.

Feel free to fire out the questions, I stop by from time to time.

---

### Post by ExMachina on 2006-07-10
Wow. This is pretty kewl information!
Now only if i had computers that worked <.< the one i ahve just dont work. Not sure why.

---

### Post by richardhp on 2006-07-16
Ok sounds great. I have looked at clusterknoppix but it looks to me that you cannot get an install verison (or that i can't fins it) and that is not good. Is there a distro that allows you to install cluster enabled kernels onto hard disk?

Until I can find one I will keep on trying with Ubuntu. If I get any problems then I will post them

---

### Post by Tycoon on 2006-07-16
You can install it, but it's just kinda a pain.

You're best bet is if you want to use openmosix that much, get Fedora Core 1 and use the RPM kernel onto it.  Nice, easy, and I vouch it works!

---

### Post by WADemosthenes on 2006-08-09
Does anything work well with ubuntu?

---

### Post by Tycoon on 2006-08-09
Not with openMosix... Currently openMosix has 2.6.X still in the Developer Only Status, so it might be working... or it might not.  I couldn't figure it out and writing the proc PID directory to migrate jobs took awhile and I never could get stuff to migrate properly without just flat out killing the process.

WHEN it goes to 2.6 release it should work.  

I don't know about the other clusters you need to look around yourself.

---

### Post by chrisfay on 2006-08-09
I'm not sure what type of cluster you are considering but these two howto's go pretty well together and give some good ideas.

One deals with configuring a loadbalanced two node apache cluster while the other deals with configuring an NFS high availability storage solution for both nodes. 

Apache setup:
[http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster](http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster)

NFS:
[http://www.howtoforge.com/high_availability_nfs_drbd_heartbeat](http://www.howtoforge.com/high_availability_nfs_drbd_heartbeat)

---

### Post by harisund on 2006-08-09
My serious suggestion would be this: 

First, figure out what is it that you want to do once you have your cluster. Parallel programming? Most likely. The question is high performance versus High availaibilty. RAID, anyone?

Once you have figured that out, search online etc for options of softwares that allow you to do what you want. You want parallel programming? MPICH, LAM, PVM etc.. you want to schedule your jobs? SGE.. PBS and so on. You want to monitor all the nodes in your cluster? Go for Ganglia. 

That said, once you have figured out what softwares you are likely to be using, search for an cluster OS that comes with the software you are looking for. I would suggest a nice little distro called ROCKS. [http://www.rocksclusters.org](http://www.rocksclusters.org) or something. 

The advantage with the cluster solution is that everything is not only configured, as you work with it you will learn a lot along the way. (The reason I am saying this is because I am currently building clusters and working with the high performance computing group in my university). 

Basically the difference between a regular multiple OS installation and cluster installation is that in the latter case, you install one machine called 'head node' or 'front end'. Then on, you PXE boot each 'child' or 'slave' node. The master automatically makes necessary adjustments. I will give you some examples of what Rocks does: 

1. Update a MySQL database with the necessary information when a new cluster is added. 
2. Add an entry in the /etc/hosts file for easier access. 
3. Copy the public key in the child node for passwordless SSH access (needed for MPI etc)
4. There is just one home folder, in the head node. AutoFS is used to mount this home directory across each nodes. So technically you can connect all your disk space to the first space, and keep the rest as diskless nodes. 
5. Update all the software with the knowledge that a new computer (and correspondingly, new CPU) etc have been added. Depending on whether it MIMD, SIMD stuff is configured automatically. 
and more .. will let you know as I learn. 

Slowly, I am saving up and buying cheap machines from eBay at home. Eventually I intend to come up with a clustering solution for Ubuntu. So basically I will learn everything that Rocks does (automatically) and then manually implement it in Ubuntu. 

Do that, instead of starting from a scratch. It's a waste to try and reinvent the wheel. There are lots of cluster distributions. Learn from one and then customize your own, then start from scratch.

---

### Post by WADemosthenes on 2006-08-11
I rather have ease of use, I'm doing it as an experiment (make a viable computer out of 3 old ones).

---

### Post by karih on 2006-08-13
Hi, sorry to interrupt this thread but you are discussing exactly the thing I've been reading about for the last week.

I'm preparing for constructing a high performance cluster from four computers (just to make it work) and I am getting confused by all this software available.  From what I've figured there are two clustering solutions that are most famous, these are Mosix and Beowulf.  Then I ran into this page: [https://wiki.ubuntu.com/UbuntuEdgyClusters](https://wiki.ubuntu.com/UbuntuEdgyClusters)

This page doesn't mention either one, instead it talks about SLURM and maui scheduler.  Where does that come into the picture as opposed to Mosix and Beowulf?

The cluster I am building would not exactly be for high performace clustering but rather designed for a huge apache web server or something in that category.  Therefore I would rather not need to use special commands to let programs run on the cluster, all programs should run on the master node who should transparently distribute processess/threads to the processing nodes.  Is there any software that does this?

I'm a bit confused, first it seemd that one should choose between Mosix and Beowulf but then all these names and acronyms flood my brain.  If anyone could simplify things for me that would be much appreciated!

Thanks!

---

### Post by rick_1010 on 2006-10-09
I saw a thread earlier in the forums that talks about possibly including an openmosix enabled kernel in the next ubuntu release. I think this is a great idea and everyone should get behind it as currently openmosix is very difficult to deal with if you want to use it on a newer distro, with the latest kernel being for 2.4.26 which is years out of date. Personally, I would like to run an Xubuntu cluster and get the most out of older hardware.

I have tested OpenMosix on Fedora Core 1 and ClusterKnoppix and it seems to be the ideal "easy to use" cluster as it basically does everything for you. It isn't the solution for every project but for the average user who wants a cluster or for small business environments it would be very useful as it allows older hardware to be clustered to migrate processes automatically between the machines to keep them running at full efficiency.

---

