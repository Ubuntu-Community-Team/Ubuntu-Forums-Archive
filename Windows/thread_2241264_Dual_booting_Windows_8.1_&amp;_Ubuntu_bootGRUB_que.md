---
title: "Dual booting Windows 8.1 &amp; Ubuntu boot/GRUB query"
date: 2014-08-25
forum: Windows
---

### Post by gaz4 on 2014-08-25
Hiya

I have a dual boot system (Ubuntu and Windows 8.1) and I'd like to have Windows as the primary booting OS, as opposed to Ubuntu/GRUB.  
Can anyone shed any light about how I can implement this to hopefully end up with a screen like this but with 8.1 and Ubuntu when I turn my system on?
[IMG]http://cdn1.groovypost.com/wp-content/uploads/2012/06/Change-Defaults.jpg[/IMG]

---

### Post by oldfred on 2014-08-25
Please attach screen shots not post in line.

Is your Windows 8 installed in UEFI mode?
This is one of many fixes for UEFI systems that only boot Windows. But will let you boot Ubuntu from BCD entry. I believe Windows then changes UEFI one time next boot entry, and shuts down to boot another system.

 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

