---
title: "Error when trying to install Win7 64bit guest on ubuntu 13.04 server host using VBox"
date: 2013-05-23
forum: Server Platforms
---

### Post by secure bit on 2013-05-23
Hi,

I have an ubuntu server version 13.04 and got Virtualbox installed on it. Now I am trying to install Windows Ultimate 64 bit as guest. 

Well, I can't. Once the setup reaches about 50% all the services related to virtualbox get frozen and can't become responsive again till I reboot the server.

The Setup : 32GB Host RAM, Guest : 16 GB RAM.

The server logs and screen shows this error when the problem happens :

kernel : ACPI Error: SMBus/IPMI/GenericSerialBus write requires Buffer of length 66, found length 32 (20121018/exfield-299)
kernel : ACPI Error: Method parse/execution failed [\_SB_.PMI0._PMM] (Node ffff880411c4e820), AE_AML_BUFFER_LIMIT (20121018/psparse-537)
kernel : ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _PMM (20121018/power_meter-339)

I've tested the RAM of server previously with ubuntu boot CD and found no problems.

Also apparmor is disabled.

The server got dual Xeon CPUs, HP Proliant ML370 G6.

OS is updated.

Please help.

---

### Post by greenfrog on 2013-05-23
VirtualBox supports 64-bit guest operating systems, even on 32-bit host operating systems, provided that the following conditions are met:

1.-You need a 64-bit processor with hardware virtualization support (see Section 10.3, “Hardware vs. software virtualization”).

2.-You must enable hardware virtualization for the particular VM for which you want 64-bit support; software virtualization is not supported for 64-bit VMs.

3.-If you want to use 64-bit guest support on a 32-bit host operating system, you must also select a 64-bit operating system for the particular VM. Since supporting 64 bits on 32-bit hosts incurs additional overhead, VirtualBox only enables this support upon explicit request.

On 64-bit hosts (which typically come with hardware virtualization support), 64-bit guest operating systems are always supported regardless of settings, so you can simply install a 64-bit operating system in the guest.

---

### Post by secure bit on 2013-05-23
Thanks for your post, Both host and guest are 64 bit, all virtualization technologies are enabled in the BIOS setup.

Still doesn't work.

---

### Post by secure bit on 2013-05-25
Please help !!!

---

