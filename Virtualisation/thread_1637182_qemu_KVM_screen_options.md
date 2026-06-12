---
title: "qemu KVM screen options"
date: 2010-12-04
forum: Virtualisation
---

### Post by heatblazer on 2010-12-04
Hello,
Recently I am using a lot qemu/kvm on my ubuntu 8.04. I have an issue with the screen resolutions on the OSes I`ve installed.
ex.
WindwsXP - 1200 x 1024 - max
Ubuntu 10.10  - 800 x 600 max
Fedora - 1024x768 max...
These reses really makes no sense. I am starting kvm that way:

sudo kvm -smp 2 -m 512 -std-vga -soundhw all -usbdevice mouse fedora.img

No idea why the same options gave the different oses different resolutions... Any ideas???

---

### Post by ortayus on 2010-12-04
what model video card are you using for each VM?  I think the default is cirrus but I usually change it to vga to get the most resolution options in the guest OS.

---

### Post by heatblazer on 2010-12-04
> **ortayus said:**
> what model video card are you using for each VM?  I think the default is cirrus but I usually change it to vga to get the most resolution options in the guest OS.

Cirrus too here. Any idea how to change it to better? What are your options???

---

### Post by ortayus on 2010-12-04
If you like GUIs you can install virt-manager, that is the easiest GUI for KVM that I know of.  Then you can go to your guest (while it is not running) and change the video driver from "cirrus" to "vga" and then restart your VM.

If you want to do it through command line then find your guest machine's hardware xml file.  By default I believe you will find it in /etc/libvirt/qemu/*guestname*.xml.  In the <video> tag you will see <model type='cirrus'>.  Change 'currus' to 'vga'.  Once you have changed the .xml file you must redfine your VM.  I would use the command 'virsh define *guestname.*xml'.  Now you can restart your VM.

---

### Post by heatblazer on 2010-12-04
> **ortayus said:**
> If you like GUIs you can install virt-manager, that is the easiest GUI for KVM that I know of.  Then you can go to your guest (while it is not running) and change the video driver from "cirrus" to "vga" and then restart your VM.

If you want to do it through command line then find your guest machine's hardware xml file.  By default I believe you will find it in /etc/libvirt/qemu/*guestname*.xml.  In the <video> tag you will see <model type='cirrus'>.  Change 'currus' to 'vga'.  Once you have changed the .xml file you must redfine your VM.  I would use the command 'virsh define *guestname.*xml'.  Now you can restart your VM.

Are you sure about the libvirt dir? It does not appear such dir in my filesystem... ???

---

### Post by ortayus on 2010-12-06
Do you run your VMs as root or as a user?  I always run mine as root so they are in /etc/.  If you run them as a user then the file is probably somewhere in your /home.

---

### Post by heatblazer on 2010-12-06
> **ortayus said:**
> Do you run your VMs as root or as a user?  I always run mine as root so they are in /etc/.  If you run them as a user then the file is probably somewhere in your /home.

I am starting it as a root. But I can`t locate such dir in my etc folder. Can you be more accurate.

---

### Post by ortayus on 2010-12-07
If you originally created the VM as a non-root user then I think the xml file is somewhere in /home/*userid*.  Probably in a folder called .libvirt/qemu

---

### Post by koala15 on 2011-02-09
Has this been solved ? :confused:

---

