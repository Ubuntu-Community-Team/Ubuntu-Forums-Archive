---
title: "Stuck while installing Ubuntu on Virtualbox: Freeing initrd memory"
date: 2023-08-23
forum: Virtualisation
---

### Post by ayyypaaa on 2023-08-23
**I have been trying to install Ubuntu 22.04.3 on Virtualbox 7.0 and I am facing the following issue:**

[B]
 So I tried to install Ubuntu 20.04.6 after that and faced the same error (but a different memory size):[/B]


Earlier I has installed Ubuntu 20.04 on Virtualbox on my Lenovo ideapad and it worked fine but I am facing the above error while installation on my new Asus TUF laptop. It would be great if anyone can guide me through this.

---

### Post by MAFoElffen on 2023-08-23
Usually if the system is getting "Freeing _____ memory" errors and VirtualBox is not starting its a low memory error. 

First question would be, what is the HOST OS ad release version? 
Second would be how much memory does the system have? 
How much memory is being allocated to the Guest VM?
How long has the Host been online? (Since the last boot...)
What else is running at the time?

Here is why I am asking theses types of questions... When VirualBox starts a VM Guest, the way is does that, it doesn't just need the ampunt of memory allocate to the VM, the "block" of memory is required to be contiguous (no gaps or fragmentation).

The longer the host runs, the more of a chance that things running in memory are not in a contiguous blocks...

---

### Post by mdalacu on 2023-09-15
Exactly the same error on win11 host with wsl2. Theoretically it should work, slow but it should.
I have allocated 2vcpu and 16GB ram.
I have tried 20.04, 22.04, 23.04 of Ubuntu. After line Freeing initrd memory ...nothing.
Did you found any solution for this?

---

### Post by MAFoElffen on 2023-09-15
Found this in passing. 

VirtualBox allocates memory in lazy mode, which means that RAM is dynamically allocated by the host as the guest uses an increasing quantity of memory. To get around that, try this command:
```

VBoxManage setextradata "VM name" "VBoxInternal/RamPreAlloc" 1

```
That command forces VirtualBox to "grab" all of the guest's memory at startup that is possible.  This will attempt to allocate the entire guest memory from the host.  If that memory isn't really free, then the guest will not start at all.

That command is per VM, you must use the name of the VM in that command.

---

### Post by SeijiSensei on 2023-09-16
Are you running VirtualBox on a Linux machine? I'd use KVM instead.

[https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/)

---

### Post by ilovenewjeans on 2023-09-17
im also having the exact same problem on the same laptop, i have tried everything but it still doesnt work

---

### Post by MAFoElffen on 2023-09-18
And is it capable of running KVM? That has been my Virtual Host preference for over a decade now.

---

### Post by mdalacu on 2023-09-18
Hi @MAFoElffen,

> VBoxManage setextradata "VM name" "VBoxInternal/RamPreAlloc" 1
With this setting the VM fails to start at all .. :/

> Attemted illegal operation in simplified memory management mode. (VERR_PGM_NOT_SUPPORTED_FOR_NEM_MODE).
Result Code:
E_FAIL (0X80004005)
Component:
ConsoleWrap
Interface:
IConsole {6ac83d89-6ee7-4e33-8ae6-b257b2e81be8}
Any more ideas? Thanks

---

### Post by ilovenewjeans on 2023-09-18
i think so yea, it has a ryzen 9 7940hs and 16gb of ddr5 ram

---

### Post by MAFoElffen on 2023-09-18
Please post the results of this within CODE Tags:
```

grep . /proc/meminfo

```

---

### Post by MAFoElffen on 2023-09-18
Well, dug int some Linux and kernel System Admin Doc's and found this. I was looking for how to find what the largest block of contiguous memory is. Well at [https://www.kernel.org/doc/Documentation/filesystems/proc.txt](https://www.kernel.org/doc/Documentation/filesystems/proc.txt), it says that /proc/buddyinfo is used primarily for diagnosing memory fragmentation.
> 
External fragmentation is a problem under some workloads, and buddyinfo is a
useful tool for helping diagnose these problems.  Buddyinfo will give you a 
clue as to how big an area you can safely allocate, or why a previous
allocation failed.

I tested all this on my laptop, which has 8GB of RAM. I figured that would be a bteer example than either of my servers, that have 128GB RAM.

Looking at it:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ sudo grep . /proc/buddyinfo
Node 0, zone      DMA      0      0      0      0      0      0      0      0      0      1      3 
Node 0, zone    DMA32  19883   7185   4058   3123   1847   1220    637    312    139     71     29 
Node 0, zone   Normal  22095  18552   9367   4498    739     90    233    222     93     31      7 

