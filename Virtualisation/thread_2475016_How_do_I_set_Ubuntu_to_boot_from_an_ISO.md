---
title: "How do I set Ubuntu to boot from an ISO?"
date: 2022-05-13
forum: Virtualisation
---

### Post by Complete on 2022-05-13
I am using Ubuntu 22.04 as a Virtual Machine using VMfware on a Windows 10 Pro host.  I had to increase the disk size and that caused some problems where I need to  use the GParted ISO to boot the Ubuntu VM to partition the virtual disk drive.

So, how do I do that?

---

### Post by TheFu on 2022-05-15
Connect the ISO to a CDROM/DVD virtual device in the guest VM, set that drive to boot first and run/start the VM.

---

### Post by Complete on 2022-05-15
> **TheFu said:**
> Connect the ISO to a CDROM/DVD virtual device in the guest VM, set that drive to boot first and run/start the VM.

I have the ISO file connected to the virtual CD/DVD in the guest VM.  I am using VMware.  I am guessing that this might be a VMware question but how do I set the drive to boot first?

---

### Post by ajgreeny on 2022-05-15
If Vmware is anything like VBox there will be a keypress to choose the device when you see the VMware splash screen.
For VBox it is F12, but I have never used VMware.  However look carefully at the splash screen and it may well tell you which key is needed.

---

### Post by TheFu on 2022-05-15
> **Complete said:**
> I have the ISO file connected to the virtual CD/DVD in the guest VM.  I am using VMware.  I am guessing that this might be a VMware question but how do I set the drive to boot first?

The last time I used VMware Workstation was in the 1990s. My most recent experience was with vSphere and ESXi around 2011, but pretty much every GUI hypervisor has a "Boot" tab to control which connected storage devices are booted from and to control the order.

Google found this: [https://communities.vmware.com/t5/VMware-Workstation-Player/How-to-let-VMPlayer-boot-from-iso-CD-DVD-Change-boot-sequence/td-p/1714348](https://communities.vmware.com/t5/VMware-Workstation-Player/How-to-let-VMPlayer-boot-from-iso-CD-DVD-Change-boot-sequence/td-p/1714348) and this [https://kb.vmware.com/s/article/2011654](https://kb.vmware.com/s/article/2011654)

If you have a paid VMware product and cannot find the answer, perhaps calling the company for the quick answer? After all, with that payment, some level of support should be provided, right?  Just be aware that VMware makes a number of different hypervisor products, so you can't just say "VMware". That isn't specific.

If you aren't stuck using VMware, you'll find that more people in these forums use Oracle's Virtualbox or the native hypervisor for Linux, KVM-QEMU. You may have more luck if you switch to those. Virtualbox runs on Windows - but don't have 2 hypervisors installed at the same time. It will be bad.  Replacing Windows for Linux probably isn't likely, but KVM-QEMU is what almost every VPS host in the world uses today. It has desktop-on-desktop capabilities AND full enterprise server capabilities, with a very wide range of supported hardware, unlike the VMware ESXi, which is fairly restrictive on supported hardware.

---

### Post by ajgreeny on 2022-05-16
Assuming things haven't changed too much in the past few years it looks as if you need to use the Esc key to get to the boot menu in VMware.
See [https://superuser.com/questions/940427/vmware-workstation-how-can-you-boot-from-cd](https://superuser.com/questions/940427/vmware-workstation-how-can-you-boot-from-cd)

---

### Post by MAFoElffen on 2022-06-02
For VMware products, for my own recent experience with, I just know VSphere and ESXi...
> 

[LIST=1]
[*]Shut down the virtual machine. 
[*]Click the virtual machine in the Inventory. 
[*]Right click **Edit Settings**. 
[*]In the Virtual Machine Properties dialog, click the **VM Options** tab. 
[*]Under Boot Options, select the check box for **Force BIOS setup.** 
[*]Click **OK** to save the changes. 
[*]Power on the virtual machine 
[*]Open a VM console and navigate to the BIOS > Boot section 
[*]Make your boot order selection and save 
[/LIST]

Alternately, on startup, if you are trying to get into the BIOS Settings, the hotkey is <F2>, then change the Boot Order of the devices.

---

