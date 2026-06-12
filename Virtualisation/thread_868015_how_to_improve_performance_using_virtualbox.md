---
title: "how to improve performance using virtualbox"
date: 2008-07-23
forum: Virtualisation
---

### Post by wsamh on 2008-07-23
I need advice on what should I be doing do improve performance of my vm with windows xp as a guest os. Right now it runs pretty good. But I want to know if there is any way to make it a little better.

---

### Post by tuxxy on 2008-07-23
You could increase the RAM allocated to the virtualbox if thats being the problem.

---

### Post by wsamh on 2008-07-23
I have 1 gig of ram and the guest os is set at 256MB. I think that is enough for windows xp. It is not really slow. It is just there is a slight lag. I hava P4 1.7. should I expect that for that kind of processor.

---

### Post by tuxxy on 2008-07-23
I dont use virtualbox intensively so not experienced any sort of lag but when I installed a virtual XP it recommended 512 MB for me.

How does it lag, is it certain programs?

---

### Post by wsamh on 2008-07-23
It lags when it starts up and shutsdown, and doing windows updates.I don't have any programs installed just yet because I'm trying to figure out this lag problem, if it is a problem. After it starts up, it is fine ding normal things. The lag is like a fews seconds longer than it usually is when using a physical partition.

---

### Post by 00arthuryu on 2008-07-24
With a 1.7, I would expect some lag, as it also lags on my 2.4GHz
Virtualbox does run slower than native windows. especially with bulky programs, itunes, limewire, java etc.
you could try and use the emulation abilities of your cpu though. Although this made mine even slower :s

---

### Post by spencerlewis on 2009-02-19
i'm also using virtual box with XP it laggs pretty bad. and in XPs  system properties it says its running at 800mhz(my host is using 2.0ghz! u see a problem?:o)  and using .99gb of ram.
 how to turn up the processor? 

ill have to tinker wit it:)

---

### Post by HotShotDJ on 2009-02-19
> **spencerlewis said:**
> i'm also using virtual box with XP it laggs pretty bad. and in XPs  system properties it says its running at 800mhz(my host is using 2.0ghz! u see a problem?:o)Yes.  I see a problem.  But it is not what you think.  This means that the CPU is not where the bottleneck is.  The CPU is managed by the HOST os, not the guest.  If any process, including VirtualBox and everything running within it, needs more processor speed, the Host will step up the CPU speed.  If you don't believe me, you can test it for yourself.  Try switching your CPU settings on your host from "On Demand" to "Performance." (You can do this by adding the applet "CPU Frequency Scaling Monitor" to your panel. Once it is in your panel, just click on it and adjust the settings). Now, restart your VM.  You should see XP's system properties showing that the CPU is running at full throttle (2.0 Ghz).  But you will see little, if any, performance improvement.

The bottle neck is almost certainly with your physical RAM.  When using any virtualization software, you must keep two things in mind... 1) the memory needs of the HOST OS, and 2) the memory needs of the GUEST OS.  With Windows XP, you MIGHT get ok performance (but certainly not optimal) with less than 512 Gig RAM.  With Ubuntu, you MIGHT get ok performance (but certainly not optimal) with 512 Gig RAM.  But when you run Windows in a Virtual Machine (with 256 Meg RAM assigned to it), you are also leaving only 256 Meg RAM for Ubuntu to use.  You are going to have the VM doing its swapping thing with its virtual drive PLUS Ubuntu doing its swapping thing with its swap partition.  Slow-Down + Slow-Down = INSANE SLOW-DOWN.

---

### Post by iheartubuntu on 2009-02-19
The problem is you have only one gig of total ram. Ubuntu recommends 512mb to operate smoothly, which only leaves you half to run virtualisations. I dont think 256mb is enough. You could up it, but Im sure your system will lag all together. You need at least 2gb of memory IMO.

---

### Post by spencerlewis on 2009-02-19
i totaly see what u guys are saying and i tried the preformance thing and it works! pretty neat

---

### Post by HotShotDJ on 2009-02-19
> **spencerlewis said:**
> i totaly see what u guys are saying and i tried the preformance thing and it works! pretty neatJust remember to keep it set for "On Demand" most of the time.  The CPU Manager in Ubuntu is VERY good at what it does.  When the system needs the CPU running at full throttle, then the CPU Manager will give it everything it has.  Otherwise, it is better to have the CPU throttled down and generating less heat.

---

### Post by damis648 on 2009-02-19
You could enable hardware virtualization support (Vt-x AMD-v)

---

