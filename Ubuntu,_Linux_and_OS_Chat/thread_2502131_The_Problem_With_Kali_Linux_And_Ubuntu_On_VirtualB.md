---
title: "The Problem With Kali Linux And Ubuntu On VirtualBox Or VMware."
date: 2024-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by loreclove on 2024-11-02
Hello, I'm new on this forum and I don't even think I'll find an use to it. I just want to state a major problem with virtualization these days, because I have been trying to get an estable Kali Linux on VirtualBox and VMware for, I think, weeks. 

I will not write my thoughts, but you may read them.

I have managed to solve the problem. This was my way: forgot VirtualBox, that place was a mess. If not initramfs problems, "Oh no there was a problem" problems. If not, go to any forum and seek solutions, none of which worked. 

Making sudo apt-get update/upgrade is like throwing Kali Linux iso to the bin next time you boot.

Eventually, migrated to VMware, same problems, don't even think, but I could solve it with frsck /dev/sda1 on initramfs and mount/update/dis-upgrade/clean/autoremove/reboot on SMBus Host Not Enabled (Yes! yet another problem with this!).

Enough of sarcasm. I don't know if anyone will read these, I don't know if someone with enough power will do something. But these present year versions of Kali Linux, VirtualBox, and VMware have more problems than solutions. And that can not be.

Thank you for reading me. Good Luck, and excuse my english.

---

### Post by grahammechanical on 2024-11-02
Welcome to Ubuntu Forums but

Kali Linux is nothing to do with Ubuntu. Unless policy has changed I do not think that we are allowed to give help on fixing problems with Kali Linux. Are you using Ubuntu? Are you trying to run Kali Linux in a virtual Machine?

I do not see any connection between your thread title which mentions Ubuntu and your complaints which are about VirtualBox and VMware and also this forum which you do not think you will find a use for.

Some of us a fully able to use Linux and fix problems ourselves. We come on the forum to help others. That is the use some of us find for being on this forum.

Regards

---

### Post by bobby-d-000 on 2024-11-03
Kali is based on <s>Ubuntu but is not an Ubuntu distro<s /> Debian like Ubuntu but is not an Ubuntu distro, similar to Mint is based on Ubuntu but is tweaked enough to be its own thing. If you have issues try downloading VirtualBox directly from Oracle because I spent a couple of minutes of minutes checking the client set-up and was up and going in no time as a enthusiastic novice on a 2015 intel macbook air. They have pre-built distros already set-up for VirtualBox. 

Its real issue is it uses software emulation instead of hardware. For ease of use Gnome Boxes is a godsend for new VMers, Virtual Machine Manager [https://virt-manager.org/](https://virt-manager.org/) is more VirtualBox like but at the machine level, I personally keep them in a dedicated partition and boxes is too simple for my tastes, plus I've also done well with AQEMU.  VirtualBox has known issues with proper USB integration and virt-manager will provide a list of devices to capture while the VM is running, I have to use a wifi dongle to listen on this machine so it's essential for Kali.


Edit: I shouldn't comment before 9am.

---

### Post by coffeecat on 2024-11-03
> **bobby-d-000 said:**
> Kali is based on Ubuntu but is not an Ubuntu distro, similar to Mint.

Let us be clear - Kali Linux is **not** based on Ubuntu.

---

### Post by 1fallen on 2024-11-03
> **coffeecat said:**
> Let us be clear - Kali Linux is **not** based on Ubuntu.

+1 I get tired of hearing that as well:
> **Kali**  Linux is a Linux distribution designed for digital forensics and  penetration testing. [4] It is maintained and funded by Offensive  Security. [5] The software is based on the Debian Testing branch: most  packages **Kali** uses are imported from the Debian repositories.

---

### Post by bobby-d-000 on 2024-11-03
I was thinking of Debian, I fixed it/

---

### Post by lammert-nijhof on 2024-11-05
I run Ubuntu 24.04 LTS in a Virtualbox VM and the reliability has been terrible.  Even now after more that half a year the system still fails from time to time during the boot process. Sometimes after an update it works again somewhat, but after the next update it fails again.  One of the error messages is; "Hypervisor Unknown", which is ridiculous, because I use Virtualbox from 2009 to 2023 without any major problem. In 2024 I had to go back to Ubuntu 22.04 LTS.  

I see 2 bugs and nobody addresses them!
- The easy one is the garbling of the screen during normal operation, you can suppress it by pushing "CTRL+F" 2 times. In the past, I did see this type of garbling with graphical radars screens, if the people tested on 4096 instead of 4095 for the screen size. So I assume initially they are setting the wrong screen size and it is corrected, if you change the screen size, by CTRL+F or by moving the size 1 mm or 2 mm.
- The system gets into boot loop and trying to recover for many many minutes.   Sometimes during the 2nd or 3rd boot the boot succeeds. I use OpenZFS with a large effective memory cache for disk IO, so when more of the code is cached the boot goes faster and the hypervisor is known, before somebody tests the presence of the hypervisor. 

I reported the bug long ago, but it seems to difficult for the maintenance organizations, maybe because too many are involved Canonical for Ubuntu; Oracle for Virtualbox and VMware for the drivers. It looks like they blame each other and do NOTHING. I expect the boot problem occurs especially on slower systems, in my case Ryzen 3 2200G; 3rd gen nvme (3400/2300MB/s) and OpenZFS with all storage and caches lz4-compressed.

---

