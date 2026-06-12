---
title: "Inspiron 1525 Bios lacks VT option"
date: 2008-02-28
forum: Virtualisation
---

### Post by mari0 on 2008-02-28
hi
I tried to enable VT on my DELL inspiron 1525 today (to get kvm running) but i cant find an option to do so in the bios.
The Bios is up-to-date (01/07/2008) and the Hardware should support VT.

Just to make sure i don't talk trash, this is what ' sudo modprobe kvm-intel' gives me:
```

FATAL: Error inserting kvm_intel(/lib/modules/2.6.22-14-generic/kernel/drivers/kvm/kvm-intel.ko): Operation not supported
```
I'm right to assume that i have to enable Virtualisation in the Bios, ain't I.

//edit: /proc/cpuinfo shows
flags        : fpu **vme** de [...]
on both cores. This should be the Virtualisation Extension, right? so why isnt 'sudo modprobe kvm-intel' working?

thx in advance
mari0

---

### Post by dicecca112 on 2008-02-28
Yes the newer Dells you can't enable VT.  The hardware supports it, but for some reason Dell decided not to enable it or include an option in the BIOS to do so.

---

### Post by harold4 on 2008-02-28
The T5550 does not have VT instructions, in case that's the chip you have.

---

### Post by mari0 on 2008-02-28
so there is no way of getting kvm to run?

---

### Post by harold4 on 2008-02-28
You should be able to run kvm without having the kvm-intel module.  VT instructions allow the chip to handle virtual environments more efficiently, without the instruction the performance is normally still very good..

---

### Post by fjgaude on 2008-02-28
Hey, I have a Dell E1505 on which I run VMware server without issue. It's quick and has no speed problems. The CPU is a slow Intel Core 2 Duo, 1.73MHz with one gig of RAM.

I don't think the BIOS has anything to say about VT. VMware runs fine without it.

---

### Post by harold4 on 2008-02-28
VT is an instruction IN the Core2Duo generation processors, minus the t5550.

If the OS knows how to use it and it's present (as stated above) it will.

VT is most beneficial in environments when more than 1 virtual machine instance is running.  For single virtual machine instances in a user environment, you won't see much, if any difference.

---

### Post by mari0 on 2008-03-01
hmm i can't even get KVM up and running. I installed kvm from the repositories and try to start my VM with "kvm -m 768 -redir tcp:3389::3389 windows.img"
The VM starts and is running, but i get the following error printed out in the console:

kvm kernel version too old: KVM_GET_API_VERSION ioctl not supported
Could not initialize KVM, will disable KVM support

thx in advance
mari0

---

### Post by TehPenguin on 2008-03-25
Good New Everybody!

In the latest BIOS revision for the 1525 (ie BIOS version A11) Dell has put back in the Virtualisation options!!

---

### Post by otterrsch on 2008-03-27
I updated the inspiron 1525 BIOS to A11
  but I don't see where you can set the
  virtualization options.

---

### Post by David Cartwright on 2008-04-16
Actually, the bad news is that lots of the low-end Intel CPUs do not support Intel's VT Virtualization Technology.

