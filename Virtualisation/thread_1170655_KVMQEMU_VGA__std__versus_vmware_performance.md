---
title: "KVM/QEMU VGA:  std  versus vmware performance"
date: 2009-05-26
forum: Virtualisation
---

### Post by HDave on 2009-05-26
2 quick questions:

1) Has anybody benchmarked the std driver vs the vmware (SVGA II) driver for performance?

2) I am willing to do this and report back if I could only figure out how to install the Vmware SVGA II driver without loading up all of vmware tools. Any ideas on how to do this?  Currently if I start my WinXP-SP3 vm with the "-vga vmware" all I get after booting is a blank screen.

---

### Post by HDave on 2009-05-26
OK - I found out that if you look at the vm while it is inside vmware, you can go to the c:\program files\vmware\drivers folder and pull out the drivers.

However, once I did this and installed them, kvm *still* gives me a blank/black screen after I boot up...even in safe mode.

Has anybody ever gotten "-vga vmware" to work in kvm on a winxp guest?

---

### Post by HDave on 2009-05-27
HDave -- After sifting through mounds of KVM messages I found [this]("http://www.spinics.net/lists/kvm/msg10189.html") one that basically states that the vmware vga option is only for Linux/Unix guests, not Windows guests.

Same old story, it's always Linux that gets the support and never Windows. ;)

---

### Post by HDave on 2009-05-27
To make a long story short, here is what I found out using the passmark 2d graphics benchmark:

1) the "cirrus" vga emulator is 20% slower than the "std" one
2) The "std" one is 5X slower than vmware workstation

Bottom line for me is that if you need to work all day in a VM, VMware workstation is much snappier than kvm/qemu.  

I believe this is because vmware workstation does not use a software graphics emulator, but rather has some way of directly accessing the video adapter.

---

### Post by hogliux on 2009-12-16
> **HDave said:**
> 2 quick questions:

1) Has anybody benchmarked the std driver vs the vmware (SVGA II) driver for performance?

2) I am willing to do this and report back if I could only figure out how to install the Vmware SVGA II driver without loading up all of vmware tools. Any ideas on how to do this?  Currently if I start my WinXP-SP3 vm with the "-vga vmware" all I get after booting is a blank screen.
Hi,
i had the same problem and it took me ages to find out the solution. Actually your screen is not staying black but not updating correctly. If you switch back and forth between fullscreen and window mode (ctrl+alt+f) you will force an update. The solution is to force continuously updating the screen and luckily this is rather simple: just set the environment variable SVGA_REG_CONFIG_DONE=1

you can do this by typing in:

[FONT=Courier New]export SVGA_REG_CONFIG_DONE=1
qemu -vga vmware ...

[FONT=Arial]Works for me![/FONT]
[FONT=Arial]Hope that helped!!

-hogli
[/FONT][/FONT]

---

