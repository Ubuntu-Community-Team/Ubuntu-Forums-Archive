---
title: "VirtualBox Seamless Mode"
date: 2014-08-23
forum: Virtualisation
---

### Post by ibjsb4 on 2014-08-23
Activating seamless mode in the past has been simple.  Just install guest additions and its there.

However this time its not.

I have VMs set up and working, using both 12o4 and 14o4 with metacity and openbox as window managers.  VB was install from the VB site a few days ago (4.3.14).  Host is Fallback 12o4-kernel 3.2.0.67 and guest are also set up on the latest kernel 12o4/3.2.0.67 and 14o4/3.13-34.60.  Dkms is installed.

I have verified that guest have guest additions installed (ls /opt).  When I run "lsmod | grep -i vbox" I get this:
```
$ lsmod | grep -i vbox
vboxpci                23237  0 
vboxnetadp             25670  0 
vboxnetflt             27612  0 
vboxdrv               409615  6 vboxpci,vboxnetadp,vboxnetflt
```
Am I missing a setting in bios that could do this?  Running a [Xeon x5650 processor]("http://ark.intel.com/products/47922/Intel-Xeon-Processor-X5650-12M-Cache-2_66-GHz-6_40-GTs-Intel-QPI").

---

### Post by ibjsb4 on 2014-08-24
bump

---

### Post by SeijiSensei on 2014-08-24
I'm running KDE 14.04 beta in a fully-updated KDE 14.04 host so YMMV.  I just now installed the extension pack in the guest by downloading the file from the VB download page.  I have an ATI adapter with the fglrx driver and allocated 128 MB for video in the machine settings.

After installing and rebooting the VM the seamless option appears.  [s]A little testing uncovered a problem if the guest's panel is set to auto-hide.  When a notification popped up on the hidden panel, it appeared.  Otherwise moving the mouse to the top of the screen where it was located did not bring the panel down.  This could be a KDE thing, but I have run a Windows VM inside KDE and could hide its panel at the top of the screen without a problem[/s].

I realized I had to have made one of the guest's windows active before trying to bring down the panel.  Once I did that, seamless mode works correctly.

---

### Post by ibjsb4 on 2014-08-24
Does your "lsmod | grep -i vbox" look like mine?

---

### Post by SeijiSensei on 2014-08-24
```

vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               409768  4 vboxnetadp,vboxnetflt,vboxpci

```

The sizes are slightly different but that could reflect kernel differences.  I'm running 3.13.0-34-generic at the moment.

I will say that whether I can get the panel to appear is pretty hit or miss.  My daughter reports similar problems running Kubuntu 14.04 on a Windows 7 host as well.  I have a Konsole window running in the VM.  If I use Alt-Tab to make the VM window active and click on the Konsole window, the panel will appear, but once it's retracted, I can't make it reappear by moving the mouse to the window's edge.

---

### Post by ibjsb4 on 2014-08-24
Thanks, I thought I could be missing something, but not the case.

My panels are fixed position.

Seamless mode is grayed out in "View>Switch to" and "Host + L" does nothing.

I guest I could try the 3.13 kernel.

---

### Post by ibjsb4 on 2014-08-24
I now have the host running the 3.13 kernel and still no seamless mode.

I keep wanting to point a finger at bios.  I'm going to go through it one more time.

---

### Post by ibjsb4 on 2014-08-24
FOUND THE SUCKER !!

I unchecked "Enable Nested Paging" and I now have seamless mode.

[ATTACH=CONFIG]255808[/ATTACH]

---

### Post by SeijiSensei on 2014-08-25
I certainly wouldn't have thought nested paging is the culprit from reading the description of this feature in the VB manual:
> 
A newer feature called "nested paging" implements some memory management in hardware, which can greatly accelerate hardware virtualization since these tasks no longer need to be performed by the virtualization software.

With nested paging, the hardware provides another level of indirection when translating linear to physical addresses. Page tables function as before, but linear addresses are now translated to "guest physical" addresses first and not physical addresses directly. A new set of paging registers now exists under the traditional paging mechanism and translates from guest physical addresses to host physical addresses, which are used to access memory.

Nested paging eliminates the overhead caused by VM exits and page table accesses. In essence, with nested page tables the guest can handle paging without intervention from the hypervisor. Nested paging thus significantly improves virtualization performance.

On AMD processors, nested paging has been available starting with the Barcelona (K10) architecture -- they call it now "rapid virtualization indexing" (RVI). Intel added support for nested paging, which they call "extended page tables" (EPT), with their Core i7 (Nehalem) processors.

If nested paging is enabled, the VirtualBox hypervisor can also use large pages to reduce TLB usage and overhead. This can yield a performance improvement of up to 5%. 

---

### Post by ibjsb4 on 2014-08-25
I marked this thread solved because I now have seamless, but I have other headaches with my vBox installs.

I have not had these problems in the pass.  This is my first box with VT-x and the first time that I have ran 64bit.  I think I now also need a better understanding of whats going on.  Plus ..

I have another install with qemu-kvm and at the moment qemu-launcher.  I think its time for me to move away from vBox.

Thanks for the support :)

---

### Post by ibjsb4 on 2014-08-28
> **ibjsb4 said:**
> FOUND THE SUCKER !!

I unchecked "Enable Nested Paging" and I now have seamless mode.

[ATTACH=CONFIG]255808[/ATTACH]

One last comment and I will put this thread to rest.

I went back and enabled nested paging and found I still have seamless mode.  So what happen?  I really don't know.  Maybe playing with virtual bios kicked something in.  Just don't have a good answer.  I will still play some more with kvm, but ..

[http://ubuntuforums.org/showthread.php?t=2241504&p=13108768#post13108768](http://ubuntuforums.org/showthread.php?t=2241504&p=13108768#post13108768)

---

