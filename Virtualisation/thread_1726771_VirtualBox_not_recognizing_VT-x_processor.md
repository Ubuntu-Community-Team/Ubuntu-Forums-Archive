---
title: "VirtualBox not recognizing VT-x processor"
date: 2011-04-11
forum: Virtualisation
---

### Post by Fraoch on 2011-04-11
I have a Core 2 Duo E6600 processor which supports VT-x according to this list:

[http://ark.intel.com/VTList.aspx](http://ark.intel.com/VTList.aspx)

However VirtualBox (the Oracle version) does not seem to recognize that the processor supports VT-x.  I tried to install 64-bit Natty in a VM and the installer indicated that the processor architecture was i686, not x86_64, and terminated.  Incidentally the host OS is 64-bit.  Also while other VMs run, Oracle VM Manager indicates that VT-x is not being used or detected.

It's my understanding that a processor that supports VT-x and whose OS is 64-bit will allow the installation of a 64-bit VM.

The logs seem to indicate that VM Manager can't detect virtualization on the processor:

```
VMX - Virtual Machine Technology       = 0 (1)
```

though that's not exactly VT-x.

Any suggestions?

---

### Post by tgm4883 on 2011-04-11
> **Fraoch said:**
> I have a Core 2 Duo E6600 processor which supports VT-x according to this list:

[http://ark.intel.com/VTList.aspx](http://ark.intel.com/VTList.aspx)

However VirtualBox (the Oracle version) does not seem to recognize that the processor supports VT-x.  I tried to install 64-bit Natty in a VM and the installer indicated that the processor architecture was i686, not x86_64, and terminated.  Incidentally the host OS is 64-bit.  Also while other VMs run, Oracle VM Manager indicates that VT-x is not being used or detected.

It's my understanding that a processor that supports VT-x and whose OS is 64-bit will allow the installation of a 64-bit VM.

The logs seem to indicate that VM Manager can't detect virtualization on the processor:

```
VMX - Virtual Machine Technology       = 0 (1)
```

though that's not exactly VT-x.

Any suggestions?

When creating the virtual machine for natty, did you select Ubuntu (64-bit)

---

### Post by CharlesA on 2011-04-11
> **tgm4883 said:**
> When creating the virtual machine for natty, did you select Ubuntu (64-bit)

That was my guess as well. I know I've run into that before.

---

### Post by Fraoch on 2011-04-11
> **tgm4883 said:**
> When creating the virtual machine for natty, did you select Ubuntu (64-bit)

I did feel stupid, because I didn't, but it still doesn't work, see attachment.

Looks like a BIOS issue?

---

### Post by tgm4883 on 2011-04-11
> **Fraoch said:**
> I did feel stupid, because I didn't, but it still doesn't work, see attachment.

Looks like a BIOS issue?

Yea could be a BIOS setting. I know I have that setting in the BIOS of both my work machine and my home machine.

---

### Post by Fraoch on 2011-04-11
Ah yes, that was it!

There was a setting in the BIOS which was disabled.

I set it and it runs fine.

Thanks, and sorry for overlooking the obvious!

---

### Post by tgm4883 on 2011-04-11
> **Fraoch said:**
> Ah yes, that was it!

There was a setting in the BIOS which was disabled.

I set it and it runs fine.

Thanks, and sorry for overlooking the obvious!

Your welcome. Please set the thread to solved.

---

### Post by Fraoch on 2011-04-11
Done.  Thanks again.

---

