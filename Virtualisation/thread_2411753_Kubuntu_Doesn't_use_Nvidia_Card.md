---
title: "Kubuntu Doesn't use Nvidia Card"
date: 2019-02-03
forum: Virtualisation
---

### Post by revcrussell on 2019-02-03
I have been banging my head on this one for quite a few hours.

I am running Kubuntu 18.10 virtualized with a Gigabyte GV-N210SL-1GI GeForce 210 on passthrough. Shouldn't be a problem there.

The machine sees it:

```
lspci | grep VGA
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
1b:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

```

I installed the driver from the repos:

```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-340
```

I used 340 instead of 390 because supposedly that is the right thing to do.

I built the Xorg.conf like:

```
# cd /etc/X11/
# Xorg -configure
```

I did the following:

```

sudo nvidia-xconfig
sudo reboot
sudo rm -rf /etc/X11/xorg.conf
sudo reboot
sudo nvidia-xconfig
sudo reboot

```

Nothing.

I am going to try and purge the nvidia drivers next, but please if  someone has any ideas. Let me know what logs I can post if required.

---

### Post by TheFu on 2019-02-03
I don't do passthru, but inside the VM, you need to do the normal stuff to have nvidia work.

Did you blacklist the other video driver, so the nvidia driver gets used?

Have you looked at the Xorg.0.log file?  Anything inside it?  

Also, nvidia drivers support a debug option inside the xorg.config file you use.  Mine is named /etc/X11/xorg.conf.d/20-nvidia.conf

```
Section "Device"
    .....
    Option      "ModeDebug"
EndSection
```
I'm using newer drivers, but I have a 1030 GPU.

Also. does lsmod show the nvidia driver loaded?
```
$ lsmod |grep nvid
nvidia_uvm            798720  0
nvidia_drm             40960  2
nvidia_modeset       1040384  3 nvidia_drm
drm_kms_helper        172032  1 nvidia_drm
drm                   401408  5 drm_kms_helper,nvidia_drm
nvidia              17285120  84 nvidia_uvm,nvidia_modeset
ipmi_msghandler        53248  2 ipmi_devintf,nvidia
```

---

### Post by revcrussell on 2019-02-03
do I blacklist the nouveau driver before or after installing the nvidia driver?

like this?
[h=4]2.6.1 Create or edit /etc/modprobe.d/blacklist.conf[/h] Append ‘blacklist nouveau’
 echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf
 [h=4]2.6.2 Edit /etc/sysconfig/grub[/h] Append ‘rd.driver.blacklist=nouveau’ to end of ‘GRUB_CMDLINE_LINUX=”…”‘.
 ## Example row ##
GRUB_CMDLINE_LINUX="rd.lvm.lv=fedora/swap rd.lvm.lv=fedora/root rhgb quiet rd.driver.blacklist=nouveau"
 [h=4]2.6.3 Update grub2 conf[/h] ## BIOS ##
grub2-mkconfig -o /boot/grub2/grub.cfg

## UEFI ##
grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
 [h=4]2.6.4 Remove xorg-x11-drv-nouveau[/h] ## Fedora 29/28/27/26/25/24/23/22 ##
dnf remove xorg-x11-drv-nouveau
 If you have following row on **/etc/dnf/dnf.conf** file, then you can remove it:
 exclude=xorg-x11*
 [h=4]2.6.5 Generate initramfs[/h] ## Backup old initramfs nouveau image ##
mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nouveau.img
 
## Create new initramfs image ##
dracut /boot/initramfs-$(uname -r).img $(uname -r)
 [h=3]2.7 Reboot to runlevel 3[/h] **Note:** You don’t have Desktop/GUI on runlevel 3. Make  sure that you have some access to end of guide. (Print it, use  lynx/links/w3m, save it to text file).
 systemctl set-default multi-user.target

reboot

content of Xorg.0.log: [https://paste.ubuntu.com/p/XFtNcVJ5zB/](https://paste.ubuntu.com/p/XFtNcVJ5zB/)

```
lsmod | grep nvid
nvidia_uvm             36864  0
nvidia              10563584  45 nvidia_uvm
drm                   458752  6 vmwgfx,drm_kms_helper,nvidia,ttm
```

Purging the drivers screwed up boot and so I re-installed fresh.

Installed the drivers from the software driver module. No change. 340 was the version suggested. OS obviously sees the card.

---

### Post by TheFu on 2019-02-03
Yes, install the correct nvidia driver, before the reboot.  

```
# echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf
```
is sufficient. Nothing else should be needed.  Nothing in grub needed. Reboot.
Verify that the line was added to the end of the file.

Ubuntu 15.10 and later don't have "runlevels" anymore. They have "targets."

---

### Post by TheFu on 2019-02-03
Looks like the VMware driver is being picked according to that X...log.  Does that need to be blacklisted too?  That's a virtual machine passthru question.

A few questions.
* what is the hostOS running?
* what hypervisor is being used? Be specific. Vmware made 6 different hypervisors.
* does the machine have 2 GPUs? What are they?

---

### Post by revcrussell on 2019-02-03
> **TheFu said:**
> Looks like the VMware driver is being picked according to that X...log.  Does that need to be blacklisted too?  That's a virtual machine passthru question.

Maybe, I will try it for sure.

I blacklisted nouveau and disabled the virtual VGA. Things still didn't work.

Host OS is ESXi 6.5 U2, I guess vSphere is the hypervisor.
the host has three physical GPU but the guest only has one passthrough. Like I said disabling virtual VGA did nothing.

Really starting to think this is Xorg configuration issue, because I don't have the usual expected conf files.

---

### Post by TheFu on 2019-02-03
ESXi 6.5 U2 is the hypervisor and the hostOS.  vSphere is just a GUI. It doesn't matter.  Time to use that VMware support contract or ask in those forums, I suppose. Sorry, I'm not any help.  We dropped VMware stuff in 2011 and never looked back.  Most of the people here will have Xen or KVM hypervisors or use VirtualBox if they can take the performance hit.  Some Linux gaming forums might help with this too, though I suspect those people won't have VMware stuff either.  Never know until you ask.   Did you check out the virtualization sub-forum here already for any threads?  I'm surprised that a moderator didn't move the entire threat there quickly.

Xorg on normal hardware usually doesn't need any config file, so not having one is actually normal.  The card just needs the driver installed and running - usually blacklisting the other adaptors is sufficient.  
But if the connection from the card to the monitor isn't straight to the monitor, you *may* need to do some extra things, especially if the video signal from the card is changed to a different connector on the other side.  I've had to hand-craft a complete xorg.conf file recently because of a DVI-D conversion to VGA in the last few weeks.  VGA thru a KVM switch to a VGA monitor connector worked perfectly, but DVI-D demands EDID information. the DVI-D-to-VGA adapter wasn't passing the resolution I wanted to the GPU and none of the modes passed were anywhere near close to the monitor capabilities.

If I hadn't been working on that issue here, I'd never have responded to your post.  ;)  It just happens to be fresh in my mind.  Last time I needed to touch an xorg.conf file was probably 2008-ish.  They sorta "just work" these days.

I won't be around the rest of the day - sortof a national holiday here.

---

### Post by revcrussell on 2019-02-03
Thanks for help. I going to try straight ubuntu to see if that works. Every time I uninstall the nvidia driver, it borks the boot process.

Looks like it is a software lock. 
"PCI Passthrough of NVidia cards is usually software-restricted to the  professional Quadro series of cards. Desktop cards will flat out not  work whatsoever if the drivers detect that they are being run inside  virtualization."

---

### Post by howefield on 2019-02-03
Thread moved to the "*Virtualisation*" forum.

---

