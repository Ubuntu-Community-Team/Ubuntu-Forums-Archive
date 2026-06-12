---
title: "ubuntu 7.04 compatible server hardware for big VMware setup"
date: 2007-05-30
forum: Server Platforms
---

### Post by Sapphiron on 2007-05-30
Hi All

a complicated one for you all (called a challange)

I need to quote my client for a application server.  he wants to run a VMware server with multiple guest OS's.

he is going to use this server for running multiple instances(5-20) of their web based application and sell the software as a service (SAS model)

He is familiar with how to get his software running on Ubuntu 6.06 to 7.04.  The software can be very CPU and memory intensive in short bursts.

My problem is finding the right hardware for this configuration.  i have got access to multiple server component distributers in South Africa.  I can get most of the Intel parts and can get Supermicro servers as well.

here is the Intel server spec I have come up with.

2x Intel Xeon E5310 quad 1.6Ghz processors (8 cores in total)
Intel S5000VSASATA Server board
8x 2GB (16GB total) DDR2 Kingston RAM modules
3x 320GB SATA hard drives in RAID 5.
LSI megaraid PCI-X 6 port SATA controller

I am unsure of the exact hard drive configuration (Raid 5vs6vs1), which RAID controllers to use.  I would dearly like one that can rebuild in usermode, and provide email notification of any failures.  Normally the softwaredo not require very fast hard drives.  The software rarely uses the hard drive as almost the entire MySQL backend database gets loaded into memory.  I do not know what the effect of VMware will be on that  I have heard that there is quite a large performance difference between hardware raid controllers under linux.

Searching for Ubuntu linux compatability is pretty frustrating as most of the hardware manufacturers only certify their hardware for Old Linux OS's like SUSE enterprise 8 en Red hat enterprise 3.

Does anyone out there have experience with a setup like this.

I kinda like to go with a Supermicro server as they custom build to order and provide a 4 hour response onsite warranty.  I can also get Dell or HP servers too, but the choices there are very limited due to our 3rd world IT status.

Thanks in advance.  Any advice is wellcome

---

### Post by craigp84 on 2007-05-30
Hi Sapphiron,

What you suggest sounds fine for the most part. x86 is the most bang for your buck at this point. Although it doesn't win the best platform for stability award, it should be reliable enough.

The only 2 suggestions i'd make here are:

1) Drop the virtualisation if at all possible, it really does slow an app down, you can expect 50%-200% slowdown for each instance of the app compared with all of them running on the server unvirtualised. Or alternatively, virtualise in batches, so instead of one VM per app instance, run 5 instances to a VM.

2) Consider going raid1 or raid1+0 rather than raid5

I don't know what Sun Micro's support in SA is like, but if it's any good, they're worth a good look. Their x86 hardware is very well priced and excellent quality (first hand experience). Their SPARC kit is second to none for reliability but it's pricey too. The new T1000 and T2000 servers as designed for this kind of workload. They come with really simple to setup virtualisation either at the hardware level in the form of LDOMs or software level with Solaris Zones. Zones allow good, flexible configuration of hardware sharing between containers (guest instances).

Hope this helps,

-c

p.s. never realised i was such a Sun Micro fan boy. They are pretty good these days though

---

### Post by Brazen on 2007-05-30
We run VMWare software on several blade servers here.  We run about 8 virtual machines on each and they all STILL run at nearly native speed.  The only concern is RAM.  Be sure you have plenty of it as there is a little overhead (about 20-30MB per vm, I think) which it looks like you are aleady maxing out how much you can get.  Also, make sure you have plenty of harddrive speed.  We actually attached our servers to a fibre channel SAN and created 4 Raid5 arrays and then stripe the LUNs across all 4 arrays (effectively a Raid50).  To be honest though, we upgraded to that for capacity, not speed, using on-server Raid5 arrays worked like a charm for us before, but as we have grown I would have figured speed would have become an issue; I suppose it really just depends on how drive-intesive your app is.

I have not used Supermicro servers but have heard good things about them.  We use Dell here.

I think it's a great idea using vms for their hosted services.  It makes disaster recovery much easier... just bring in new hardware and restore your backed-up virtual machine images (there are command line tools to script taking a snapshot of the vms and then back those up to tape or wherever).  You should also keep your vms on a different partitions, so if your harddrives are intact, just pop them in the new server, reinstall the host OS, if need be, reinstall vmware server and fire up the vms.

