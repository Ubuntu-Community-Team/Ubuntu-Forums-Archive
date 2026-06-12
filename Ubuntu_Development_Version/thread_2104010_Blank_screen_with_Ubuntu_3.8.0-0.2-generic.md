---
title: "Blank screen with Ubuntu 3.8.0-0.2-generic"
date: 2013-01-11
forum: Ubuntu Development Version
---

### Post by nismoryco on 2013-01-11
I upgraded my Acer laptop to Ubuntu 3.8.0-0.2-generic from the Raring repositories today.  I get a blank screen when I boot up with no text or gui.  I can tell that the system is starting correctly and I can access the machine via ssh.  I can get the screen to work if I add 'nomodeset' in /etc/default/grub.  However, doing so prevents me from changing screen brightness from the maximum value.  I tried using 'ubuntu-bug linux-image-3.8.0-0-generic' to submit a bug report, but it is complaining that it is a mainline kernel.  Can someone point me in the right direction to report this bug?  This is a regression from the previous 3.7 kernel.

Thanks,
Ryan

---

### Post by ventrical on 2013-01-11
> **nismoryco said:**
> I upgraded my Acer laptop to Ubuntu 3.8.0-0.2-generic from the Raring repositories today.  I get a blank screen when I boot up with no text or gui.  I can tell that the system is starting correctly and I can access the machine via ssh.  I can get the screen to work if I add 'nomodeset' in /etc/default/grub.  However, doing so prevents me from changing screen brightness from the maximum value.  I tried using 'ubuntu-bug linux-image-3.8.0-0-generic' to submit a bug report, but it is complaining that it is a mainline kernel.  Can someone point me in the right direction to report this bug?  This is a regression from the previous 3.7 kernel.

Thanks,
Ryan


  I just upgraded my Dell D 3100 and I get this EDID error at bootup but then it goes to boot and works normally after that. I had to reset the themes to Ambiance because the desktop was borked .. but not blacked out.

---

### Post by pqwoerituytrueiwoq on 2013-01-11
@op are you using closed source drivers?

reason why i ask:
start here 
[http://ubuntuforums.org/showthread.php?t=2102119#8](http://ubuntuforums.org/showthread.php?t=2102119#8)

---

### Post by nismoryco on 2013-01-11
It is like the screen is shutting off.  It goes from the bios splash to nothing - no text, plymouth, or X.  My system uses nVidia Optimus.  I currently have bumblebee and nvidia-current installed, but it does it without them installed, too.  I think it is happening very early in the boot process.  I created a bug report on bugzilla.kernel.org since I couldn't figure out how to do it with Launchpad.

---

### Post by redkiwi on 2013-01-12
I have the same problem with my ThinkPad SL500 2746-P3G (Intel 4500MHD Graphic).

"Solution":
Install Linux 3.7.2 from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.2-raring/)

Download:
[linux-headers-3.7.2-030702-generic_3.7.2-030702.201301111424_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.7.2-raring/linux-headers-3.7.2-030702-generic_3.7.2-030702.201301111424_amd64.deb")
[linux-headers-3.7.2-030702_3.7.2-030702.201301111424_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.7.2-raring/linux-headers-3.7.2-030702_3.7.2-030702.201301111424_all.deb")
[linux-image-3.7.2-030702-generic_3.7.2-030702.201301111424_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.7.2-raring/linux-image-3.7.2-030702-generic_3.7.2-030702.201301111424_amd64.deb")
[linux-image-extra-3.7.2-030702-generic_3.7.2-030702.201301111424_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.7.2-raring/linux-image-extra-3.7.2-030702-generic_3.7.2-030702.201301111424_amd64.deb")

Install:
sudo dpkg -i *.deb

With Linux 3.7.2 my System boots without any problems.

---

### Post by cariboo on 2013-01-12
There is a kernel update available today 3.8.0-0.3 do you still have the same problem?

---

### Post by nismoryco on 2013-01-13
The problem persists on Ubuntu 3.8.0-0.3-generic.  I am currently using Ubuntu-3.7.0-7.15 without any problems.

---

### Post by cariboo on 2013-01-13
I just upgraded to 3.8.0-03 and rebooted, every thing works ok here:

```
uname -a
Linux redstone 3.8.0-0-generic #3-Ubuntu SMP Fri Jan 11 17:26:08 UTC 2013 i686 i686 i686 GNU/Linux
```

display details:

```
sudo lshw -C display
[sudo] password for cariboo: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GSE Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fe980000-fe9fffff ioport:dc80(size=8) memory:d0000000-dfffffff memory:fe940000-fe97ffff
  
```

and just in case /etc/X11/xorg.conf

```
cat xorg.conf
Section "Device"
  Identifier "Card0"
  Driver "intel"
  Option "AccelMethod" "sna"
EndSection
```

**Note:** this is posted from my Compaq netbook.

---

### Post by nismoryco on 2013-01-13
sudo lshw -C display
```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GK107 [GeForce GT 650M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:d3000000-d33fffff memory:c0000000-cfffffff ioport:5000(size=64)

```

I am also using SNA acceleration with good results so far.

---

