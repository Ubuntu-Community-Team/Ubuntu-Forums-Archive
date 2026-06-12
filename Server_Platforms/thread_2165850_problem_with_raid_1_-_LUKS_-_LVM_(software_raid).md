---
title: "problem with raid 1 - LUKS - LVM (software raid)"
date: 2013-08-06
forum: Server Platforms
---

### Post by jefkebazaar2 on 2013-08-06
Hello,


I am trying at the moment to setup an ubuntu server with software raid 1, luks and lvm.

Basically, I do the following:
2 hard disks -> sda & sdb.
I create two partitions per disk: sda1 (1GB) - sda2 (rest of disk); sdb1 (1GB) - sdb2 (rest of disk)
Then I create two raid devices -> md0 = sda1 + sdb1; md1 = sda2 + sdb2
I then make sure that md0 is used as ext4, bootable, /boot mounted.
On md1 I create an encrypted device. On this encrypted device I create an LVM. In this LVM I create a swap and an ext4 logical volume with / mounted.

This is all ok, ubuntu installs, I can restart, I can install all updates, everything checks out.

Then the problems begin: I want to test to see if my software raid works. (I checked that it should boot even degraded during install).
I unplug one of the two disks and reboot.

It sits there for a long while at the beginning of boot, waiting for encrypted source device. Then after several minutes it drops me to an initramfs prompt and that's it, game over.
Some symptom if I remove either disk 1 or disk 2... What is going on here?
I find some descriptions via google and on this forums of resembling issues, but those already date back since months/years sometimes. You're not telling me ubuntu is aware that this is a bug and isn't doing anything to solve it? Or am I doing something wrong here?

Any advice is greatly appreciated!

---

### Post by jefkebazaar2 on 2013-08-06
Hello,


I am trying at the moment to setup an ubuntu server with software raid 1, luks and lvm.

Basically, I do the following:
2 hard disks -> sda & sdb.
I create two partitions per disk: sda1 (1GB) - sda2 (rest of disk); sdb1 (1GB) - sdb2 (rest of disk)
Then I create two raid devices -> md0 = sda1 + sdb1; md1 = sda2 + sdb2
I then make sure that md0 is used as ext4, bootable, /boot mounted.
On md1 I create an encrypted device. On this encrypted device I create  an LVM. In this LVM I create a swap and an ext4 logical volume with /  mounted.

This is all ok, ubuntu installs, I can restart, I can install all updates, everything checks out.

Then the problems begin: I want to test to see if my software raid  works. (I checked that it should boot even degraded during install).
I unplug one of the two disks and reboot.

It sits there for a long while at the beginning of boot, waiting for  encrypted source device. Then after several minutes it drops me to an  initramfs prompt and that's it, game over.
Some symptom if I remove either disk 1 or disk 2... What is going on here?
I find some descriptions via google and on this forums of resembling  issues, but those already date back since months/years sometimes. You're  not telling me ubuntu is aware that this is a bug and isn't doing  anything to solve it? Or am I doing something wrong here?

Any advice is greatly appreciated!

---

### Post by TheFu on 2013-08-06
While it should work, sometimes complex things like this just don't.  For a long time, we had to have /boot without RAID, so many old-timers still run that way. It doesn't change that much and creating a mirror of 500MB /boot takes next to nothing.

You said that any advice would be appreciated. ;)  
Sorry - not the answer you wanted.

When it comes to troubleshooting things like this - you really need to look inside the log files for hints. If those are missing, perhaps setting up an rsyslog that sends the log files to a remote system is needed?

---

### Post by Vegan on 2013-08-06
software RAID is not safe, and its not a substitute for a backup

---

### Post by bab1 on 2013-08-06
> **jefkebazaar2 said:**
> Hello,


I am trying at the moment to setup an ubuntu server with software raid 1, luks and lvm.

Basically, I do the following:
2 hard disks -> sda & sdb.
I create two partitions per disk: sda1 (1GB) - sda2 (rest of disk); sdb1 (1GB) - sdb2 (rest of disk)
Then I create two raid devices -> md0 = sda1 + sdb1; md1 = sda2 + sdb2
I then make sure that md0 is used as ext4, bootable, /boot mounted.
On md1 I create an encrypted device. On this encrypted device I create  an LVM. In this LVM I create a swap and an ext4 logical volume with /  mounted.