One suggestion though... I love Ubuntu (Dapper only on servers) and Debian, but VMWare has excellent support for Redhat (and Redhat clones, I use CentOS) and flakey support for everyone else.

As for RAID controllers, there are so many to choose from.  Personally, linux software RAID is so mature and stable, I've always just used that.  Linux's software raid will probably be your only choice if you want it to email you on a drive failure (I do think Dell also has a utilty that works under linux that will monitor their Raid controller, but last I looked at it, there was no notification ability or it was not obviously apparent anyway).  If for some reason you don't want to use linux software Raid, you should probably google for your available raid controllers with 'linux' and see what turns up.

One more thing: why doesn't the client just install a single VM and use virtual hosts in Apache to provide SaS?

---

### Post by craigp84 on 2007-05-30
> The only concern is RAM

We used to run VMWare ESX on a few very large boxes (about 12 instances) but moved away, the performance was really really poor. The only useful feature we lost was vmotion.

PCI buses become bottlenecks and there's limited ability to dictate shares of I/O bandwidth to guests. So crappy unimportant guests make your important stuff wait.

> It makes disaster recovery much easier

Wrong, you don't get simpler than starting the app on another host. We do our env the old school way currently, NIS for accounts, NFS for storage, hosts are just compute. A DNS push and a quick startup on the new box is all that's required. No messing around with VMs.

Also think of the effort it takes to maintain a 20 instance VM setup. Factor in your BCP envs and you've got 40 hosts to patch, test, and generally maintain on an ongoing basis. The alternative is 2 x hosts and a lot cheaper to run.

> ne more thing: why doesn't the client just install a single VM and use virtual hosts in Apache to provide SaS?

What advantage does a VM provide at all in this case?

In general VM's attempt to solve a problem that doesn't exist for 99%+ businesses. Worse still, they fail to solve that problem!

It's just an added expense your client doesn't need. Invest the savings on licenceing on a good tape drive :-)

-c

---

### Post by Sapphiron on 2007-05-30
Thank you all for replying

The whole reasoning behind the VMware solution is because my client's software runs on a Java application server called Jboss.  Due to some legacy code and other complications in their software and application server, they cannot run more than one at a time.

One of the thing I am looking at for the client is simply to use one inexpensive server per instance.  Although it works out nearly the same price in total for the hardware, the running costs are massive.

Server hosting and Bandwidth in SA is nearly the most expensive in the world.  Our ADSL comes with a 1GB data Cap for $50 a month.  Thank our Telecom monopoly and their $1b a year profit margin for that.

Anyway, great to hear confidence in linux software RAID.  I have heard lots of people commending it over recent months, it seems to have come a long way.  A simple Raid 1 setup should not be too much of a problem.

Googling linux and Raid is almost crazy.  Most of the info is outdated, incorrect or irrelivant.  My frustration is leading me to lean toward software raid 1.  yes hardware RAID will be better, but by how much and at what cost?.

---

### Post by Brazen on 2007-05-31
> **craigp84 said:**
> We used to run VMWare ESX on a few very large boxes (about 12 instances) but moved away, the performance was really really poor. The only useful feature we lost was vmotion.

PCI buses become bottlenecks and there's limited ability to dictate shares of I/O bandwidth to guests. So crappy unimportant guests make your important stuff wait.



Wrong, you don't get simpler than starting the app on another host. We do our env the old school way currently, NIS for accounts, NFS for storage, hosts are just compute. A DNS push and a quick startup on the new box is all that's required. No messing around with VMs.

Also think of the effort it takes to maintain a 20 instance VM setup. Factor in your BCP envs and you've got 40 hosts to patch, test, and generally maintain on an ongoing basis. The alternative is 2 x hosts and a lot cheaper to run.



What advantage does a VM provide at all in this case?

In general VM's attempt to solve a problem that doesn't exist for 99%+ businesses. Worse still, they fail to solve that problem!

It's just an added expense your client doesn't need. Invest the savings on licenceing on a good tape drive :-)

-c

