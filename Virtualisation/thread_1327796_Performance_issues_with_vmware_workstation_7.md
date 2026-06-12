---
title: "Performance issues with vmware workstation 7"
date: 2009-11-15
forum: Virtualisation
---

### Post by maflynn on 2009-11-15
Anyone notice any performance issues with vmware workstation 7 on ubuntu 9.10

I'm running the 32bit version of ubuntu/vmware and running a guest session was painfully slow.  I tried dedicating both cores hoping that would alleviate the problem but no such luck.

Anyone else experience this?  I'm on the 30 day trial and I'm trying to determine whether I want to buy workstation 7 or stick with osx/vmware fusion which doesn't seems to be suffering from the performance issues

---

### Post by fjgaude on 2009-11-15
Try just one core and see what happens.

---

### Post by maflynn on 2009-11-15
I had done that as well, no real difference. Very poor performance.

---

### Post by darco on 2009-11-15
I use 2 processors and 1 core...runs perfect
Running a q600 quad core

*edit*..oops I actually have 1 processor and 2 cores setup in vmware

darco

---

### Post by fjgaude on 2009-11-16
I too have dual-core but only use one with vmware Player 3.0 and Server 1.0.9. With two cores the performance is terrible!

---

### Post by brunjes on 2009-11-20
> **fjgaude said:**
> I too have dual-core but only use one with vmware Player 3.0 and Server 1.0.9. With two cores the performance is terrible!

I also have a dual core system. I run Ubuntu 9.10 64-bit as the host OS. If I try to create a Windows XP (same with Windows 7 and Windows Server 2008 ) system with 2 virtual cpus in it (using either 32-bit Windows or 64-bit Windows), it takes minutes (literally) to do things that normally require a second or two. If I change nothing but the number of virtual cpus from two to 1, performance is suddenly normal for that guest (after rebooting the guest OS of course).

I have 8 GB of RAM on my system and the VM only has 1 GB of RAM, so that's not the issue.

Is this a bug in VMware Workstation 7 (Linux version)?  If I try to set up a dual cpu Ubuntu VM, no such issue is seen. Performance is normal whether the guest Ubuntu VM is 32-bit or 64-bit.


Roy

---

### Post by fjgaude on 2009-11-20
Bug, who knows! All I can say is 9.10 was a drastic move toward a better, quicker OS, and it will take time for all the apps and so forth to make the changes necessary for smooth operation.

---

### Post by binabik80 on 2009-11-30
While I am not on 9.10 (still on 9.04) I am running VMWare Workstation 7 with three VMs (two always running) on a Quad Core with 8 GB of RAM and the performance is quite good about as good as the dedicated server was.

Each VM is setup with one CPU and 2 GB of RAM per VM.

---

### Post by fjgaude on 2009-11-30
It seems for many, one core is the way to go... I run four VMs, each with one core, and as it is said, each is as fast as native. I only use 512 MB for each, even the WinXP one. I'm a happy camper!

---

### Post by jtliii on 2010-01-12
Changing to a single processor and a single core seems to be the answer. I have tried multiple VM's since upgrading to Workstation 7 and all have been extremely poor performers. I have a dual quad core processor host so I have always added at least two cores to my VM's (if they can benefit from it). After reading this thread I reduced my most recent Windows 7 VM from one CPU and four cores to one CPU and one core and it is zipping along just fine now.  This must be an issue with Workstation 7 because I had the same issue with a Windows XP VM I was using (and which was performing just fine) when I upgraded to Workstation 7. After the upgrade performance on that VM tanked. I then built up a Windows 7 VM and that hasn't performed any better until I reduced it to a single CPU, single core configuration.

---

### Post by HermanAB on 2010-01-13
Howdy,

Did you turn the VMcrapware off and installed Vmware Tools?

Disable background snapshots.  Disable auto CDROM detection (turn it on manually when you need it). Disable the floppy disk.  Install VMware Tools. Then you should be OK.

---

### Post by jtliii on 2010-01-19
Upon further reflection I believe this is an issue with Ubuntu 9.10 and Workstation 7. I have been trying to remember the exact sequence of upgrades I did and I am pretty sure that with Ubuntu 9.04 and Ubuntu 9.10, Workstation 6 will work just fine with multiple cores and I am pretty sure I have read of others using 9.04, Workstation 7 and multiple cores without an issue.