```
Where: 
DMA is the first 16MB
DMA32 is the above 4GB (64bit systems)
Normal is the memory between 16MB and 4GB

PAGE_SIZE is 4Mbyte

11 Columns in the table
Column 1 is 2^(0*PAGE_SIZE) chunks of memory (4kb each)
Column 2 is 2^(1*PAGE_SIZE) chunks of memory (8kb each)
Column 3 is 2^(2*PAGE_SIZE) chunks of memory (16kb each)
Column 4 is 2^(3*PAGE_SIZE) chunks of memory (32kb each)
Column 5 is 2^(4*PAGE_SIZE) chunks of memory (64kb each)
Column 6 is 2^(5*PAGE_SIZE) chunks of memory (128kb each)
Column 7 is 2^(6*PAGE_SIZE) chunks of memory (256kb each)
Column 8 is 2^(7*PAGE_SIZE) chunks of memory (512kb each)
Column 9 is 2^(8*PAGE_SIZE) chunks of memory (1024kb each)
Column 10 is 2^(9*PAGE_SIZE) chunks of memory (2048kb each)
Column 11 is 2^(10*PAGE_SIZE) chunks of memory (4096kb each)

After doing this:
```

sudo sysctl vm.compact_memory=1

```
What that should do, if it doesn't crash the kernel, is to try to consolidate pages from left to right (larger blocks) and from DMA to Normal to DMA32

This was the results of memory compaction to defragment memory:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ sudo grep . /proc/buddyinfo
Node 0, zone      DMA      0      0      0      0      0      0      0      0      0      1      3 
Node 0, zone    DMA32   3917   3864   3034   2818   1908   1277    688    346    153     75     29 
Node 0, zone   Normal     60     89   4352   1153    212     58     26     11      4      2      0 

```

---

### Post by mdalacu on 2023-09-19
> i think so yea, it has a ryzen 9 7940hs and 16gb of ddr5 ram
I also have this CPU with 64GB of ram.
Could it be related? A CPU incompatibility?
I must say that a VM with Win10 is running just fine on my Win11 host...

---

### Post by ilovenewjeans on 2023-09-19
> **MAFoElffen said:**
> Please post the results of this within CODE Tags:
```

grep . /proc/meminfo

```
This is a linux command right? My and ops problem is that we can't even install ubuntu on a vm because it hangs at "Freeing initrd memory".

---

### Post by ilovenewjeans on 2023-09-19
> **mdalacu said:**
> I also have this CPU with 64GB of ram.
Could it be related? A CPU incompatibility?
I must say that a VM with Win10 is running just fine on my Win11 host...
I think that's the source of the kernel panic, but i still haven't found any solutions, i tried disabling hyper-v but it wouldn't disable.

---

### Post by mdalacu on 2023-09-19
Anyway...i love my minipc...i am gaming Starfield on it! :guitar:

---

### Post by MAFoElffen on 2023-09-20
> **ilovenewjeans said:**
> I think that's the source of the kernel panic, but i still haven't found any solutions, i tried disabling [COLOR=#ff0000]hyper-v[/COLOR] but it wouldn't disable.
First-- Personally, I support Linux, Windows... KVM, VMware, Hyper-V, XEN/Centrix, and have supported VirtualBox... It would have been nice to have been told the Host System OS, early on. Since it was not mentioned, and this is an Ubuntu Linux Forum, I assumed the host might have been Ubuntu, with VirtualBox as the Virt Host... But this points out this was an incorrect assumption. I guess I should have asked.

Second-- Since I also support Windows, I know this --> Microsoft assumes that Windows and it's own product exist in a vacuum. If you turn on Hyper-V, then it takes over the system with very deep roots, and no other Virtualization hosting system will work on it. That goes for VirtualBox, and VMware Workstation Pro or VMware Player. They don't care, as long as Hyper-V works.

There is no easy way to see memory fragmentation or a way to defragment memory in Windows OS. I know of one tool, but it is over $400 a year to subscribe to a subscription for it.

There is a function in C# to check if you can allocate a certain size of memory, in your want to code it yourself...

---

### Post by zoxzox2 on 2023-09-20
I meet the issue as well while I am trying to install ubuntu 22.04.3 on vbox 7.0.10. My computer has 7840s and 32GB lpddr5x memory. It seems to be a common problems with ryzen 7040 series. Hope someone would told me how to deal with it.

---

### Post by mdalacu on 2023-09-24
Hey! Every problem went away after installing the latest BIOS version. So, check if you have a update available for your FW and do it.
Victory!!!! :guitar:

---

### Post by MAFoElffen on 2023-09-24
Happy to hear this is working for you now.

Please use the "Thread Tools" link in the upper right to Mark this as "Solved" so that others (many have said they have the same issue) can find what worked for you.

---

### Post by mdalacu on 2023-09-25
I am not the OP :/

---

### Post by MAFoElffen on 2023-09-26
> **mdalacu said:**
> I am not the OP :/

LOL... Sorry. Lost track.

Checked. The OP was: ayyypaaa

He has not posted since his original, first post. That was over 4 weeks ago. Maybe he abandoned this as he didn't need help? Oh well.

---

### Post by mross117 on 2023-10-06
> **ilovenewjeans said:**
> i think so yea, it has a ryzen 9 7940hs and 16gb of ddr5 ram


I have same processor but with 32 gb ddr5 ram and so this bug have appeard after making the bios 308 update... Have you made it or are you already in an older version ? I have tested and this appeard to be on all linux distribution in my case...

---