This is all ok, ubuntu installs, I can restart, I can install all updates, everything checks out.

Then the problems begin: I want to test to see if my software raid  works. (I checked that it should boot even degraded during install).
I unplug one of the two disks and reboot.

It sits there for a long while at the beginning of boot, waiting for  encrypted source device. Then after several minutes it drops me to an  initramfs prompt and that's it, game over.
Some symptom if I remove either disk 1 or disk 2... What is going on here?
I find some descriptions via google and on this forums of resembling  issues, but those already date back since months/years sometimes. You're  not telling me ubuntu is aware that this is a bug and isn't doing  anything to solve it? Or am I doing something wrong here?

Any advice is greatly appreciated!

I assume you are just testing this setup.  There is no advantage to setting up RAID on multiple partitions of the same drive (device).  The same is true setting up LVM across multiple partitions of the same device is of little advantage from the point of view of LVM.  

Both of these methods add a layer of abstraction that removes some relationship between device and the filesystem on the partition.  By this I mean that RAID allows you to combine devices (spindles (that the platers rotate on)) into one partition that you then format with a file system.  You can add striping so that a device can fail and you can replace that device.  But in your case where both partitions have a failed device (on same spindle).  

The same is true of LVM.  LVM allows you to combine devices to allow for partitions to be created without regard for any single device in the LV.

I would assume the problem you are having is due to the unusual configuration.  It appears that there is not enough information for either RAID to run with a failed drive.  In other words: why do this in the first place?  Or am I way off base and not understanding what you are doing here.

@Vegan, normally I don't respond to others opinions, but in this case I will ask: how is a statement like yours valuable to the OP.   As you have stated it, it is just an unfounded opinion.  If software RAID is indeed "not safe"; why is it not safe.  Documenting your statement would be nice if you can't state it yourself.  In the same manner, why is it "not a substitute for a backup".  It really doesn't help the OP to understand what his options are or enlighten him/her regarding RAID or LVM strategies.

---

### Post by QIII on 2013-08-06
Threads merged.

Please do not create duplicate threads in different parts of the Forum.  It dilutes the community's effort to help you.

---

### Post by jefkebazaar2 on 2013-08-07
> **bab1 said:**
> I assume you are just testing this setup.  There is no advantage to setting up RAID on multiple partitions of the same drive (device).  The same is true setting up LVM across multiple partitions of the same device is of little advantage from the point of view of LVM.  



Your assumption would be right :-)
And the reason why I'm doing this is, well, this link: [http://ubuntuforums.org/showthread.php?t=1935300](http://ubuntuforums.org/showthread.php?t=1935300)
It's a tutorial, and well, it says "Solved", so I guessed this worked :-) Only difference is indeed that instead of putting the /boot on one disk, I put it on both disks in raid 1. But I can't exactly see this as a major blocking issue, rather an improvement on the availability of the system no?

So, if using soft-raid 1 with LVM and Luks isn't the way to go, then what would be the recommended way to go?
My requirements are:
- the disks need to be raid 1, so that either one of the disks can fail, the machine still needs to come up.
- it needs to be encrypted.

And thanks to everybody for the replies until now!

---

### Post by bab1 on 2013-08-07
> **jefkebazaar2 said:**
> Your assumption would be right :-)
And the reason why I'm doing this is, well, this link: [http://ubuntuforums.org/showthread.php?t=1935300](http://ubuntuforums.org/showthread.php?t=1935300)
It's a tutorial, and well, it says "Solved", so I guessed this worked :-) 

That's a poor reason to do anything.  Just because means you are not thinking the process out.  You're just following someone else's possibly misguided thoughts. 
> 
Only difference is indeed that instead of putting the /boot on one disk, I put it on both disks in raid 1. But I can't exactly see this as a major blocking issue, rather an improvement on the availability of the system no?