---

### Post by fjgaude on 2010-01-19
Running VMware Player 3.0 under Ubuntu 9.10 and after installing Ubuntu 10.4 Alpha 2 as a guest I wasn't able to Install Tools. This happened under host Ubuntu 9.04 also. I don't think the tools work for either 9.10 or 10.4 as guest.

Does anyone have an answer for this?

---

### Post by darco on 2010-01-20
I cant speak for Player but WS7 tools work fine in my Lucid guest.

---

### Post by grenyg on 2010-02-01
I am having the same performance problems here. Was running VMware Workstation 6.5.3 on 9.04 and everything was fine.

Then I first installed 6.5.3 on 9.10 and peformance was terrible, cpu at 100% most of the time. Then tried 7.01 on 9.10 and same terrible performance. Something is wrong!

Edit:
Tried changing from 2 processors/1 core to 1 processor/two cores => Still slow.
Tried changing to 1 processor/1 core => And indeed now the VM is running fast!

Feels like there is a threading or race issue with more then one cpu/core...

---

### Post by fjgaude on 2010-02-01
"Feels like there is a threading or race issue with more then one cpu/core... "

That seems to be an issue with virtualization, as far as I can see.

---

### Post by TJet1.8 on 2010-02-05
Actually...this isn't an issue with VMware Workstation.
The linux kernel 2.6.31 has a bug with processor scheduling.

This is why, for some, using VMware Workstation 6.5.3, VMware Workstation 7.0.x, Virtualbox, etc... shows the same slowness with Karmic 9.10 as Karmic uses the 2.6.31 kernel.

The processor scheduling issue has apparently been resolved with kernel 2.6.32 which "should" be included with Ubuntu 10.04.

So...when Lucid is release, your slowness with multi-processor vm's should be resolved.

Now...I don't consider myself a Linux expert by any stretch of the imagination, but if some guru out there knows how to update the kernel in 9.10 to version 2.6.32....maybe they can confirm this...or we wait another 2 months when Lucid is release and see.

If such a guru is successful in upgrading the kernel...maybe said guru could post a detailed howto on how they did it ;)

---

### Post by meemer on 2010-02-16
I updated my karmic koala to use the latest kernel (2.6.31.20) using the unsupported updates setting, and the performance problems seem to have gone away.  Everything is MUCH faster.  Thanks for the tip on the kernel performance issues.

You can either set your software sources to the unsuported updates setting as I did, or you might want to try something like kernelcheck:

[http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html](http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html)

Might be a better way, not sure, not being a ubuntu guru myself either.

---

### Post by IgnacioE on 2010-02-28
@Meemer: I upgraded to 2.6.31.20 on Ubuntu 9.10 and it didn't help at all. Still 100% on 1 CPU and I tried everything in the VM settings. I have Intel Core2 Duo CPU, t7300 @ 2.00GHz on a Dell Laptop.

System monitor shows 100% on 1 CPU for about 45 seconds, then switches over to the other CPU for 100%, then back - and my WinXP VM never boots up.

How frustrating :-(

I wonder if/when the 2.6.32 kernel will be available on 9.10.

---

### Post by Doping on 2010-03-08
> **meemer said:**
> I updated my karmic koala to use the latest kernel (2.6.31.20) using the unsupported updates setting, and the performance problems seem to have gone away.  Everything is MUCH faster.  Thanks for the tip on the kernel performance issues.
[...]


Hmm. My Ubuntu Karmic was updated to 2.6.31-20-generic a few days ago, but that didn't change anything with respect to VM performance. Windoze XP under VMware Player 3.0.1 is still unbearably slow when the number of virtual processors is set to 2. Setting it to 1 on the other hand is fine. (This is on a Core2 Duo and everything was fine under Jaunty...)

Guess I'll wait for Lucid and hope for the best...

---

### Post by TJet1.8 on 2010-04-04
> **TJet1.8 said:**
> Actually...this isn't an issue with VMware Workstation.
The linux kernel 2.6.31 has a bug with processor scheduling.

This is why, for some, using VMware Workstation 6.5.3, VMware Workstation 7.0.x, Virtualbox, etc... shows the same slowness with Karmic 9.10 as Karmic uses the 2.6.31 kernel.

The processor scheduling issue has apparently been resolved with kernel 2.6.32 which "should" be included with Ubuntu 10.04.

So...when Lucid is release, your slowness with multi-processor vm's should be resolved.

Now...I don't consider myself a Linux expert by any stretch of the imagination, but if some guru out there knows how to update the kernel in 9.10 to version 2.6.32....maybe they can confirm this...or we wait another 2 months when Lucid is release and see.

If such a guru is successful in upgrading the kernel...maybe said guru could post a detailed howto on how they did it ;)

