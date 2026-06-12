---
title: "Freeze with Ubuntu guest OS on vmware"
date: 2008-08-06
forum: Virtualisation
---

### Post by yaznar on 2008-08-06
Hi,

i have some trouble with Ubuntu and vmware.

vmware version are the last infrastructure foundation on dual xeon L5420 with 16Go of memory.

I have install Ubuntu 8.04.1 with PXE.

I don't know why, but the guest OS freeze. And only when I have more than one processor.

For exemple, it's can freeze during the PXE install (and use 100% of the 8 core) or when I try to compile an application.

I have read on the VMWare community that the Ubuntu kernel have some difficulty with multi-processor and vmware.

Do know you a solution ?

---

### Post by thomasbeagle on 2008-08-07
No help here, but confirming we're seeing something similar with Ubuntu 8.04 (kernel 2.6.24-19-server SMP) running on VMWare ESX Server 3i (3.5.0, 103909).

We've now switched to allocating it only one CPU and ... well, it hasn't died yet. :-)

---

### Post by yaznar on 2008-08-08
Good, I'm not the only one who have this problem :)

Do you know if this problem are from Ubuntu kernel or vmware ?

Because I need to be able to activate and use SMP on vmware without freeze on Ubuntu. So, if it's a problem with the Ubuntu Kernel I can try to compile a new kernel. But if not, i don't know ...

---

### Post by Technoviking on 2008-08-27
Filed bug report, please comfirm.
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/261937](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/261937)

---

### Post by SunF1re on 2008-09-03
We do have similar issues when running Ubuntu 8.04.1 64bit Server as a guest OS on a VMware ESXi 3.5 U2 server.
The Ubuntu guest running in a VM with 2 or 4 CPUs consumes 100% out of the blue and without a restart of the VM it can't be recovered. Setting the guest OS to 1 CPU only resolves the issue.

EDIT:
Right after posting this I found a possible solution for this.... as usual. ;)
Try adding clocksource=acpi_pm to your kernel boot options. I am not 100% sure if this will really eliminate the problem but my system has yet to crash since I set it.

---

### Post by bexamous on 2008-09-09
Anyone confirm this fix?  Going to start some images with 4 CPUs and see what happens.

---

