---
title: "Need help getting started with VirtualBox"
date: 2009-10-06
forum: Virtualisation
---

### Post by DFord425 on 2009-10-06
Im trying to setup a vitrual machine but i keep getting this error. Im not sure what it means, can someone help me understand what it means. It says:
[I]Failed to start vitrual machine Windows7
VT-x is not available.  (VERR_VMX_NO_VMX)
Unknown error creating VM (VERR_VMX_NO_VMX).[/I]

Thanks in advance.

---

### Post by ceylonerana on 2009-10-07
What is the VirtualBox software do you use? Is it Sun VirtualBox or VMware product?

---

### Post by aesis05401 on 2009-10-07
Hello, 

VT-x is hardware assistance for running VMs.  I do not have a VirtualBox install available to look at, but there should be a check-box in the VM options to enable/disable VT-x.  

Your machine may have VT capability - you have to turn it on in the BIOS usually.

---

### Post by SoftwareExplorer on 2009-10-07
I think it mean that you have to turn on 'virtualization features' or 'VT-x' in the bios. To get into the bios it will say something like press del to enter setup when you first turn your computer on.

---

### Post by DFord425 on 2009-10-07
I have you change the settings in the physical machine, right?

---

### Post by howefield on 2009-10-07
Try editing the machines's xml file, (probably inside your .Virtualbox/Machines/Windows folder)

```
<HardwareVirtEx enabled="true"/>
```

change to

```
<HardwareVirtEx />
```

Backup the file before editing, in case you mess it up.

---

### Post by SoftwareExplorer on 2009-10-07
> **DFord425 said:**
> I have you change the settings in the physical machine, right?

If the problem is that you need to set the bios then you would have to reboot the physical machine.

---

### Post by DFord425 on 2009-10-07
> **howefield said:**
> Try editing the machines's xml file, (probably inside your .Virtualbox/Machines/Windows folder)

```
<HardwareVirtEx enabled="true"/>
```

change to

```
<HardwareVirtEx />
```

Backup the file before editing, in case you mess it up.

I tired this and it seemed to fix that error. But now im getting another error:
[I]VT-x/AMD-V hardware acceleration has been enabled, but is not operational. Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot.
Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.[/I]
It seems like this has to be fixed in the BIOS. I will give that a try now.

---

### Post by aesis05401 on 2009-10-07
Have you determined whether your hardware supports it?  Is your host OS install a 64 bit install?

---

### Post by DFord425 on 2009-10-08
Yes, I was able to install the OS. I still got the error, but i was still able to run VirtualBox and install the OS.

---

