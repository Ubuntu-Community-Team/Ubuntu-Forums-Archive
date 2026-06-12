---
title: "Virtualbox or kvm: total freeze/hangup"
date: 2010-03-15
forum: Virtualisation
---

### Post by tankdriver on 2010-03-15
Hello,
I have an Asus N90Sc Notebook PC, running Ubuntu Karmic 64-Bit.
It has an Intel C2D P8700 2530 CPU (which has the VT-x feature)

The Problem is I can't do any 64-Bit-Guest virtualization under Karmic (or Lucid A3)
I tried Virtualbox 3.1.4 and qemu (qemu-launcher from repos.)
When I launch the VM, the computer immediately freezes completely.
There are no bios-settings affecting VT-x or sth.

With Windows 7 Virtualbox works flawlessly.

What can I do to fix this problem?

Thanks

[SIZE=1]Hardware: [http://www.asus.com/product.aspx?P_ID=mUcHrzcLLUhTFYqS](http://www.asus.com/product.aspx?P_ID=mUcHrzcLLUhTFYqS)[/SIZE]

---

### Post by MooPi on 2010-03-15
Have you install the dkms kernel installed ? Are you using the open source or version that's in the repository or from Sun's repository ? Can you show your ram amount ? I have , virtualbox-ose-source, virtualbox-ose-qt, virtualbox-ose, virtualbox-guest-additions, installed on a AMD quad not using qemu. No problems here. You might want to try the open source version.

---

### Post by tankdriver on 2010-03-16
dkms is installed.
I completely removed the proprietary* virtualbox* package and the *kvm* packages and installed the *virtualbox-ose* packages from the ubuntu repos.
It does not work either. Exactly the same issue as before.

I have 4GB RAM
```
$ free -mt
             total       used       free     shared    buffers     cached
Mem:          3964       1308       2656          0         43        471
-/+ buffers/cache:        793       3171
Swap:         8001          0       8001
Total:       11966       1308      10657
```I tried the boot option *nohz=off*, no success.

It seems to be that this problem is triggered by the "*VT-x/AMD-V enable*" option.
When this option is disabled, everything is ok. But I can't do 64-virtualization without it.

---

### Post by Rainer-E on 2010-03-16
Hi folks,

here's my story about checkin out Lucid Lynx from within VirtualBox on top of Karmic Koala (running on an AMD64 Athlon X2 Dual Core-Notebook with 4G mem):

- VBox-OSE-3.0.8 (coming with Koala) : no chance to get installed the stuff
- SUN VBox 3.1.4 : 64Bit guests need  the VT-x/AMD_V feature activated to run, which on my machine currently is blocked by the KVM kernel module (I'll try KVM later on) ...
That's why I'm using the 32Bit-Lynx (it's OK to check out Lynx) and on my box it's running fine within the (proprietary SUN) VBox 3.1.4 (I just downloaded VBOX 3.1.4-OSE source in order to try that, too) - however, I didn't install it in the Koala-partition but in two seperate NTFS-partitions (for either /-FS and swap, actually used by WindozeVista) - and I gave it plenty of memory to run (1,5 G) ... anyhow, with this setup it's running fine, except for one issue : After installing the VBoxLinuxAdditions (needed e.g. for file sharing) high resolution graphics don't work anymore

BTW, I also tried the Lynx (64Bit) under VMware Server 2.0 on top of Windoze Vista, and there it's running fast, too , without problems so far...

Take care
Rainer

---

### Post by tankdriver on 2010-03-16
I have tried the 2.6.33 kernel from *kernel.ubuntu.com* with *virtualbox 3.1.4.* **fail.**
Ubuntu is still freezing when launching the x64 VM.

Interesting point: when I set "*nolapic*" as boot option, only 1 CPU core is detected, but I can launch the VM (eg. Karmic live CD), I can select Language, but when I enter "Try Ubuntu..." The (host) screen goes Black and freezes.

I think this might be an BIOS issue and depends on the hosthardware. (BIOS is already up-to-date) Probably wrong ACPI/APIC. Especially because I can't set VT-x usage in Bios.
So the *VT-x/AMD-V init method* (as you can see your Vbox.log) is not *GLOBAL* but *LOCAL*.
That might be problematic.

---

### Post by tankdriver on 2010-03-17
I found a method to check if the host theoretically is able to use VT-x:
```
sudo apt-get install msr-tools
sudo modprobe msr
sudo rdmsr 0x3a
```[FONT=Verdana]gives me
[/FONT]```
5
```[FONT=Verdana]

[SIZE=1]Source: [http://www.mail-archive.com/sony-vaio-z-series@lists.launchpad.net/msg00399.html](http://www.mail-archive.com/sony-vaio-z-series@lists.launchpad.net/msg00399.html)[/SIZE]

That means the CPU and the BIOS have enabled VT-x.
I will try random unloading kernel modules. I have no idea what to do to solve this problem.
[/FONT]

---

### Post by tankdriver on 2010-03-23
I made some testing with boot options (host system):

```
irqpoll
```>starting an 64-Bit VM crashes X on host > dropped back to tty1 shell. cursor is blinking but no reaction of keyboard (hard reset)

```
nolapic
```>starting an 64-Bit VM gives me an black screen (host), frozen.

```
irqpoll+nolapic
```> starting an 64-Bit VM > black screen + KERNEL PANIC

With irqpoll there has been created a VBox.log file. (attached)

---

### Post by falha404 on 2010-03-25
[http://forums.virtualbox.org/viewtopic.php?f=7&t=23978]("http://forums.virtualbox.org/viewtopic.php?f=7&t=23978")

Installing linux-image-rt and linux-headers-rt worked for me.


Fabiano Nunes

---

### Post by tankdriver on 2010-03-25
> **falha404 said:**
> [http://forums.virtualbox.org/viewtopic.php?f=7&t=23978](http://forums.virtualbox.org/viewtopic.php?f=7&t=23978)

Installing linux-image-rt and linux-headers-rt worked for me.


Fabiano Nunes

Thanks for the tipp, but when I boot the rt kernel, I have black screen and instant kernel panic when I try to start the VM.

---

