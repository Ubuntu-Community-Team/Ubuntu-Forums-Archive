---
title: "VMWare and VirtualBox install"
date: 2008-08-02
forum: Virtualisation
---

### Post by orrorin on 2008-08-02
I've VMWare server already installed on my Hardy-64. Can I also have VirtualBox installed at the same time? The reason I ask is ... each of these installs needs re-compile for kernel and I hope their kernel modules don't interfere with one another. Has anyone done this?

PS:I'm NOT looking to share guest VM's between VMWare and VirtualBox; I just want to try both implementations.

---

### Post by LinuxRocks713 on 2008-08-04
No, they **do not** need you to recompile the linux kernel. They just need to compile a **kernel module** that you load into the kernel.

 To answer your question, yes, you can have both VMWare and Vbox co-exist.

---

### Post by Shazaam on 2008-08-04
Once you get used to making virtual machines in VirtualBox, you CAN run your existing VMware vm's through VirtualBox. When you are making a vbox vm choose "Existing" in the vbox hard drive selection and point it to where your VMware .vmdk is.  So you would choose "My_Virtual_Machine.vmdk" (or whatever your vmware /vmdk is called).
Like this...
1. Start vbox.
2. Go to "New", "Create Virtual Machine".
3. Name your vbox vm, choose your "OS Type".
4. Set your base memory where you want it.
5. Under "Hard Disk" choose "Existing".
6. Click "Add".
7. In "Select a hard disk image file"-"Look in:", browse to your VMware folder and find/highlight the .vmdk file; click "Open".
8. This will get you back to "Virtual Disk Manager". Highlight the disk (.vmdk) you just made and click "Select".
9. Now your back to "Create Virtual Machine". Click "Next".
10. Now you can highlight the new vbox vm, go to settings and configure what you want..
11. Run the vm.
In my experience running a VMware made vm using VirtualBox has not had any ill effects happen to the OS installed on said vm. And, you can install vbox "Guest Additions" on the VMware vm too. :)

---

### Post by orrorin on 2008-08-05
> **LinuxRocks713 said:**
> No, they **do not** need you to recompile the linux kernel. They just need to compile a **kernel module** that you load into the kernel.

 To answer your question, yes, you can have both VMWare and Vbox co-exist.

Thanks for your response and for correcting me! :)

---

### Post by orrorin on 2008-08-05
> **Shazaam said:**
> 
In my experience running a VMware made vm using VirtualBox has not had any ill effects happen to the OS installed on said vm. And, you can install vbox "Guest Additions" on the VMware vm too. :)

Wow! I'm really impressed. I like VMWare because they offer bridged networking; VirtualBox seems to only support NAT and something called 'Host Interface' though I don't quite understand it. But, I like Vbox for their guest additions, particularly "any-sizing" of VM's (your VM can thus have arbitrary resolutions) and seamless windows. Would installing Guest-Additions on VMWare get me these features as well?

---

### Post by LinuxRocks713 on 2008-08-09
> **orrorin said:**
> Wow! I'm really impressed. I like VMWare because they offer bridged networking; VirtualBox seems to only support NAT and something called 'Host Interface' though I don't quite understand it. But, I like Vbox for their guest additions, particularly "any-sizing" of VM's (your VM can thus have arbitrary resolutions) and seamless windows. Would installing Guest-Additions on VMWare get me these features as well?

Installing VMWare Tools would give you any-sizing, but seamless windows are still a work in progress.

---

### Post by orrorin on 2008-08-09
> **LinuxRocks713 said:**
> Installing VMWare Tools would give you any-sizing, but seamless windows are still a work in progress.

Thanks for the tip, I'm able to resize windows in VmWare now.

Here's how to do it in VmWare Server 1.06 ...

```
Goto Edit-->Preferences and click on Display Tab.
**Uncheck the box for "AutoFit Window"** (which is for fitting the VmWare application window to the display settings in the guest OS) and instead 
**check the box for "AutoFit guest"** (which will fit the guest diaply resolution to the size of the VmWare application window).
```

---

### Post by Tichondrius on 2008-10-28
> **orrorin said:**
> Wow! I'm really impressed. I like VMWare because they offer bridged networking; VirtualBox seems to only support NAT and something called 'Host Interface' though I don't quite understand it. But, I like Vbox for their guest additions, particularly "any-sizing" of VM's (your VM can thus have arbitrary resolutions) and seamless windows. Would installing Guest-Additions on VMWare get me these features as well?

RTFM !

Virtualbox also supports bridged networking, which is done using the host interface mode. The only extra step is that you have to do the bridging manually in windows networking control panel (that is, bridge the host interface created by VirtualBox your physical network interface card). It's clearly explained in the manual. VMWare does the bridging automatically, but for me VirtualBox networking setup worked better overall.

---

