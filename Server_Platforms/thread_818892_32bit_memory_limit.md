---
title: "32bit memory limit"
date: 2008-06-04
forum: Server Platforms
---

### Post by bbarrons on 2008-06-04
I have a rackable server with dual xeon 2.8 processors. I put 6 gb of memory in it but only 4 gig shows. Is there a way around the 32 bit limit?  Or am I just wasting the extra 2 gigs of ram?
 thanks
 Bill

---

### Post by quelx on 2008-06-04
About Windows, but applies to all 32 bit operating systems.

[http://www.codinghorror.com/blog/archives/000811.html](http://www.codinghorror.com/blog/archives/000811.html)

---

### Post by wdaniels on 2008-06-04
If you use the server kernel, it has PAE enabled by default, which should allow you to use all the RAM, but there is a small performance hit with PAE and potentially some hardware driver issues (last I heard, anyway).

---

### Post by Joeb454 on 2008-06-04
I've never heard of the hardware issues with PAE, but I know that's the way to get the system to see all 6GB.

Unless you want to run a 64 bit system of course, then you'll have no issues at all. I've experienced no issues with my 64 bit install on my laptop

---

### Post by logos34 on 2008-06-04
as long as your xeon is EM64T-capable, you can run x64 ubuntu and use all your ram

---

### Post by wdaniels on 2008-06-04
> **logos34 said:**
> as long as your xeon is EM64T-capable, you can run x64 ubuntu and use all your ram

Yes, I'm assuming these are older Xeons before the 64-bit extensions? The obvious solution would be to just switch to 64-bit Ubuntu - that is what I use and there are no major problems with it now.

I don't remember the details about the hardware issues with PAE, but I think the hardware needs to support 64-bit PCI addressing, or use some particular DMA interface that knows how to work around it, or something like that...possibly this has all been remedied by now, it was a while ago that I read up on it all.

---

### Post by bbarrons on 2008-06-04
After I posted I found  thread that said PAE was enabled in the server kernel. I thought I had already had that because I had done a server install but apparently not. I tried to update to the linux-image-server but got several grub errors. I will have to look unto that tomorrow. I didnt think I could instal a 64 bit system on this board but I really dont know if the xeon processors are correct for 64bit. I also never looked into that. Any easy way to tell?
 thanks
 Bill

---

### Post by Joeb454 on 2008-06-04
```
cat /proc/cpuinfo
``` should tell you what you need :)

---

### Post by bbarrons on 2008-06-04
here is the output of that code:
processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) CPU 3.06GHz
stepping        : 9
cpu MHz         : 3056.557
cache size      : 512 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 6112.96
clflush size    : 64

I have 2 servers. this one has 3.0 xeon, the has 2.8
SO, the solution is to install the 64 bit version and see where it takes me?

---

### Post by wdaniels on 2008-06-04
> **bbarrons said:**
> flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr

If the processor were 64-bit you would see a flag called "lm" here, which there isn't, so you're out of luck on that one.

Also, check that your motherboard supports the full 6GB RAM (see what it reports in the BIOS).

---

### Post by bbarrons on 2008-06-05
motherboard supports 12gig  6 slots and capable of 2 gig per slot. I have 6 1 gig memory in it now.
it shows 6 gig when booting

---

### Post by wdaniels on 2008-06-05
So are you still having a problem with this? You're definitely booting with the server kernel and still can't see all the RAM?

---

### Post by bbarrons on 2008-06-05
that is the problem, I checked the kernel and it was not the server kernel so I tried to apt-get it and it fails. I get an dpkg error that I have never seen before. I cleaned out the archives and tried it again with the same result. it is 
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-18-server_2.6.24-18.32_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.24-18-server': No space left on device
 I have more space than I need. my boot partition has 200 mb, root has 40 gigs and home has 250 gig... space isnt the problem...... I dont think :-)

---

### Post by bbarrons on 2008-06-05
also apt-get -f install and dpkg --configure -a end in the same results

---

### Post by wdaniels on 2008-06-05
> **bbarrons said:**
> No space left on device
 I have more space than I need. my boot partition has 200 mb, root has 40 gigs and home has 250 gig... space isnt the problem...... I dont think :-)

I think you need to take the error at face value and start from there. Sometimes you can run out of inodes even though there is still physical space left - it just can't be allocated. So, first thing, check:

```
df -i
```

---

### Post by Steveway on 2008-06-05
Since the Kernel goes to /boot and you say it has only 200 MB I see what is failing.
You don't have enough space there, a kernel can take up about 50 MB with ease.

---