### Post by Kolipoki on 2008-09-09
As of August 13, VMware released another build for ESXi 3.5. The _[release notes]("http://www.vmware.com/support/vi3/doc/vi3_esx3i_i_35u2_vc25u2_rel_notes.html")_ (taken from VMware's site) include the following:
> Note: An issue has been discovered by many VMware customers and partners with ESX Update 2 (build number 103908) and ESXi 3.5 Update 2 (build number 103909) where Virtual Machines fail to power on or VMotion successfully. This problem began to occur on August 12, 2008 for customers that had upgraded to ESX 3.5 Update 2. The problem is caused by a beta release product expiration that was mistakenly left enabled for the release build. New installations of build number 110271 of ESX Server 3i version 3.5 Update 2 Installable will not experience this issue. For more information, see KB 1006716.
So go grab the fix.

---

### Post by bexamous on 2008-09-10
That update is not related, at least for me.  110271 did not fix the problem.

I did however start two images yesterday using 'clocksource=acpi_pm' and they're both running this morning.  I still got my fingers crossed.  One image is running HPL/Linpack and the other is doing regular work load.  I'll start some more at the end of the day to run overnight.

---

### Post by bexamous on 2008-09-11
For anyone who sees this topic in the future 'clocksource=acpi_pm' almost certainly resolves the lockups.

Previously I had systems locking up in 2-30 minutes and now its been two days without any lockups.  This is with 110271 on two E5410s and 12GB RAM.

SunF1re owns.

---

### Post by bobdob on 2008-09-18
can't believe it, just found this entry, 
We have 46 Ubuntu VMs on ESX 3.5U2, randomly hanging, being working on this issue the last two weeks. 8.04.1 machines with one CPU dont hang, going to test clocksource=acpi_pm on a few of them with 2 and 4xCPUs

as a side note 8.04.1 is not actually officially supported by VMware on ESX 3.5U2 only ESX 3.0.3 with a patch. So no matter how loud you scream at VMware, there not interested..

---

### Post by MajorPeabody on 2008-09-18
> **bobdob said:**
> ..snip..
as a side note 8.04.1 is not actually officially supported by VMware on ESX 3.5U2 only ESX 3.0.3 with a patch. So no matter how loud you scream at VMware, there not interested..

I believe you are mistaken. From [http://www.vmware.com/pdf/GuestOS_guide.pdf](http://www.vmware.com/pdf/GuestOS_guide.pdf) (Page 233) - 
Server Edition – ESX 3.0.3 (requires Patch ESX303&#8208;200808405&#8208;BG), **3.5 U2**
Desktop Edition – ESX 3.0.3 (requires Patch ESX303&#8208;200808405&#8208;BG), **3.5 U2**
Server Edition JeOS – ESX 3.0.3 (requires Patch ESX303&#8208;200808405&#8208;BG), **3.5 U2**
Update Support
Ubuntu 8.04.1 LTS – ESX 3.0.3 (requires Patch ESX303&#8208;200808405&#8208;BG)
Additional Support
SMP – full support on ESX 3.0.3, **ESX 3.5 U2**
VMI – full support on **ESX 3.5 U2**

---

### Post by r_e_d_b_a_r_o_n on 2008-09-23
I am using Ubuntu Server 8.04.1 on ESX 3.5U2 with 2 cpus for month or more with heavy load without freezes but it freezes randomly when I enable VMI for Ubuntu virual machine. 
I forgot to say that ubuntu changed clocksource to acpi_pm without my interaction once and without reboot, I don't remember exact message but it wrote something in kernel.log that it changed clocksource to acpi_pm.

---

### Post by karrots on 2008-09-24
I have been working with VMWare tech support they told me Ubuntu 8.04.1 is supported and even recommended VMI. We changed the clock source to the acpi_pm which seemed to make things more stable but didn't fix the problem.

We have one VM that would lock up like clock work when running the vmi-timer. After changing to the acpi_pm it went a week with out locking up.

All of my machines are single CPU VM's running ESX 3.5 update 2. One thing the first tech thought was that the problem was introduced in update 2. Does anyone else have any insight into update 2 causing the problem?

---

### Post by bobdob on 2008-09-25
> **MajorPeabody said:**
> I believe you are mistaken. From [http://www.vmware.com/pdf/GuestOS_guide.pdf](http://www.vmware.com/pdf/GuestOS_guide.pdf) (Page 233)  
Server Edition – ESX 3.0.3 (requires Patch ESX303&#8208;200808405&#8208;BG), **3.5 U2**


Actually if you all look at the documentation for ESX it says 8.04 LTS and not 8.04.1 LTS, there is a slight difference. Only 3.0.3 supports 8.04.1 and this is what VMware have said

We still have machines hanging, even with the 'clocksource=acpi_pm' enabled, just not as often. 
Were either setting the machines to use 1 CPU or disabling VMI (paravirtualization) feature from the VM's advanced options which seems to sort the issue. 

Our current train of thought is that it is VMI/Linux kernel issue.

---

### Post by Svenstaro on 2008-10-04
To update you guys:

Vmware Server forums thread about this issue: [http://communities.vmware.com/message/1066922#1066922](http://communities.vmware.com/message/1066922#1066922)

And don't worry, it's fixed in Intrepid :)

---

### Post by karrots on 2008-10-07
> **Svenstaro said:**
> To update you guys:

Vmware Server forums thread about this issue: [http://communities.vmware.com/message/1066922#1066922](http://communities.vmware.com/message/1066922#1066922)

And don't worry, it's fixed in Intrepid :)

The VMWare KB article mentioned in this thread seems to only apply to the tsc clock. My VM's that were locking up were using the vmi-clock. The acpi_pm clock mentioned in the article had a similar effect as Bobdob's vm's they became more stable but still crashed. One thing I am seeing that no one else seems to have mentioned is Virtual Infrastructure seems to loose control of the VM. I can't power off or restart the VM's once they lockup. I have to reboot the ESX host before they are controllable again.

One other note with the vmi-clock I can crash the Guest VM on demand just by doing something CPU intensive like untaring the Linux Kernel. 

To work around the problem I have done as Bobdob and turned off VMI in the VM until the problem shows as being fixed. 

The problem seems to only be with the newer kernels (e.g.2.6.24). I have some Suse Enterprise 10 servers running a VMI kernel version 2.6.16.60-0.29 (Novell backported VMI to the 2.6.16 kernel). Which run fine with 1 CPU and 2 CPU's.

---

### Post by r_e_d_b_a_r_o_n on 2008-10-09
> **karrots said:**
> The VMWare KB article mentioned in this thread seems to only apply to the tsc clock. My VM's that were locking up were using the vmi-clock. The acpi_pm clock mentioned in the article had a similar effect as Bobdob's vm's they became more stable but still crashed. One thing I am seeing that no one else seems to have mentioned is Virtual Infrastructure seems to loose control of the VM. I can't power off or restart the VM's once they lockup. I have to reboot the ESX host before they are controllable again.

One other note with the vmi-clock I can crash the Guest VM on demand just by doing something CPU intensive like untaring the Linux Kernel. 

To work around the problem I have done as Bobdob and turned off VMI in the VM until the problem shows as being fixed. 

The problem seems to only be with the newer kernels (e.g.2.6.24). I have some Suse Enterprise 10 servers running a VMI kernel version 2.6.16.60-0.29 (Novell backported VMI to the 2.6.16 kernel). Which run fine with 1 CPU and 2 CPU's.

Same to me when, when I enable VMI it freezes randomly and I can't even shutdown the vm, I use vm-support -X in ESX console to turn off the vm without restarting esx.

---

### Post by bobdob on 2008-10-15
our VM Guests could'nt be shutdown either, attempting to restart from VI hangs at 95% so we use subtle commands from the service console "ps -axwww | grep dead-ubuntu-serverxyz.vmx" to find the PID 
then kill -9 $PID - VM-support -X works as well, but takes too long :)

Anybody know when 8.04.2 is due out ?, and shouldn't Ubuntu fix this ? seeing as they have VMI in the kernel which is now useless on dual CPU machines. 
According to that VMware KB, Redhat have provided a fix for RHEL 5

---

### Post by r_e_d_b_a_r_o_n on 2008-10-20
New kenel is avalable for Ubuntu 8.04.1 "Linux ubuntu 2.6.24-21-server", maybe the problem is solved there, can anyone recheck?

---

### Post by karrots on 2008-10-20
> **r_e_d_b_a_r_o_n said:**
> New kenel is avalable for Ubuntu 8.04.1 "Linux ubuntu 2.6.24-21-server", maybe the problem is solved there, can anyone recheck?

I will recheck hopefully later today. I can make the VM's lock on demand by untaring the Linux kernel tarball.

Looking through the change log I didn't see anything that jumped out. Other than something for the tsc clock to stop it from going backwards.

---

### Post by r_e_d_b_a_r_o_n on 2008-10-21
> **karrots said:**
> I will recheck hopefully later today. I can make the VM's lock on demand by untaring the Linux kernel tarball.

Looking through the change log I didn't see anything that jumped out. Other than something for the tsc clock to stop it from going backwards.

Updated today. Same problem :(

---

### Post by bobdob on 2008-11-07
Ubuntu 8.04.1 now officially supported by VMware with ESX 3.5 update 3. [http://www.yellow-bricks.com/2008/11/07/vmware-esx-35-update-3/](http://www.yellow-bricks.com/2008/11/07/vmware-esx-35-update-3/)

---

### Post by ScottEChapman on 2009-03-01
So... Can anyone confirm that this problem has been resolved and Ubuntu guests can take advantage of VMI performance improvements?

---

### Post by bobdob on 2009-03-11
Applied a bunch of ESX host patches the other day and 
upgraded VM Guest tools to version 143128, one or two machines that used to 100% cpu hang with VMI are not doing it now, not very scientific but continuing to monitor.

Its basically a lottery with Ubuntu 8.04.x and ESX :) 

Bob

---

### Post by ScottEChapman on 2009-03-12
I am pretty sure all my stuff it up to date (ESXi, vmtools, and ubuntu) and I had it hang just as quickly...

---

### Post by ScottEChapman on 2009-03-16
I am assuming this is a bug with Ubuntu and not ESXi.

Is anyone working on this??

---

### Post by bobdob on 2009-03-16
hmm..looks like my guest machines are still hanging, 
false alarm on the upgrade fixing it.

> Is anyone working on this?? 
That is a good question..probably not, but its very hard to diagnose.

Bob

---

### Post by RoadRunnr on 2009-04-09
> **bobdob said:**
> our VM Guests could'nt be shutdown either, attempting to restart from VI hangs at 95% so we use subtle commands from the service console "ps -axwww | grep dead-ubuntu-serverxyz.vmx" to find the PID 
then kill -9 $PID - VM-support -X works as well, but takes too long :)


got the same problem, it seems the normal -server kernel do not trigger this problem, only the -virtual ones crash.
Reproducing it is quite simple for me, just running bonnie will trash the server in seconds.

I say this is a VMware bug, a hosted kernel, should not be able to influence the ESX server like this.

I opened a new VMTN thread: [http://communities.vmware.com//thread/204060?tstart=0](http://communities.vmware.com//thread/204060?tstart=0)

---

### Post by nardusg on 2009-04-21
Got hte same issue :( I did notice in "top" that the cpu percentage sometimes go over 100% :( Is that normal or that just n' way "top" deals with esxi ?

Just to let you guys now there is another fix seeker out there....

---

### Post by brendanmc on 2009-05-31
Mine is an experimental setup... but may add some further insight. 

Host machine is a dual q xeon with ubuntu 9.04 server as the host and vmware server 2.0.x. 

I have lock ups in _all_ guest machines including win xp pro whenever I allocate more than one CPU. This continues until I successfully install vmware tools in the guest.

Am about to try clocksource=acpi_pm on the host to see if it improves.

Brendan Mc

---

