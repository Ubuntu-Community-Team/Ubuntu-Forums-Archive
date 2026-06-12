---
title: "How to install Windows 7 as a KVM Virtual Machine under Ubuntu."
date: 2009-10-16
forum: Virtualisation
---

### Post by bmullan on 2009-10-16
**Purpose:**

Well one reason I do it is now I don't have to have a Dual Boot setup on my machine. 

Now I always boot into Ubuntu initially and if I need Windows running I just goto System Tools - Virtual Machine Manager (or the command line) to start up Windows XP, Vista or Win7.  

Once started it is running concurrently with my Ubuntu Linux so I can easily switch back & forth from Ubuntu to Windows while running applications in BOTH operating systems!  

Better than dual-boot where your choice is run one or the other but NOT both simultaneously.

So whether you currently dual boot to WinXP, Vista or some other Operating System you can now use KVM on Ubuntu

**Installation**

Whether you want to create a KVM Virtual Machine (VM) of WinXP, Vista, WIN7 or any other operating system using both KVM and the KVM Virtual Machine Manager its a pretty simple process.

For the rest of this document assume we have the new Windows 7 (I'll refer to it as WIN7) and you want to install it as a KVM VM under Ubuntu so you can run it side-by-side (concurrently) with Linux.

**Prerequisites:**

You will need either a .ISO image file or a Installation CD/DVD of the Operating System you want to install.   We're going to do Windows 7 here.

                            = = = = = = = = = = = = = = = = = = = =

To install "*KVM*" and the KVM Virtual Machine Manager "*virt-manager*" execute each of the following steps:

Steps:

   1. Boot Ubuntu
   2. Login
   3. click on "*System*"
   4. click on "*Synaptic*"
   5. in the Quick seach window enter: *KVM*
   6. click on/select "*qemu-kvm*"
   7. click on "*mark for installation*"
   8. if prompted for "*Mark additional required changes*"
   9. click on "*Mark*"
  10. in the Quick search window enter: "*virt-manager*"
  11. click on/select "*virt-manage*r"
  12. click on "*mark for installation*"
  13. if prompted for "*Mark additional required changes*"
  14. click on "*Mark*"
  15. click on "*Apply*"
  16. when prompted for "*Apply the following changes?*" 
  17. click on "*Apply*"
  18. click on "*Applications*"
  19. click on "*System Tools*"
  20. click on "*Virtual Machine Manager*"
  21. *right click* on "*localhost (User) qemu Disconnected... etc*"
  22. click on "*Connect*"
  23. **notice -** localhost status goes to "*Active*"
  24. *right click* on "localhost (User) qemu Active... etc"
  25. **notice -** when window pops up enter any name for the new Virtual Machine you want to create.   example:  "*WIN7*"
  26. next if you are installing it from a local CD/DVD select:
          * "*Local install media (ISO image or CDROM)*"
  27. then click on "*Forward*"
  28. **notice -** on the next screen indicate where to load the new OS image.
  29. If you have a .ISO image on your hard drive
          * select "*Use ISO image:*"
  30. elseif you have a CD/DVD in a CD/DVD drive
          * select "*Use CDROM or DVD*"
  31. next to "*OS Type:*"
          *  click on "*Generic*"
  32. and select: "*Windows*"
  33. next to "V*ersion*"
          * select: "*Microsoft Windows Vista*" -- Win7 is largely Vista
  34. click on "*Forward*"
  35. Under "*Choose Memory and CPU settings*"
  36. Enter at least "1024" MB of RAM.. preferably "2048"
  37. If you have multiple CPU like a quad core you can dedicate more than 1 to WIN7 when it is running. (only used if the WIN7 VM is running)
          * **note** WIN7 runs OK with "1"
  38. click on "*Forward*"
  39. I would suggest giving WIN7 at least an initial 32GB (maybe 48 GB) of initial disk space (that can grow).  If you have other local Drives for storage then the WIN7 Virtual Machine can just use those drives for other storage locally.
  40. click on "*Forward*"
          * _before_ you click "*Finish*"...
          * Click on "*Applications*"
          * Click on "*Accessories*"
          * Click on "*Terminal*"
          * **note -** make sure the directory "/var/lib/libvirt/images" has read/write priviliges
          * if it doesn't then enter:  "*sudo chmod 755 /var/lib/libvirt/images*"
  41. click on "*Finish*"
  42. at this point a window from the KVM Virt-Manager will pop up as your WIN7starts to install.   Answer all the questions as if you were installing WIN7 by itself.  
  43. When prompted for: "*Which type of installation do you want?*"
          * "Select "*Custom (advanced)*" --- since you are not upgrading from existing Windows


**notice -** Installing WIN7 will take just as long as if installing on its own, so go get a cup of coffee!"

When the WIN7 installation is complete it will reboot and you can login.

On my system virt-manager puts the .IMG files in /var/lib/libvirt/images

To make sure any Guest OS you install as a Virtual Machine can configure maximum Screen Resolution you can start up your VM from the command line.

On my system I just create a Desktop Launcher (right click on desktop) and make the command to execute:

kvm -vga std -hda /var/lib/libvirt/images/<my OS VM>.img -boot c -m 2048

so for my Windows 7 example this becomes

kvm -vga std -hda /var/lib/libvirt/images/win7.img -boot c -m 2048

Now I can just click the Desktop Icon and start up a copy of Windows 7.   When I log into Windows... I can now change the Screen Resolution to whatever
my Host machine can provide.

**Last note -** to understand some of KVM's magic (see Qumranet's short but sweet white paper:  [http://www.qumranet.com/files/white_papers/KVM_Whitepaper.pdf](http://www.qumranet.com/files/white_papers/KVM_Whitepaper.pdf)) and pay attention to the description of KVM I/O handling for Virtual Machines and it will explain why KVM is such a high-performance virtualization!

Next you will have to spend some time learning how to clone your new WIN7 image, how to save changes to it to make a new/updated image that you can then Clone and run.

---

### Post by fjgaude on 2009-10-17
Thanks for the details... if I can't get VMware Server to run in 9.10, released, I'll use your guide to try to get KVM to work.

One question, can you **copy and paste** text from Windows to Ubuntu and vice versa, using the clipboard?

---

### Post by bmullan on 2009-10-18
> **fjgaude said:**
> Thanks for the details... if I can't get VMware Server to run in 9.10, released, I'll use your guide to try to get KVM to work.

One question, can you **copy and paste** text from Windows to Ubuntu and vice versa, using the clipboard?

I haven't been able to do that yet.
It may just be a configuration issue I don't know about yet as I just started looking through the KVM/qemu standard options.

see [kvm.org Documents]("http://www.linux-kvm.org/page/Documents")

I was able to share drives by installing SAMBA on my Ubuntu host.

I have a wireless HP printer on my home network and I got it working just fine by telling Windows 7 the IP address of the printer.  Win7 then downloaded/installed the correct drivers for the HP c7180.

---

### Post by fjgaude on 2009-10-19
Well, as time goes by, we'll learn what can and can't be done... I await the release of 9.10... it seems to be really, really good.

---

### Post by AldenIsZen on 2009-11-07
I can't see to get it to allow me to create the disk image. I would rather it not be in the place that it is as I only have 15 gigs for Ubuntu, but I figured I could move it once it is created. I don't see a way to create it anywhere but in the location where you said to give it permission. I tried to give it permission with the instructions you provided, but I still get the below error.

```
Unable to complete install '<type 'exceptions.RuntimeError'> Couldn't create storage volume 'Win7.img': 'cannot create path '/var/lib/libvirt/images/Win7.img': Permission denied'
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 1485, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 541, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 628, in _do_install
    self._create_devices(meter)
  File "/usr/lib/python2.6/dist-packages/virtinst/Guest.py", line 601, in _create_devices
    disk.setup(progresscb)
  File "/usr/lib/python2.6/dist-packages/virtinst/VirtualDisk.py", line 611, in setup
    self._set_vol_object(self.vol_install.install(meter=progresscb),
  File "/usr/lib/python2.6/dist-packages/virtinst/Storage.py", line 905, in install
    (self.name, str(e)))
RuntimeError: Couldn't create storage volume 'Win7.img': 'cannot create path '/var/lib/libvirt/images/Win7.img': Permission denied'
'
```

---

### Post by antiram on 2009-11-09
there are virtio net & block driver for windows
[http://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers](http://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers)
[http://www.linux-kvm.com/content/redhat-54-windows-virtio-drivers-part-2-block-drivers](http://www.linux-kvm.com/content/redhat-54-windows-virtio-drivers-part-2-block-drivers)

the block driver is slow on XP.

better graphics with rdp eg.
rdesktop <guest-ip>:3389 -g 1920x1198 -D -K -x 0x80 -u <win-username> -p <win-password>
for fullscreen with 1 pixel at top and bottom for hidden gnome-panels.
but a bridged network is needed for that 3389 port.

---

### Post by mestrini on 2009-11-15
> **AldenIsZen said:**
> I can't see to get it to allow me to create the disk image. I would rather it not be in the place that it is as I only have 15 gigs for Ubuntu, but I figured I could move it once it is created. I don't see a way to create it anywhere but in the location where you said to give it permission. I tried to give it permission with the instructions you provided, but I still get the below error.


That happens because you're not starting the virtual manager with root privileges.
Either open a console and type ```
sudo virt-manager
``` or edit the main menu shortcut with ```
gksu virt-manager
```

cheers

PS:
fully working and at first try on a HP TX2000 by allocating 12GB disk space and 2GB memory
tx to the OP

---

### Post by fatmcgav on 2009-12-06
Hi there, 

Cheers for the instructions - very useful... 

I've hit one issue though - i'm trying to enable hibernation on my Win7 Guest, however when I try to enable hibernation using ```
powercfg /hibernat on
```

However it complains that 'Legacy Drivers are installed: VgaSave' - this appears to be the Graphics driver causing an issue... 

I've enabled 'std' VGA mode, and run in fullscreen... ON checking Device Manager on the Win7 guest, it is showing a warning on the Display adapter... 

Any ideas how I can install a compatible graphics driver? 

Cheers
Gavin

---