If you have 20 servers to run under vmware, how do you magically turn them into 2 on physical hosts?  Your comparison would have to be for maintaining 20 virtual machines versus maintaining 20 physical machines.

1.  It sounds like your problems with ESX are configuration related?  Did you align your partitions?  Did you read the best practices guide?  We run email servers, web servers, application servers, etc, many of which are under constant load and have zero performance problems.

2.. It sounds like your environment may just be small enough that the complexities of vms just don't outweigh the things they simplify.  When you move beyond 2 servers though, things get a little more complicated.  Personally, I think vms have advantages for small environments, too, but I understand that for some people the learning curve obfuscates things.

---

### Post by Brazen on 2007-05-31
> **Sapphiron said:**
> Thank you all for replying

The whole reasoning behind the VMware solution is because my client's software runs on a Java application server called Jboss.  Due to some legacy code and other complications in their software and application server, they cannot run more than one at a time.

One of the thing I am looking at for the client is simply to use one inexpensive server per instance.  Although it works out nearly the same price in total for the hardware, the running costs are massive.

Server hosting and Bandwidth in SA is nearly the most expensive in the world.  Our ADSL comes with a 1GB data Cap for $50 a month.  Thank our Telecom monopoly and their $1b a year profit margin for that.

Anyway, great to hear confidence in linux software RAID.  I have heard lots of people commending it over recent months, it seems to have come a long way.  A simple Raid 1 setup should not be too much of a problem.

Googling linux and Raid is almost crazy.  Most of the info is outdated, incorrect or irrelivant.  My frustration is leading me to lean toward software raid 1.  yes hardware RAID will be better, but by how much and at what cost?.

I have had great luck with great experience with LSI hardware raid.  If you want to go the hardware route, you will not be disappointed with LSI products.  Really though, you are not going to gain any features with hardware raid, in fact, you will probably be losing features, or at least ease of use of the features.  The advantage would be with performance, but primarily that is by offloading the processing from your main CPU.  And with CPUs these days, you are probably talking about less than 1% of the CPU load.

---

### Post by craigp84 on 2007-05-31
> **Brazen said:**
> If you have 20 servers to run under vmware, how do you magically turn them into 2 on physical hosts?

Take the need to run 12 jboss instances seperately - you get the 12 ip's, assign them to your network card, setup each instance's config, bring them up. Job done. They are now available for your app owners to deloy their apps into.

This is the way it's always been done, right back to the 80's and before possibly! Just think, how would you setup 4 x instances or oracle on the same box? It's the same high level approach.

> Your comparison would have to be for maintaining 20 virtual machines versus maintaining 20 physical machines.

No, as above, it's 2 x hosts versus 40 hosts to maintain and patch.

> 1.  It sounds like your problems with ESX are configuration related?  Did you align your partitions?  Did you read the best practices guide?  We run email servers, web servers, application servers, etc, many of which are under constant load and have zero performance problems.

VMware's own staff set it up, we had a senior vmware engineer on site for longer than i care to remember. They couldn't resolve the performance issues - actually, they pretty much buried their heads in the sand.

If you're seeing no performance degradation, then your measurements or instrumentation method are wrong. To be fair, 50%-200% performance loss is accepted as "the way it is" by quite a few top consultants i deal with monthly.

> 2.. It sounds like your environment may just be small enough that the complexities of vms just don't outweigh the things they simplify. 
My env? It's pretty much as big as it gets to be honest.

> When you move beyond 2 servers though, things get a little more complicated.  
Of course, and as such, you design appropriately. Virtualisation only complicates the scale issue - it makes the problem of scale, bigger.

> Personally, I think vms have advantages for small environments, too, but I understand that for some people the learning curve obfuscates things.
I only see heavyweight / slow partitioning - which is normally done fast at hardware level, c.f. large sun fire machines, mainframes etc. etc. as the benefit of virtualisation.

It's detractors are massive performance degredation (anything over 40% qualifies as massive), increased costs - the support contract quotes are unrealistic, never mind the considerable upfront costs.

My main dislike stems from It does not make my life easier as a sysadmin, instead of one machine that could fail, i have 20 times the chances of seeing a machine go down.

I'm lead to believe there are cases where virtualisation is the best solution. I have no first hand experience of them and have never encountered such a case. Read into this as you will.

-c

---

