---
title: "Missing CPU"
date: 2010-07-20
forum: Virtualisation
---

### Post by GregCPX on 2010-07-20
Hello all,

hopefully I am not posting a question that has already been answered, but I did search and did not see anything, so here is my problem.

I have installed VMware Server 2.0.2 on the latest version of ubuntu.  I got everything installed and I am also working around a bug w/firefox and the console.  I am able to do everything I need (so far), but something concerns me a lot.

I have 2 PROCS, 4 core Xeon processor.  When I installed and tested ESXi, it showed the correct cores/procs, but when I install it on ubuntu with VMWare Server 2, it only shows 1 proc, 4 cores. 

Now, all 8 procs show up under /proc/cpuinfo.  They are also listed in top.  I do have VT turned on (since I was able to see all procs and install a 64 bit guest under ESXi), so I am at a loss on how I lost an entire CPU?

Any help/suggestions????
I'd prefer to keep the ubuntu configuration (much more flexible) but this is a deal breaker if I can't see/use more of the cores I have.

---

### Post by kemra on 2010-07-21
Sorry but your setup sound a little confusing, from what I understand you have an Ubuntu servers, with VMWare Server software installed and you are installing ESXi as a Virtual machine suing VMWare server yes?

Although that is a little odd, it might be something to do with how you configured the ESXi Virtual machine when you set it up. During set-up you should have been able to specify the amount of cpu's it has access to from the host machine. try looking for a setting like this.

---

### Post by TheFu on 2010-07-21
Does VMware Server have a limitation around the number of cores or physical CPUs that can be used? I'd check that, since 2 seems like a limitation for their non-professional solutions. If you add more VMs, I'd think those would be able to use the other vCPUs, but I don't know since I stopped using VMware Server about 3 yrs ago.  A quick google found this thread [http://communities.vmware.com/thread/184715](http://communities.vmware.com/thread/184715) where someone says 2 is the limitation for the free "VMware Server".

---

### Post by kemra on 2010-07-22
In my opinion at least at it certainly is marketed as such VMWare Server is most definately a professional solution. And VMWare Server is capable of supporting as many CPUs as the HOST OS in this case Ubuntu, so that shouldn't be a problem. Also as far as I know there is no none-free version, the only things you would pay for are the vSphere Managment or support from VMWare. If any that is wrong pleas epoint it out as I'd like to know.

---

### Post by GregCPX on 2010-07-22
> **kemra said:**
> Sorry but your setup sound a little confusing, from what I understand you have an Ubuntu servers, with VMWare Server software installed and you are installing ESXi as a Virtual machine suing VMWare server yes?
 
Although that is a little odd, it might be something to do with how you configured the ESXi Virtual machine when you set it up. During set-up you should have been able to specify the amount of cpu's it has access to from the host machine. try looking for a setting like this.
 
Sorry, I guess I did not make things as clear as I should...
I was trying to say, I was using ESXI hypervisor on the same equipment and everything worked great (w/the exception of no USB support). 
 
I then turned around, and nuked that install, installed ubuntu and VMServer 2.0 and was trying out that configuration.  
 
The configration w/the hypervisor showed all CPU's and cores, the VMServer 2.0 running on Ubuntu does not.
I was trying to make the point that indeed, VT is turned on since the hypervisor ESXi configuration showed it working correctly and I was able to install a 64bit version of Windows 2008. Without VT turned on, you can not install 64bit windows 2008.
 
I hope that makes a bit more sense?
 
I have sense destoryed the Ubuntu version and I am now using Windows 2008 as the base O/S with VMServer 2.0 on top.
 
I am attempting to find the right combo that meets my VM needs, but also gives usb support.
 
Cheers

---

### Post by GregCPX on 2010-07-22
> **kemra said:**
> In my opinion at least at it certainly is marketed as such VMWare Server is most definately a professional solution. And VMWare Server is capable of supporting as many CPUs as the HOST OS in this case Ubuntu, so that shouldn't be a problem. Also as far as I know there is no none-free version, the only things you would pay for are the vSphere Managment or support from VMWare. If any that is wrong pleas epoint it out as I'd like to know.
 
I found some info that other folks are having the same issues, but VMWare is not providing much insight into the issue.
 
Apparently you have to edit of the .vmx of the guest and add the following (or something similar) to tell it how many procs to use. Example:
 
Guest 1:
processor0.use = TRUE
processor1.use = TRUE
processor2.use = FALSE
processor3.use = FALSE
processor4.use = FALSE
processor5.use = FALSE
processor6.use = FALSE
processor7.use = FALSE
 
Guest 2:
processor0.use = FALSE
processor1.use = FALSE
processor2.use = TRUE
processor3.use = TRUE
processor4.use = FALSE
processor5.use = FALSE
processor6.use = FALSE
processor7.use = FALSE
 
...
...
...
 
Seems like a clunky fix.

---

### Post by TheFu on 2010-07-23
> **kemra said:**
> In my opinion at least at it certainly is marketed as such VMWare Server is most definately a professional solution. And VMWare Server is capable of supporting as many CPUs as the HOST OS in this case Ubuntu, so that shouldn't be a problem. Also as far as I know there is no none-free version, the only things you would pay for are the vSphere Managment or support from VMWare. If any that is wrong pleas epoint it out as I'd like to know.

VMware makes lots of virtualization software. I think you are confusing the free "Server" version with ESXi or ESX, which are their main commercial virtual server products.

Here's quick list of VMware virtualization software.

[LIST]
[*]VMware Player
[*]VMware Server
[*]VMware Fusion (Mac)
[*]VMware Workstation (PC)
[*]VMware ESXi
[*]VMware ESX
[/LIST]
Each of these are called hypervisors, some are bare metal (no OS allowed) and other are more for desktop use and require an OS like Windows or Linux. You can only have 1 of them loaded on a PC at a time (though you can load them into different partitions and dual/quad/octal boot).

Player and Server and ESXi can be used without cost for most individuals. There are lots of other VMware-branded virtualization tools, but those are usually connected to the ESX(i) products. vSphere is like that and there are at least 5 other ESX-connected VMware software.

BTW, If you visit the VMware web site and read, you will learn lots. Wikipedia has a nice chart too [http://en.wikipedia.org/wiki/VMware#Products](http://en.wikipedia.org/wiki/VMware#Products)

It is best when discussing "vmware" here to be extremely specific on the actual software being used so nobody will assume it.

---

### Post by GregCPX on 2010-07-23
> **TheFu said:**
> 
...
 
It is best when discussing "vmware" here to be extremely specific on the actual software being used so nobody will assume it.
 
Actually, going back and reading my original post, I was very specific and very clear.
 
No matter, I found that ubuntu with Server 2.0 slow and very very clunky. Thus far, my test indicate that Server 2.0 on top of Windows Server is working much better.  
I'm a big fan of Linux, but this implmentation of Server and Linux is not working out well.

---