I don't see that and your simple tests don't see that either.  I have plenty of servers that get rebuilt long before the single HDD that holds the /boot partition fails.  Yes I have had HDD failure and I have had to rebuild from bare metal in less than 30 minutes, but that is a very rare occurrence these days.   If you have a host that needs high availability, I would think about a fail over to another entire machine (hot replacement).  See [**[COLOR="#FF8C00"]here[/COLOR]**]("https://www.google.com/search?q=high+availability+failover&btnG=Go!") for more info.  
> 
So, if using soft-raid 1 with LVM and Luks isn't the way to go, then what would be the recommended way to go?

It really depends on what your trying to achieve.  if testing is all you are doing then just experiment and see what works and what doesn't.  If learning about WHY these options are available then I would dig in and read about all of them and ask a lot of questions.  Personally I don't use RAID at all.  But if you use RAID, use it for what it was intended for; high performance with hardware redundancy.  Data safety is only  a secondary aspect.  I've seen more RAID failure that couldn't be rescued than not.  See [**[COLOR="#FF8C00"]here[/COLOR]**]("http://storagemojo.com/2012/07/23/the-post-raid-era-has-begun/") for some thoughts on RAID in the 21st century.

I would recommend a good backup routine that protects all of your data.  Document all of your operating system and application configuration.  If you have a need for consistency over many installs you can look into either[**[COLOR="#FF8C00"] puppet or chef[/COLOR]**]("https://www.google.com/search?q=puppet+chef+linux&btnG=Go!").> 

My requirements are:
- the disks need to be raid 1, so that either one of the disks can fail, the machine still needs to come up.

What makes you think this scenario will happen?  Raid 1 is for fast read speed in a high availability system.  The most likely scenario is that the system will still fail to boot when the software RAID fails or when you loose a drive (HDD).  
> 
- it needs to be encrypted.
Why would you need to encrypt the /boot file system?  What do you gain from that.  There are other more appropriate methods you can use to harden the system.  Data can be encrypted if you like, but I don't see any advantage to encrypting /boot. 

And thanks to everybody for the replies until now!
Again, what you do depends on what you are ultimately trying to achieve in the end.  I use a small disk for booting (there is less that 10 GB space needed) and LVM for all of the data stores.  

After may years the configuration on my machines are pretty consistent.  In fact I have the same config file parameters used for most of my hosts.

I backup every day to a remote LV that some day will be an all SSD array.  I've never had my data hacked.  I only use encryption on those directories that hold sensitive data.  I don't encrypt the bosses images from last weeks BBQ.  :D

Then there is the inevitable hardware and software failures to think about.  Like I said, I don't see that much failure of hardware anymore.  Yes the occasional drive will fail (about once every 5 years or so).  The most likely scenario is new equipment failing in the first 90 days or failure due to power surges.  The first can be controlled with burn in testing procedures if you like.  The second one you will just have to deal with on a case by case basis.  A RAID array won't be of any help as a defense in this case anyway.  If you are truly paranoid about HDD failure I believe you can have hdparam output HDD specs to the syslog.  You can follow the syslog messages with something like [[COLOR="#FF8C00"]SPLUNK[/COLOR]]("http://www.splunk.com/get?r=header").

