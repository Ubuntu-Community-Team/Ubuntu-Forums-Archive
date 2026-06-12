---
title: "Having trouble installing Ubuntu 18.04 VM"
date: 2020-01-31
forum: Virtualisation
---

### Post by sjenyart on 2020-01-31
Hello.

I've been using a Windows 10 host VM for quite a while as a CI test platform for embedded software development.  I recently tried using an FTDI UART/USB cable in an older version of Ubuntu and, despite trying everything I could find in discussions to get it to work, I could not.  So, I decided to get the latest version of Oracle VM VirtualBox and upgrade to a clean installation of Ubuntu 18.04.

First thing I noticed was that installation process seemed to hang up on a black screen indefinitely.  I did a little reading on this and found that a suggestion to disable Hyper-V.  I did so and the process seemed to get further, although I did notice some memory issues along the way.  I am no expert on any flavor of Linux or VMs so I am using all of the default settings in the installation process, with the exception of changing the machine name.

What I am seeing is that the installation looks like it might have finished at a "Live session user" screen.  If I try to log in using the username and password I specified, it does not authenticate.  If I login to the live session user account, I see a shortcut to the installation ISO and a few apps.  If I restart the VM, it restarts the installation.

Wondering if maybe I need to change one of the defaults or if there is some step I am missing.

Thank you.

---

### Post by howefield on 2020-01-31
Thread moved to the "*Virtualisation*" forum, probably a better fit.

---

### Post by bernard010 on 2020-02-04
VM on 18.04 Ubuntu is using the 2.6 VM Kernel it has a lot of bugs attached to it. 
The new 20.04 LTS Ubuntu will have the new 5.3 Kernel, due for release April 2020. 
Ubuntu 19.10 has the current 5.3 VM Kernel.
"12.4.2. Buggy Linux 2.6 Kernel Versions
         The following bugs in Linux kernels prevent them from executing         correctly in Oracle VM VirtualBox, causing VM boot crashes:       

[LIST]
[*]             The Linux kernel version 2.6.18, and some 2.6.17 versions,             introduced a race condition that can cause boot crashes in             Oracle VM VirtualBox. Please use a kernel version 2.6.19 or later.           

[*]             With hardware virtualization and the I/O APIC enabled,             kernels before 2.6.24-rc6 may panic on boot with the             following message:           
Kernel panic - not syncing: IO-APIC + timer doesn't work!  Boot with
apic=debug and send a report.  Then try booting with the 'noapic' option
If you see this message, either disable hardware
            virtualization or the I/O APIC as described"
[https://www.virtualbox.org/manual/UserManual.html#ts_linux-kernelmodule-fails-to-load](https://www.virtualbox.org/manual/UserManual.html#ts_linux-kernelmodule-fails-to-load)

This is the virtual box manual. Hope this helps.
[/LIST]

---

### Post by TheFu on 2020-02-04
> **bernard010 said:**
> VM on 18.04 Ubuntu is using the 2.6 VM Kernel 

Not true.

If you did an install and the next boot shows the install menus again, then perhaps the ISO file is still attached to the VM for booting?  Disconnect it, post install, then reboot pointing at the correct virtual disk device.

No clue what the kernel v2.6.x stuff above is about. Ubuntu hasn't used that in about a decade.  16.04 uses the 4.15.x kernel.

Trying to run 2 hypervisors or have their CPU drivers load concurrently is a bad idea and likely to fail, if not lock up the host machine.

I have never looked for ways to passthrough a serial port to a VM.  USB ports can be passed through pretty easy.
I've never run Win10 or hyper-v. Just not something I'd do, especially as a VM host.

---

### Post by deadflowr on 2020-02-04
Ubuntu 20.04 is already past 5.3 and is currently on 5.4.
I don't know if it'll be rebased to 5.5 or not.
Maybe...

---

### Post by bernard010 on 2020-02-04
Read the Documentation from that I posted from Oracle VM VirtualBox. Yes it is True. Chapter 12.4 Linux and X11 Guests & Chapter 2.3.3.1 of the manual. It is correct, I checked the synaptic package manager. I have no idea why.
 I would guess that the 20.04 will be a new kernel change to 5.5.2 or so.

---

### Post by TheFu on 2020-02-04
> **bernard010 said:**
> Read the Documentation from that I posted from Oracle VM VirtualBox. Yes it is True. Chapter 12.4 Linux and X11 Guests & Chaapter 2.3.3.1 of the manual. It correct I checked the synaptic package manager. I have no idea why.
 I would guess that the 20.04 will be a new kernel change to 5.5.2 or so.

It can be demonstrated as incorrect in a running VM.
```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    **Ubuntu 18.04.3 LTS**
Release:        18.04
Codename:       bionic

$ uname -a
Linux test-1804 **4.15.0-74-**generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```
18.04 uses the 4.15 kernel.

The OP is using Win10 as the host.  Or is there a huge misunderstanding?

---

### Post by bernard010 on 2020-02-04
Contact the VM Package maintainer and express your concerns. I only have their documentation to go by.

---

### Post by bernard010 on 2020-02-04
> Oracle VM VirtualBox and upgrade to a clean installation of Ubuntu 18.04.
This is your current OS for the Host of virtual box, Correct ? 
            > "Live session user" screen.  Is this the Virtual Box Guest OS?
If you start an OS and arrive at the live session, next is to install the OS on the hard drive. On the live screen will be a Install Icon. Click that icon to start the installation.
            >  If I restart the VM, it restarts the installation.  Did you complete the installation of the Guest OS where it will prompt you to Restart the Guest OS and remove install media ?
It should have a restart Icon display after the installation. I am only trying to clarify and understand.

---

