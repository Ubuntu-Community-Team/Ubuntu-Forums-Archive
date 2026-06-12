---
title: "Upgrade to artful has broken VirtualBox raw disk booting of Windows 10"
date: 2017-12-16
forum: Virtualisation
---

### Post by Ramón Casero on 2017-12-16
I have posted this in the VirtualBox forum as [Raw disk booting of Windows 10 broken with Ubuntu artful]("https://forums.virtualbox.org/viewtopic.php?f=2&t=85903#p409055"). As it's not clear whether this is an Ubuntu or VirtualBox issue, for convenience I replicate the issue here.

**Summary:** I had Windows 10 (guest) booting as a raw disk from Ubuntu 17.04 (host). With the upgrade to Ubuntu 17.10 (artful), VirtualBox goes to grub2, instead of booting Windows 10.

**More detail:** I have the following partitions:

[IMG]https://forums.virtualbox.org/download/file.php?id=27627[/IMG]

The machine is a Dell XPS 15. Windows lives in /dev/nvme0n1p3, and Ubuntu in /dev/nvme0n1p7. From linux, I create a raw disk

```
sudo VBoxManage internalcommands createrawvmdk -filename ~/VirtualBox_VMs/win10pro.vmdk -rawdisk /dev/nvme0n1 -partitions 1,2,3,4,5,6

```

This creates files ~/VirtualBox_VMs/win10pro.vmdk and VirtualBox_VMs/win10pro-pt.vmdk.

I change the owner of the files to my regular user, so that VirtualBox can access them

```
sudo chown $USER:$USER VirtualBox_VMs/win10pro*

```

To create the VM:
[LIST=1]
[*]I launch VirtualBox 5.1.30_Ubuntu r118389
[*]Create a new VM named "Windows_10_Pro"
[*]Increase RAM to 8192 MB
[*]"Use an existing virtual hard disk file" -> ~/VirtualBox_VMs/win10pro.vmdk
[/LIST]


In the new VM Settings, I make the following changes

[LIST=1]
[*]System -> Enable EFI (special OSes only)
[*]Display -> Enable 3D Acceleration
[*]Display -> Enable 2D Acceleration
[*]Display -> Video Memory = 256 MB
[*]Storage -> win10pro.vmdk -> Solid-state Drive
[/LIST]


When I click "Start" for the VM, however, it goes to a "GNU GRUB" screen:

[IMG]https://forums.virtualbox.org/download/file.php?id=27629[/IMG]

This was working before upgrading to Ubuntu artful. "Start" would just launch Windows 10. When I saw that it had stopped working, I deleted the VM, created a new one with the steps above, but I still get the GNU GRUB screen.

Although Windows 10 doesn't boot from VirtualBox anymore, I can launch it from the initial dual boot menu when I switch the laptop on. So Windows 10 hasn't broken, and works as before.

Any ideas?

---

### Post by Gavin Fowler on 2018-01-05
I've got the same issue - did you find a work around / resolve?

---

### Post by howefield on 2018-01-05
Thread moved to the "*Virtualisation*" forum.

---

### Post by Gavin Fowler on 2018-01-05
Hi Ramon

It appears the resolve is to create a raw virtualbox disk image for the *entire* disk (rather than stating which partitions to use). So the command becomes: 

```
sudo VBoxManage internalcommands createrawvmdk -filename ~/VirtualBox_VMs/win10pro.vmdk -rawdisk /dev/nvme0n1
```

**NOTE**: As you are allowing access to the whole drive, **very dangerous**, as it will allow you to boot your Ubuntu host as a guest too (with both systems trying to access the same drive).  You **must** make sure that when you boot the virtual machine you select "windows 10" from the grub menu. If you do this, you need to make sure every time you boot your virtual machine, that you choose Windows. It's may be safer to make "windows 10 the default OS to boot (change to windows 10 by setting GRUB_DEFAULT=2, in /etc/default/grub and then run sudo update-grub2, more details can be found [here]("https://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry"))

---

### Post by jazepstein on 2018-01-22
I was having the same problem after upgrading from 17.04 Zesty to 17.10 Artful, and the solution provided in comment 4 above worked (i.e. not specifying any partitions) - thanks Gavin.

However, would be nice if I could reclaim my previous setup, where the Grub screen didn't appear and Windows 10 booted immediately in VirtualBox.

---

### Post by wisedevman on 2018-05-01
I think it's related to grub2 and VBox raw disk. This article could help to solve the issue:

[https://systemoverlord.com/2013/04/04/booting-raw-partitions-in-virtualbox-with-grub2/](https://systemoverlord.com/2013/04/04/booting-raw-partitions-in-virtualbox-with-grub2/)

I didn't try yet because I'm worried that it could damage my windows partition (I have not backup).

What do you think about?

---

### Post by wisedevman on 2018-05-03
I resolved the issue by booting with boot.iso cd created from grub configuration. Safest way!

---