Ok..so I decided to install Fedora 12 on a 320GB external usb drive to test my theory.

Fedora 12 ships with kernel 2.6.31.5, which after a full update ends up with kernel 2.6.32.10.

After installing VMware Workstation 7.0.1 and upping my xp guest cpu count to 1 cpu with 2 cores...I can confirm that there is NO SLOWNESS exibited on my xp guest or the Fedora 12 host.

So...when Ubuntu 10.04 ships (hopefully with a 2.6.32.x kernel), all our multiple cpu slowness problems should be resolved.

Can't wait!! :p

---

### Post by vmpho on 2010-04-27
I installed **Ubuntu 10.04 RC** with fresh installation plus VMware workstation 7.01, I  found the slow issue still exists even the kernel is 2.6.32.

I tested it on three PCs with following configurations:-

1st PC
AMD Athlon 4000 X2 
3GB RAM
Ubuntu 10.04
VM workstation 7.01
Nvidia GS 7000 graphics card
VM guest OS Win XP SP3
Results - Slow

2nd PC
AMD Phenom 9500  quad core CPU
3GB RAM
Ubuntu 10.04
VM workstation 7.01
Nvidia graphics card
same VM guest OS Win XP SP3
Results - Slow

3rd PC
HP DC7700 
Intel E6500 dual core CPU
 2GB RAM
 Ubuntu 9.10
Kernel 2.6.31-x
 VM workstation 7.01
 ATI X1500 graphics card
 same VM guest OS Win XP SP3
Results - Normal and acceptable

On 1st PC  , I installed virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb  with guest WinXPSP3 (new build not convert from VMDK) and the speed is  normal and acceptable.

I still don't understand what caused the slowness issue for VM WKS 7. 

I expected Kernel 2.6.32 fixes the problem but is not.

---

### Post by meskes on 2010-04-28
I run a Dual Core system as well with WS7 64 Bit installed. I've not noticed anything that hits the performance of the VM until I get a little too carried away with how much RAM I dedicate to the system after which it starts to hit swap. Other than that, it works great.

---

### Post by vmpho on 2010-04-28
Are you running Ubuntu 10.04 RC 32-bit. My guest just running WinXP with SP3 and vmware workstation 7.01 all are 32-bit.

A lot of links talking about the fix is on the Kernel 2.6.32. However Virtualbox 3.16.xxx looks much better on 10.04 RC.

:confused::confused::confused::confused:

Note: I just allocated 512MB memory to the guest OS. With "watch free" I can see pretty of available physical memory and never hits swap memory.

---

### Post by vmpho on 2010-04-29
Did some Google search and found the following information from Virtualbox web site:-

See [http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)

Linux hosts: fixed timing issue on hosts with Linux kernels 2.6.31 or  later with certain CPUs (asynchronous timer mode; bug [#6250]("http://www.virtualbox.org/ticket/6250")). 

Read 6250, it looks like we have to wait VMWare to fix the issue  and it answered why it works on one PC but not the others

:confused::confused::confused::confused::confused:

---

### Post by vmpho on 2010-05-29
At last I found the problem (slowness) was caused by the new partition formatted in NTFS with Linux utility.  The performance is very bad if runs in NTFS partition.

However once I formatted  the new partition again with EXT4 file system and the speed is back to normal.

I read an article in VMWare web site mentioned about the issue of NTFS (format by Linux utility) in Linux.

Note sure any better if the partition is format in Windows not Ubuntu ?

---