This list on Intel's web site has the information you need to determine whether or not a particular CPU supports VT:
[http://www.intel.com/products/processor_number/eng/chart/core2duo.htm](http://www.intel.com/products/processor_number/eng/chart/core2duo.htm)

I haven't found any of the entry level notebooks from Dell that support VT, whereas I also have an entry level notebook from HP that uses an AMD CPU that will support KVM.

Burnt once, twice shy .... I won't be buying any more Dell notebooks until Dell changes its stance on CPUs with VT support.

And given that the upcoming Ubuntu 8.04 has KVM as its default virtualization software, there are going to be lots of very frustrated Dell 1525 users.

So, in answer to the post about VT and the BIOS, it's not listed as a BIOS option because the CPU cannot support VT.

---

### Post by luisjorge on 2008-04-24
Hi everyone! All I can say is I have an Inspiron 1525 with the T5550 Core2Duo, and I run Vista Home Premium in virtualbox without a problem. Performance is really good, and you can adjust the amount of ram and video memory that goes to the virtual machine. I don't really have the need for VT.

Cheers!

Luis Jorge.

---

### Post by David Cartwright on 2008-04-24
At the moment, VirtualBox is a little more polished than KVM, and VirtualBox does not require hardware virtualization support, such as found in the Intel CPUs that incorporate VT.

However, the future belongs to KVM that is already integrated with the Linux kernel and rapidly improving. KVM has strong support from the Linux kernel community, that is one of the reasons why KVM was chosen as the default virtualization technology for Ubuntu 8.04.

If you just want something to work today, VirtualBox is a good solution (Yes, I have tested it too). But if you want sophisticated virtualization features such as live migrations from one piece of hardware to another, then KVM is worth the extra effort and the ease-of-use issues will become a non-issue during the next six months.

However, what is becoming the biggest stumbling block for KVM is the lack of hardware support in the broad range of Intel CPUs that are widely used in notebooks and desktop PCs. On the hand, my experience is that even the low-end AMD CPUs incorporate hardware virtualization that supports KVM. Kudos to AMD and notebook manufacturers that utilize CPUs with hardware virtualization.

---

### Post by unicynic on 2008-05-02
> **mari0 said:**
> hi
//edit: /proc/cpuinfo shows
flags        : fpu **vme** de [...]
on both cores. This should be the Virtualisation Extension, right?

vme is "virtual mode extensions" - for memory managers and multi-tasking OS. The flag for hardware virtualization is **vmx**.

I thought all new intel have VT... and now I just found out that one of the two things I wanted (64bit and VT), I don't have VT in my new notebook with T5550. I should have checked first... grrrr..

---

### Post by David Cartwright on 2008-05-02
> **unicynic said:**
> I thought all new intel have VT... and now I just found out that one of the two things I wanted (64bit and VT), I don't have VT in my new notebook with T5550. I should have checked first... grrrr..

Yup. I filled out Dell's customer feedback form expressing my amazement that they were using Intel 64-bit CPUs that don't support VT.

Notebooks with AMD CPUs are looking like a solution for future purchases since even the low-end AMD CPUs incorporate hardware virtualization technology.

---

### Post by fjgaude on 2008-05-02
> **unicynic said:**
> vme is "virtual mode extensions" - for memory managers and multi-tasking OS. The flag for hardware virtualization is **vmx**.

I thought all new intel have VT... and now I just found out that one of the two things I wanted (64bit and VT), I don't have VT in my new notebook with T5550. I should have checked first... grrrr..

I have a E1505n with Intel T5300 Core Duo, 1.73MHz, and it shows the vme flag. It runs just fine with VMware server.

Hard to believe that Intel even makes a CPU without vme features.

---

### Post by unicynic on 2008-05-10
VMware, VirtualBox, QEMU, and the likes can run ok without **vmx** (vme is not about hardware virtualization...). However, you can't turn on the hardware virtualization support for these virtual machines. KVM, on the other hand, **requires** hardware virtualization (vmx) and if it's not there, it will fallback to QEMU.
I should have bought the Gateway instead... same price as my Lenovo and it also has Vista Premium. Sure, I'd throw it away for Linux but the Lenovo came with IBM PC DOS... How I wished bug no. 1 is resolved and then maybe I could have gotten that Gateway cheaper... We really need to resolve bug no. 1 and then maybe Intel too would look and see the actual need of hardware VT for EVERY cpu model.

---

### Post by jmwjer on 2008-11-03
did you ever find that option in the bios? my virtualbox keeps crashing and i think it may be this option.  i can't see it anywhere :(

---

### Post by bala150985 on 2011-08-27
Today I got to know the hard truth and My system does not support VT-x even though I have a 64 Bit processor under the hood.  

I am not able to run a virutal box under my current guest OS :(.

---

### Post by bala150985 on 2011-08-27
Host Ubuntu -> Run VMPlayer on it -> Run Ubuntu as Guest inside VMPlayer -> Install VirtualBox inside Ubuntu Guest -> Install DSL inside the Ubuntu Guest, work :P

---

### Post by CharlesA on 2011-08-27
Ancient thread is ancient. VBox doesn't need VX/VT to run btw.

---

