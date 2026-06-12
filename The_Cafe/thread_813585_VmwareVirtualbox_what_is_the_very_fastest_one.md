---
title: "Vmware/Virtualbox: what is the very fastest one ?"
date: 2008-05-30
forum: The Cafe
---

### Post by frenchn00b on 2008-05-30
[SIZE="3"][COLOR="Red"][B]If you never tried Vmware, please do not vote
(and if you like Virtualbox without testing Vmware, please do not vote !) [/B][/COLOR][/SIZE]
 
Wanna emulate windows 98SE or 2000 or XP ,
(Vista ok, let's forget that word for the moment ;) )

Vmware/Virtualbox: What is the very fastest one ?

---

### Post by Lord Xeb on 2008-05-30
VirtualBox is rather fast, VMware is great. Either one is a good choice.

---

### Post by frenchn00b on 2008-05-30
> **Lord Xeb said:**
> VirtualBox is rather fast, VMware is great. Either one is a good choice.

We installed the last VMware and it looks like it is much faster than Virtualbox. That's our experience. Some installed Vmware, the last too ?

---

### Post by mustang on 2008-05-31
VirtualBox is faster than the free edition of VMWare. I've heard (and perhaps someone can confirm this) that the non-free version of VMWare is quite a bit faster.

---

### Post by phrostbyte on 2008-05-31
This is a flawed comparison because in terms of virtualization speed, the performance between them should be roughly equal. Virtualization is very much par to native performance with some caveats like video.

---

### Post by bufsabre666 on 2008-05-31
when i finally got vm ware working, it was significantly faster than virtual box, although i like virtual box more

---

### Post by jrusso2 on 2008-05-31
Yes you really need the vmware workstation which you pay for to get the fast one.

That being said I have heard Parallels is even faster.

---

### Post by popch on 2008-05-31
Restarting a suspended VM is very much faster in VirtualBox than in VMWare Workstation. Otherwise, I did not notice a marked difference in speed. However, I do not use applications in VMs where sheer speed is of the essence.

---

### Post by frenchn00b on 2008-06-01
After further trying ... it is very confirmed Virtualbox is slower than Vmware !! Virtualbox can also be sluggish time to time :)
pity

---

### Post by zachtib on 2008-06-01
I'm using VMware 6.5 beta, and it's great, even with the DEBUG mode turned on.

Plus, the new beta adds support for Unity Mode and DirectX 9

---

### Post by frenchn00b on 2008-06-01
from : [http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html](http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html)
(bit old)

> Benchmark
I used the Windows tool "FreshDiagnose" from FreshDevices to benchmark the two systems. To ensure that nothing falsifies the results, I killed all running applications on the hostsystem and rebooted the virtual machine.
	VirtualBox	Qemu	VMware-player	
CPU:				
DhryStone ALU (MDIPS)	5,716 	5,988 	5,711	
WhetStone FPU (MWIPS) 	4,189 	4,649 	4,401	
Multimedia Benchmark	2,152 	268 	2,071	
Memory:				
Integer Assignment 	13,074 	13,640 	12,502	
Real Assignment	13,782 	14,270 	14,176	
Integer Split 	18,027 	19,554 	18,885	
Real Split 	17,555 	18,682 	18,407	
GFX:				
Circles (Circles/s) 	2,415 	1,997 	n/a	
Rectangles (Rectangles)	3,123 	6,548 	n/a
Texts (Chars/s) 	62,551 	35,010 	n/a	
Harddisk:				
Write Speed (MB/s)	8.65 	12.44 	6.07	
Read Speed (MB/s)	14.65 	23.22 	4.68	
Network:				
Down Speed (MB/s)	4.9 	2 	5.3	
Up Speed (MB/s)	5.2 	2.3 	4.1	


Conclusions
VMware-Player does not seem to be that good and no real competitor to Virtualbox or Qemu after this benchmark and the Windows system running in the VMware-player didn't feel very smooth at all. That might be different, when the guest drivers are installed, but seems like they are only available with the commercial product.
Qemu and Virtualbox work great, Virtualbox feels much more smooth, but this might be mainly related to the "Guest Addition" drivers what makes the virtual machine feel like it would run on the physical hardware, e.g. the mouse doesn't lag like it does for Qemu. 
Qemu is little bit faster in writing and reading files from/to the virtual harddisk, but the speed of the simulated network communication is very slow. Thus the communication between host and guest is very slow. A big advantage of Qemu is the support of multiple target architectures like powerpc, arm, mipsel and many more which are not supported by VirtualBox.

In summary:
VMware-Player did not meet the expectations I have to a professional product and I hope the commercial editions have a working installation process and make the guest operating system run more smooth.
I used Qemu wiht kqemu to run Windows as a virtual machine for a very long time period, but VirtualBox seems to be little bit better for this use case and the kernelmodule is also GPL, so I think it is time to switch.

But nevertheless the Qemu team and Innotek made really good work with those two projects. Thanks!

---

### Post by popch on 2008-06-01
> **frenchn00b said:**
> from : [http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html](http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html)

> That might be different, when the guest drivers are installed, but seems like they are only available with the commercial product.

(bit old)

Testing VMWare Player without the VMWare Tools ruins the whole benchmark. The tools are available in the player, and running the player without the tools is a bit futile.

True, installing the Tools in a Linux guest might be a little more complicated than for other VM products. Installing them in Windows is straightforward.

---

### Post by frenchn00b on 2008-06-01
> **popch said:**
> Testing VMWare Player without the VMWare Tools ruins the whole benchmark.   Indeed ! :)  VMware is a hit! Nothing to say.

---

### Post by henryfranz2005 on 2009-10-04
hi I would try virtualbox on HP DV-1000 1GB ram centrino core-solo. I hope it would run. :)

---

### Post by henryfranz2005 on 2009-10-04
Yeah, it's now working. Well and it's fast. Nice Virtual Box. Though I'll try vmware next time

---

### Post by frenchn00b on 2009-10-18
actually guys, the reply is QEMU

QEMU is faster than vmware and virtualbox ;) Kqemu does not make it far faster. QEMU is the best, and is in linux repositories.

[http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html](http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html)

---

