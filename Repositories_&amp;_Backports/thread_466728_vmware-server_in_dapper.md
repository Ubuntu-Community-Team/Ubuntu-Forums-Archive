---
title: "vmware-server in dapper?"
date: 2007-06-07
forum: Repositories &amp; Backports
---

### Post by Betelgeuse on 2007-06-07
Hi,

I'm planning to upgrade my server machine, it's currently running Windows 2000 server and vmware server hosting 4 virtual servers. Now I want to upgrdae the OS to a better os, so I choose Ubuntu Server Edition. I want to install the LTS version. I'm running Kubuntu 7.07 on my desktop machine and I installed vmware-server from the canonican repositories. Now I want to know if I can install vmware-server on ubuntu 6.06 server edition like I installed in feisty?
I've used this command to install vmware-server in feisty :
sudo apt-get install vmware-server

I had to add commercial repositories to make this happen, so what repository should I add for ubuntu 6.06? I can install it from tha original tar.gz file but I want to install it with apt because it makes upgrades easier...

---

### Post by zvacet on 2007-06-07
I thiink that Feisty is first Ubuntu version with vmware-server in repos,so you have to download it from vmware site.Somebody,correct me if I´m wrong.

---

### Post by Chayak on 2007-06-07
That's correct, the version in the repository is for 7.04.  You need to download the .tar.gz from VMware and run the install script though be sure to install the build-essential packages before doing so as it will likely have to build a module when it configures (I've never seen it not build it)

You'll be fine for normal updates though after a kernel update you'll need to run vmware-config.pl and rebuild the module for the new kernel.

---

### Post by Betelgeuse on 2007-06-07
So, I can not install vmware-server by running command :
sudo apt-get install vmware-server
on 6.06. I can install it from original tar.gz file but This server is co-located in a datacenter of an ISP and I can only access it from ssh. So, the updates should be easy enogh. it'll run bind dns service for some 10 domains and 3 virtual machines inside. Should I go for the 7.04 server edition or should I stick with the LTS version? This server should run 24/7 and it'll be a real shame for me if there is any downtime. 
Help me decide a version. I'm considering 6.06 LTS because I think it's more secure but I'm a nooob in linux so I may be wrong.

---

### Post by ericdegen on 2007-06-08
I'm looking to do the same thing, and in the process of building a 6.06 LTS 64  bit server. Other suggested I go with the LTS offering rather then the newer Feisty (which I'm using on workstations.) 

But I want to run a 64-bit version of VMserver - is the support much better on Feisty then Dapper?

---

### Post by Betelgeuse on 2007-06-10
> **ericdegen said:**
> I'm looking to do the same thing, and in the process of building a 6.06 LTS 64  bit server. Other suggested I go with the LTS offering rather then the newer Feisty (which I'm using on workstations.) 

But I want to run a 64-bit version of VMserver - is the support much better on Feisty then Dapper?

I do not think there is any 64 bit version of vmware server. it's a 32 bit program but it can run 64 bit guest machines. 

For now, I'll consider using any 64bit software because 64 bit supports more than 4GB of RAM. I have 3 GB of RAM, so I'll stick with 32 bit software..

---

### Post by ericdegen on 2007-06-11
Well it worked out good for me. I built the 6.06 LTS server (64 bit) and then installed VMware server 1.03 and I'm able to run Windows x64 Server VMs inside - exactly what I was looking to do.

I'm very pleased with the results of this dev box I built. Tomorrow I plan on building and putting live a production version of the same hosting multiple Windows Servers I'm migrating with the VMware converter app.

---