### Post by bbarrons on 2008-06-05
here is the output from df -i
 
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/mapper/vg1-root 2621440  217047 2404393    9% /
varrun                219902      93  219809    1% /var/run
varlock               219902       2  219900    1% /var/lock
udev                  219902    2951  216951    2% /dev
devshm                219902       1  219901    1% /dev/shm
lrm                   219902      18  219884    1% /lib/modules/2.6.24-17-generic/volatile
/dev/md0               12048      38   12010    1% /boot
/dev/mapper/vg1-home 27779072   30576 27748496    1% /home

is it possible that because I used software raid and have my boot partition over 4 drives the problem?

---

### Post by wdaniels on 2008-06-05
> **Steveway said:**
> a kernel can take up about 50 MB with ease.

Not in /boot - most of the kernel stuff goes under /lib. 200MB ought to be enough to install one extra boot image.

> **bbarrons said:**
> /dev/md0               12048      38   12010    1% /boot

OK, doesn't seem to be inodes...

> **bbarrons said:**
> is it possible that because I used software raid and have my boot partition over 4 drives the problem?

I wouldn't have thought so.

Try writing to /boot yourself manually (just copy a few files over or something) and see if you get the same error - it could be that the filesystem is corrupted.

---

### Post by windependence on 2008-06-05
> **wdaniels said:**
> If the processor were 64-bit you would see a flag called "lm" here, which there isn't, so you're out of luck on that one.

Also, check that your motherboard supports the full 6GB RAM (see what it reports in the BIOS).

This is exactly the problem here. There is a huge misconception about 64 bit vs. 32 bit and the ability to "see" the memory. If the board supports it, the entire 6 GB will be recognized even on the 32 bit system, the system will just only be able to page out to 4 GB at a time. It's not really that big of a problem and PAE is a hack to get around it that seems to work fairly well. 


He needs to make sure the BIOS supports 6 gigs first and then try moving the RAM modules around to get it to see them. Server boards especially have specific requirements as to where the chips are to see all installed memory.

-Tim

---

### Post by wdaniels on 2008-06-06
> **windependence said:**
> There is a huge misconception about 64 bit vs. 32 bit and the ability to "see" the memory. If the board supports it, the entire 6 GB will be recognized even on the 32 bit system, the system will just only be able to page out to 4 GB at a time. It's not really that big of a problem and PAE is a hack to get around it that seems to work fairly well. 

This is contrary to my understanding. PAE does not change the 32bit addressing used by each process, so a single process can still only address up to 4GB, but PAE can map that 4GB into any part of up to 64GB physical RAM. Without PAE though, I don't think the kernel will even see all the RAM.

He already said that the BIOS reports the full 6GB, so I think the problem will be solved as soon as he manages to get the server kernel installed.

---

### Post by Steveway on 2008-06-06
> **wdaniels said:**
> Not in /boot - most of the kernel stuff goes under /lib. 200MB ought to be enough to install one extra boot image.



OK, doesn't seem to be inodes...



I wouldn't have thought so.

Try writing to /boot yourself manually (just copy a few files over or something) and see if you get the same error - it could be that the filesystem is corrupted.
Oh yes, you are correct. I should have double-checked instead of relying on my memory only.

---

### Post by bbarrons on 2008-06-07
I uninstalled all kernels on the system and then installed just the server kernel. I use lilo for a boot loader because grub would not install on this box. I know in grub I could select the kernel to start but dont see that option in lilo when it is booting. System still shows only 4gigs of memory. Do you have to activate PAE or does it start at boot?
 I use synaptic as my package manager and it shows only the server kernel as loaded. 
any thoughts?
BTW- thanks all that contributed to the discussion. This forum is one of the best.
 Bill

---

### Post by wdaniels on 2008-06-07
You can check the running kernel with:

```
uname -a
```

As far as I'm aware, the kernel should just look for the "pae" flag for the cpu and enable PAE if it's supported (which it is based on the /proc/cpuinfo that you posted before). Can you also post the output from:

```
free
```

---

### Post by bbarrons on 2008-06-09
I was able to correct the problem thanks to all the advice given here. IT was a space problem. Even though I had a raid built with 200mb in it it was only using the boot space from one drive. I have since corrected that and now I am using the server kernel on both servers and it shows all available memory.
 I created another problem now that I cant seem to fix. I tried to remove all the kernels first that were not server kernels. When apt-get would not remove them I deleted the files in the boot folder and then installed the kernel. Now, I cant install anything on one server because it wants to still try and uninstall the missing kernel. It cant find it and just quits. this is what I have tried so far. apt-get remove linux-image#####
dpkg --configure -a
 and also used the adept manager and synaptics package managers to cancel the  request. All other installs I try first want to remove the kernel image.
 What am I missing?
 thanks
Bill

---

### Post by bbarrons on 2008-06-09
solved. I went into /etc/dpkg/info and deleted all files relating to the missing kernel. apt-get -f install cleaned up the mess and I am back to installing what I need.
 Bill

---

