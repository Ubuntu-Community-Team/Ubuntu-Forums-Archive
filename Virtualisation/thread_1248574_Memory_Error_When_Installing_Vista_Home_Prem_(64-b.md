---
title: "Memory Error When Installing Vista Home Prem (64-bit)"
date: 2009-08-24
forum: Virtualisation
---

### Post by dharvell on 2009-08-24
I installed VirtualBox 3.0.4 r50677 on my HP Pavilion dv7 running the AMD Turion x2 64-bit processor, 500GB hard drive, 4GB RAM.  I need to run Windows Vista Home Premium (64-bit) within this virtual machine, in order to print and use Photoshop CS3.

When attempting to install Windows Vista, I get the following (Windows) error:

> The instruction at 0x770824a9 referenced memory at 0x00000000. The memory could not be read.  Click OK to terminate the program.The location (such as 0x770824a9) changes each time the error appears.  However, the referenced memory 0x00000000 is consistent.  When OK is clicked, the virtual machine restarts, restarting the installation process, which triggers the error.

Any ideas as to how to successfully install Windows Vista Home Premium 64-bit would be very much appreciated!

---

### Post by olivesandtrees on 2009-08-24
1. Are you running Ubuntu 64-bit for your host OS?
2. Did you allocate the correct amount of RAM needed for Vista in VB (at least 1 GB!)?
3. Did you double check your BIOS to make sure hardware-V is enabled?
5. Do you really need the 64-bit version of Vista virtualized?  What advantages are you getting with that instead of 32-bit?  It's not like you have a need to address more than 4 GB of RAM from you virtual machine.

---

### Post by olivesandtrees on 2009-08-24
Haha I guess I missed my 4th point on there :)

---