### Post by tilixibr on 2010-03-17
> **damis648 said:**
> You could enable hardware virtualization support (Vt-x AMD-v)
i enabled virtualization support and when i shutdown the vm and turn it on i get an error :(
something about the bios i dont remember too much

---

### Post by Christopher674 on 2010-05-02
I got the same error message.  I have a Gigabyte system board, and I had to go into the bios of the machine and set "virtualisation" to "enabled"

After that, no more error messages.

---

### Post by mcasperson on 2010-07-21
To get the most performance out of a XP VM, use TinyXP, strip out the extraneous services, enable SATA, and clean up the disks. This article [here ]("http://www.brighthub.com/hubfolio/matthew-casperson/articles/78538.aspx")shows you how.

---

### Post by TheFu on 2010-07-21
> **damis648 said:**
> You could enable hardware virtualization support (Vt-x AMD-v)
There are some settings that cannot be changed post-install for MS-Windows. While you can change the VT-x support toggle, there are other toggles that are forced when you do that which cannot be changed without a new HAL installed.  It is similar for changing the number of CPUs from 1 to 2 - the easiest answer for getting the new HAL is a fresh installation of MS-Windows.  Also, according to Sun/Oracle, using VT-x is actually slower than not using it for VirtualBox. Seems their code does a better job than the hardware.

Other things to make any virtualization work better, but I did test VirtualBox-OSE:
1) Use SATA disk controllers, not IDE. Note that WinXP does not come with these drivers, so you need to have them before you switch the disk if you want to boot.
2) Use GigE virtual networking, not 100base-tx; I like the Intel PRO/1000 MT virtual NICs.
3) Allocate at least the best amount of RAM for the OS, not the min. For WinXP, that is 1GB.
4) Use virtio drivers whenever possible for disk and networking (I've never done this myself and don't know if this overrides 1 and 2 or not)
5) Do not use sparse virtual disks (disks that dynamically grow as needed); Use pre-allocated files or, even better, pass thru partitions via LVM.
6) Place the "full" virtual files (not using dedicated LVM) on a high performance disk array.
7) Do not allocate 4 vCPUs when the workload only needs 1 vCPU. That will take away from other VMs and cause more 

I did only 1, 2, 3, 5 and 6 on a WinXP VM. Here's the specifics (HowTo) [http://jdpfu.com:82/2010/06/22/virtualbox-performance-improved](http://jdpfu.com:82/2010/06/22/virtualbox-performance-improved) and my timed results. Boot times for the VM were reduced by almost 50%.

Are there more things I should be doing?

Anyway, I'd like to see an easy how-to for virtio use under KVM. I'd honestly prefer to use KVM, but wasn't able to get acceptable performance.

---

### Post by Ginsu543 on 2010-07-22
Just to add my $.02:

As you can see in my siggy, my current system has enough cpu/ram resources to throw quite a bit at my Windows XP VM: one cpu core out of 8 and 2 GB out of 6 GB system memory. My Windows XP VM works amazingly fast and smooth. As TheFu suggested above, I think the key is to allocate enough memory and to use a fixed-size, pre-allocated .vdi file.

As far as VT-x is concerned, I didn't notice much difference between having it on and off for basic computer functions, but there was a HUGE difference in file transfer speed through USB and shared folders. Having VT-x enabled made it MUCH faster.

---

### Post by edwardtilbury on 2010-08-04
[]("http://ubuntuforums.org/member.php?u=942229")Ginsu543 how many cores are you running?

I also have an intel i7 with 8 gigs of ddr3, I'm trying to figure out the optimal settings to run virtual box in before I reinstall windows to make a new hal.


Right now I give windows 4 gigs of ram, but I think I'm killing myself with the cpu's , I installed with 1 CPU, so maybe my hal is only taking advantage of that... I'll try 4 cpu's.  Do you really have to reinstall windows after that?  If your additional CPU's appear in the system monitor in Windows that means that they're in the HAL?

---

### Post by Ginsu543 on 2010-08-05
I'm currently allocating only one core to my VM. That's because I set up my VM before I upgraded to my current i7 rig and was too lazy to reinstall Windows to try to take advantage of more than one core. Besides, I don't really do anything on my VM that requires a lot of cpu power. I do set aside 2 GB ram for the VM and that gives me all the performance I need for what I do.

---

### Post by soldier1st on 2010-08-06
XP even a virtual one needs at least 512MB to operate decently but 1GB would prove better especialy if your running memory intensive applications and virtualbox offers to use the Host I/O in the storage settings so that will help and Preallocate the disk as then the disk won't need to adjust the size. also your cpu is fine but the main thing to consider is the memory needs of the host and the guest as if the host has insufficient memory for it's needs it will use the hard drive and that will cause a slowdown and then your guest will run slow but if the host has enough memory for it's needs it won't use the hard drive and won't cause a slowdown so your better off doubling or even trippling your memory if your going to be doing any kind of virtualization.

---