[COLOR="#0000FF"]Edit:  I just came across[[COLOR="#FF8C00"]** this interesting thread **[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2164696")that deals with email notification of a failing HDD.[/COLOR]

---

### Post by jefkebazaar2 on 2013-08-07
The weird thing is, when I try a similar setup with Centos 6.4, it just works.

In Centos, I also created the md0, ext4, /boot on both disks.
And where in ubuntu you need to create md1 on both disks, create an encrypted partition on this device and then create an LVM on top, in Centos I created the same md1 on both disks, and then directly created an LVM on top. However, in CentOS, you have the option to encrypt the LVM when creating one on software raid (next to the option also to create encrypted partitions and create unencrypted LVM on top of that). In Ubuntu, I have the impression you can't do this directly from the Ubuntu installer?
When I then unplug either one of the disks in Centos, the OS just keeps booting and working as if nothing happened...

---

### Post by TheFu on 2013-08-07
Everyone here has different experiences, thus we have different opinions.  My experiences have lead me to different answers than what bab1 has learned.

For a home environment, I prefer software RAID over hardware RAID.  It is more flexible, easier to recover, and still provides HA - high availability for more important data.  No RAID is a replacement for backups.  It is about having data available even after a single failure.  That can also be accomplished a number of different ways - duplicate systems without RAID is another way.  In an online business, having failover systems 500+ miles apart is critical, so replicating data between those systems **is** a viable replacement for RAID, but not for good backups.

RAID is about the data, NOT the OS. The data needs to be HA. The OS does not necessarily need to be HA.  If your servers aren't redundant everything, and even if they are, it is better to have 2 different HW platforms to access the data.  Redundant power, redundant buses, redundant NICs, redundant switches, redundant disk controllers, ECC RAM, all cost more than 2x a desktop PCs cost.  For small DBs, local data replication and mirroring are cost effective to get the HA required.  As the DB gets larger, a NAS/SAN is needed with HA storage devices. Lots of ways to accomplish this. Too many to get into here - some are VERY expensive.

In a business environment, where performance is much more important, hardware RAID makes sense. We give up flexibility, since a HW-RAID controller failure can (and does) happen leaving us without any access to that data. In a business, having spares - a spare hw-RAID controller - onsite is critical.  At home, very few people will have a spare $500 RAID controller "just in case."

At home, I've migrated SW-RAID arrays between 3 different servers - each with different disk controllers. You can't do that with HW-RAID or FakeRAID built into a motherboard.

I completely agree with bab1 on monitoring and management of system configurations - though I wouldn't wish Chef or Puppet on my worst enemies.  Ansible is much easier to get your head around as a small shop.  If I were growing beyond 200 OS installs to manage, I'd start looking at Salt.  Ruby just has too much overhead to install on **every system* to be managed.  Small parts of Python are already there. Small parts of perl are already there. Plus Ansible can work with just ssh on the remote system. Managing Puppet keys is often a nightmare.

SMART data on HDDs is usually too late to recognize a disk failure before it happens. That has been my experience. Even so, enabling SMART data for every HDD and running tests weekly to watch the numbers change **is** helpful. The rate of sector failures for each disk is probably the only useful stat from SMART.  Last year, I replaced a complete set of HDDs in RAID just because the disks were 6+ yrs old. No issues, just old.

I've had SW RAID failures. The data was still available. In my case, it was just a loose SATA cable that happened over and over and over for months. Swapped in a 90deg connector to make it stop for the next 5+ yrs. Never had another issue with that enclosure again ... so far. It is still in use today with 8TB inside.  I have a spare PSU for the day that fails. It has been running continuously almost 7 yrs now.

Splunk rocks.  For really small setups, something like **logwatch** might be enough though.

I'm not saying that anyone's opinion is wrong, just that we've come from different backgrounds.
Still, I wouldn't bother with RAID on /boot.

---

### Post by TheFu on 2013-08-07
> **jefkebazaar2 said:**
> The weird thing is, when I try a similar setup with Centos 6.4, it just works.
.

On the exact same hardware?

---

### Post by jefkebazaar2 on 2013-08-07
> **TheFu said:**
> On the exact same hardware?

Yup.

---

### Post by bab1 on 2013-08-07
> **jefkebazaar2 said:**
> The weird thing is, when I try a similar setup with Centos 6.4, it just works.

In Centos, I also created the md0, ext4, /boot on both disks.
And where in ubuntu you need to create md1 on both disks, create an encrypted partition on this device and then create an LVM on top, in Centos I created the same md1 on both disks, and then directly created an LVM on top. However, in CentOS, you have the option to encrypt the LVM when creating one on software raid (next to the option also to create encrypted partitions and create unencrypted LVM on top of that). In Ubuntu, I have the impression you can't do this directly from the Ubuntu installer?
When I then unplug either one of the disks in Centos, the OS just keeps booting and working as if nothing happened...

The end result says there are differences in implementation.  The distros have lots of differences including which kernel is being used and what parameters in the kernel are used.

---

### Post by bab1 on 2013-08-07
> **TheFu said:**
> Everyone here has different experiences, thus we have different opinions.  My experiences have lead me to different answers than what bab1 has learned...

I'm not saying that anyone's opinion is wrong, just that we've come from different backgrounds.
Still, I wouldn't bother with RAID on /boot.

My background is with high availability (including clusters), multi campus, large user base, heterogeneous networks.   

In the end we're not much different in our opinions.  The only major difference is I don't see a need for RAID (hw or sw) other that in a high performance/availability host.  We both agree about backups and host monitoring/management in some way.

But the devil is in the details; isn't it?

---

### Post by jefkebazaar2 on 2013-08-07
Even if you have a look at this ubuntu wiki article:
[https://wiki.ubuntu.com/Ubiquity/AdvancedPartitioningSchemes](https://wiki.ubuntu.com/Ubiquity/AdvancedPartitioningSchemes)

There is a sub-article there titled "Full Disk encryption with LVM on top of RAID1"

What is described there is exactly what I'm doing. 

Also what is described in this youtube movie: [https://www.youtube.com/watch?v=ZZbexPrfnzQ](https://www.youtube.com/watch?v=ZZbexPrfnzQ)
This one is for Debian, but same principle.

So seems to me I'm not the only one who's trying this. But nevertheless, in Ubuntu this does not boot from 1 disk.
And I've tried both Ubuntu 12.04 LTS and 13.04.

And I agree, it's no replacement for backups, which I was already planning on implementing. But I still want this host to survive the crashing of one entire disk and keep running. 
The encryption stuff, well, in my opinion that should be a standard on any device, at home or at work, that is running server functionality.

---

### Post by TheFu on 2013-08-07
> **bab1 said:**
> My background is with high availability (including clusters), multi campus, large user base, heterogeneous networks.   

In the end we're not much different in our opinions.  The only major difference is I don't see a need for RAID (hw or sw) other that in a high performance/availability host.  We both agree about backups and host monitoring/management in some way.

But the devil is in the details; isn't it?

My background is in manned spacecraft GN&C coding, cross-platform development, deployment and support,  application architecture, systems architecture, enterprise architectures, clustering, data replication, around the world business continuity, disaster recovery, SAN design, virtualization,  extremely large internal users base (200K+ users), heterogeneous networks (LAN, WAN, 22k+ users for cellular, non-IP stacks) and heterogeneous servers for a worldwide telco and ISP. 
You've seen my work, I'm absolutely positive.

Details suck, you are correct. So are redundant system deployment schedules that the client delays over higher priority "features" ... until the DB gets corrupted causing a full workday of productivity loss for 22K users. The loss of business and worker wages were huge. My design had already been purchased, we just needed some maintenance windows to implement it in stages in 5 different locations spread around the world. We both probably have interesting stories that shouldn't be shared.

To the OP, I've learned that lots of things are in the docs, manuals and sales people will sell you that just don't work well, if at all.  There is a point where some things just aren't ready for production use. That is the reality of the world.  Fighting these things makes us old and gray before we need to be.  Hopefully, you've opened a bug with Canonical about this.  The reference to CentOS tells me that it is possible, shouldn't be hard to get working.

As to encryption - I encrypt all my portable devices, but not any servers. Perhaps I just don't understand the attack vectors that it protects against?  I'll ask some security pros about this at my next DefCon group meeting on 8/17.  They will probably want to talk about DefCon 2013 [http://www.defcon.org/](http://www.defcon.org/) though.

---

### Post by bab1 on 2013-08-07
> **jefkebazaar2 said:**
> Even if you have a look at this ubuntu wiki article:
[https://wiki.ubuntu.com/Ubiquity/AdvancedPartitioningSchemes](https://wiki.ubuntu.com/Ubiquity/AdvancedPartitioningSchemes)

There is a sub-article there titled "Full Disk encryption with LVM on top of RAID1"

What is described there is exactly what I'm doing.

Also what is described in this youtube movie: [https://www.youtube.com/watch?v=ZZbexPrfnzQ](https://www.youtube.com/watch?v=ZZbexPrfnzQ)
This one is for Debian, but same principle.

Bear in mind that these are not a professional, vetted articles.  Anybody (within the framework of the wiki) is allowed to post their thoughts.  It helps to understand the true meaning of  *[**[COLOR="#800080"]"On the Internet, Nobody Knows You're a Dog" [/COLOR]**]("http://www.unc.edu/depts/jomc/academics/dri/idog.html")*
> 

So seems to me I'm not the only one who's trying this. 

Just because you **can do ** something, doesn't mean you **should do ** something.
> 

But nevertheless, in Ubuntu this does not boot from 1 disk.
And I've tried both Ubuntu 12.04 LTS and 13.04.

And I agree, it's no replacement for backups, which I was already planning on implementing. But I still want this host to survive the crashing of one entire disk and keep running.

The encryption stuff, well, in my opinion that should be a standard on any device, at home or at work, that is running server functionality.
Why do you fee that way?  What does full disk encryption really get you in the end?  This is exactly where I came in to this discussion.  You can state something all you want.  Common consensus and best practice comes *from* just that; common consensus *of* best practices. 

[QUOTE=The fu]
... I've learned that lots of things are in the docs, manuals and sales people will sell you that just don't work well, if at all...
[/QUOTE]

I agree completely!  The engineer really has to use what is truly available or create those abilities when designing the specific device/host/network, etc.  Feature creep is something to avoid.  I find the simplest configuration is the most durable in the long run.  

> As to encryption - I encrypt all my portable devices, but not any servers. Perhaps I just don't understand the attack vectors that it protects against? 
+11 to that!  Think of the unintended consequences to full disk encryption on a server in the machine room of your fortified NOC.  KISS!

---

### Post by jefkebazaar2 on 2013-08-08
Anyways, it appears that this guy had exactly the same issue as I had... in 2010...
[https://answers.launchpad.net/ubuntu/+source/cryptsetup/+question/130779](https://answers.launchpad.net/ubuntu/+source/cryptsetup/+question/130779)

Basically, a bug already reported 3 years ago and still not fixed. He also eventually switched to Centos.
Have to admit, I hear this also from other colleagues and from own experience that CentOS often does it better than ubuntu in more enterprise-focussed features... Too bad for this kind of silly stuff, or Ubuntu might indeed be ready to take on CentOS in the enterprise.

---

### Post by TheFu on 2013-08-08
CentOS is a binary compatible version of Redhat Enterprise Linux - with all the fixes provided by Redhat.  People pay between $700 and $2000 per license for RHEL. I don't want to downplay what the CentOS guys do - getting source code and compiling everything into a distro is tough.  That is what they do.

In the USA, enterprises buy RHEL for most of their systems. It is the ISPs who use CentOS and perhaps the guys in labs inside the enterprises too.   Plus college students who realize that RHEL jobs pay more than most Debian jobs.

Ubuntu is not really used much inside enterprises. Canonical appears to be concentrating on desktop and phones. I'd guess they are following the Apple model - which doesn't include servers.  In May, I spoke to a LUG in South Africa. I always ask which distro people use - Ubuntu for most. No Redhat or CentOS at all.  At my three home LUGs in Georgia - it is 90% RHEL for servers and 60% Ubuntu for desktops.  Local colleges teach using CentOS - which makes perfect sense here.

Anyway - different goals from the different distros isn't anything new.  I love the diversity even if the current implementation of Unity is just nasty, IMHO.  I get that some people really like it.  None of this gets you to a working system running the way that you think it should. Sounds like Ubuntu is not the solution.

---

### Post by jefkebazaar2 on 2013-08-08
Yes of course, I realise that CentOS is in effect "just a recompile of Redhat with the branding removed", but still, it does mean you get all the quality, testing and coding of a tested, proven, enterprise-grade OS with it. Your software is older, your kernel is older, but so much more stable and thoroughly tested.

But then again, if you keep in mind articles likes this: [http://readwrite.com/2012/03/15/reality-check-on-ubuntus-enter](http://readwrite.com/2012/03/15/reality-check-on-ubuntus-enter)
In my opinion, Mark Shuttleworth shouldn't be making bold claims as that Ubuntu is booming as an enterprise OS :-)

Now, on the other hand, you're right, I do use Ubuntu on my client system and there, it indeed just rocks. The hardware support is so much better than debian or other distro's in my opinion, and the availability of bleeding/cutting edge versions of software in apt-repositories is just great. But of course on a client you have other expectations than on a server system.

I was just curious to see how mature Ubuntu was from a server perspective, but I think I will stick to CentOS for the backend and Ubuntu for my frontend.

I already heard that RHEL is the dominant linux server OS on the other side of the ocean, but I think in Europe it also shouldn't be underestimated.
I've seen more RHEL installs at enterprises over here than Suse or other flavors.

---

