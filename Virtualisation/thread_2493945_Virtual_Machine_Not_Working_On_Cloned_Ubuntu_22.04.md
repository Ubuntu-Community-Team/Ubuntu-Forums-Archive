---
title: "Virtual Machine Not Working On Cloned Ubuntu 22.04"
date: 2023-12-30
forum: Virtualisation
---

### Post by mikegreen8 on 2023-12-30
This is sort of a continuation of my previous Post:
    [https://ubuntuforums.org/showthread....5#post14172305](https://ubuntuforums.org/showthread....5#post14172305)

    With the help of this forum I was able to clone my MBR ubuntu Desktop onto a GPT ESATA.

    I built the ubuntu partition on the ESATA as follows:

    1. Formatted an ESATA as GPT, and allocated an EXT4 partition.

    2. Did a LIVE ubuntu ISO USB install onto the ESATA EXT4 partition

    3. Booting with a USB, I rsync my ubuntu Desktop onto the ESATA EXT4 partition. In order to ensure the ESATA would boot, I Excluded the following files in the rsync command (--exclude-from=FILE). Here is the contents of the Exclude file:
  [SIZE=1]  - /boot
    - /etc/fstab
    - /etc/default/grub
    - /etc/default/grub.d/*
    - /etc/grub.d/*
    - /etc/init.d/grub*
    - /etc/pm/sleep.d/*grub-common
    - /etc/kernel/post*.d/zz-update-grub
    - /lib/systemd/system/grub*
    - /usr/bin/grub*
    - /usr/lib/grub-legacy/*
    - /usr/sbin/*grub*
    - /usr/share/bash-completion/completions/grub*
    - /usr/share/bug/grub-pc/*
    - /usr/share/doc/grub-pc
    - /usr/share/man/man8/grub*
    - /usr/lib/grub/*
    - /usr/sbin/grub*
    - /usr/share/apport/package-hooks/*grub2*
    - /usr/share/bug/grub-common/*
    - /usr/share/grub/*
    - /usr/share/man/man*/grub-*
    - /usr/share/doc/grub-gfxpayload-lists/*
    - /usr/share/grub-gfxpayload-lists/*
    - /usr/share/bug/grub-pc-bin/*
    - /usr/share/lintian/overrides/grub-pc-bin
    - /usr/share/bug/grub2-common/*
    - /usr/share/grub/default/grub*
    - /usr/share/info/grub*
[/SIZE]
4. sudo apt install --reinstall bcmwl-kernel-source (to get wifi working)

5.  Virtual Machine is in its own partition on my Desktop - I rsync the ENTIRE Virtual Machine partition from the Desktop over to a newly created partition on the ESATA.


I BIOS disabled my SATA ubuntu Desktop, and booted the ESATA ubuntu - looks and feels identical to my Desktop - Except Virtual Machine is not working.

When I try to start my Windows 10 Vbox, I get 'Kernel Driver Not installed (rc = -1908)' 

> The virtual box linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by execting 'modprobe vboxdrv' as root.
If your system has EFI Secure Boot enabled, you may also need to sign the kernel modules vboxdrv, vboxnetflt, vboxnetadp, vbocpci before you can load them.
   
Secure Boot is Enabled in the BIOS - it is greyed out so I can't change it, but Virtual machine works on the Desktop ubuntu so this should not matter.

When I boot from the Desktop SATA, VBox works fine. When I toggle over to the ESATA ubuntu I get the error.

I would not like to re-install VBox on the ESATA, as it was a lot of work for me to get a virtual WIN10 working.

Any thoughts ?
M...

---

### Post by deadflowr on 2023-12-30
*Thread moved to **Virtualization***

---

### Post by SeijiSensei on 2023-12-30
> The virtual box linux kernel driver is either not loaded or not set up correctly. Please reinstall virtualbox-dkms package and load the kernel module by execting 'modprobe vboxdrv' as root.
You need to resolve this problem from the command line. Open a terminal,then run
```

sudo apt update
sudo apt install --reinstall virtualbox-dkms
sudo modprobe vboxdrv

```
Now try loading your VM again. Any better? If not, try rebooting.

---

### Post by mikegreen8 on 2023-12-31
Ubuntu 22.04
Virtual Box 6.1, Interface Version 6.1.38_Ubuntu r15343, (Qt5.15.3)

Hi.

I entered your 3 commands as instructed:

```
sudo apt update
sudo apt install --reinstall virtualbox-dkms
sudo modprobe vboxdr
```
         
but got the following error on the last command:
  ```
modprobe: FATAL: Module vboxdr not found in directory /lib/modules/6.2.0-39-generic
```


For the heck of it, I tried Virtual Box and it worked!!

I should have left well enough alone - I realized I had left out the 'v" on 'vboxdr' so I entered the command properly:

```
sudo modprobe vboxdrv
```

I booted and got this message when starting Virtual Box WIN10:

> diagnosing your pc...
your pc did not start correctly
your pc ran into a problem will restart for you


It never restarted.

I then tried entering all 3 commands again (but with vboxdr**v**), booted, and the same problem.

Because of my typo, I found out the 'sudo modprobe vboxdrv' caused my latest problem.

What to do now ?

Thanks,
M....

---

### Post by SeijiSensei on 2023-12-31
What do you see if you run 
```
lsmod | grep vbox
```
Is the driver already loaded? If VirtualBox now starts, you should be fine without running modprobe.

I don't use VirtualBox any more. I prefer the built-in virtualization features that come with the Linux kernel. If you want to give that a try, follow these instructions: [https://www.tecmint.com/install-kvm-on-ubuntu/](https://www.tecmint.com/install-kvm-on-ubuntu/) (It's for 20.04, but it works on later releases as well.)

---

### Post by mikegreen8 on 2023-12-31
sudo lsmod | grep vbox
[sudo] password for mg: 
```
vboxnetadp             28672  0
vboxnetflt             32768  0
vboxdrv               638976  2 vboxnetadp,vboxnetflt
```

I assume I would have to re-install WIN10 if I use the the built-in virtualization features that come with the Linux kernel ?


Thanks,
M....

---

### Post by MAFoElffen on 2023-12-31
> **mikegreen8 said:**
> 
I assume I would have to re-install WIN10 if I use the the built-in virtualization features that come with the Linux kernel ?

No you will not have to do that. If you are talking about KVM, then no.

You can use VboxManage to convert vdi images from vdi to raw... (Depending if you installed from repo or Oracle will affect whether it is vboxmage or VboxManage) Then qemu-img to convert that from raw to qcow2...
```

VboxManage clonehd &#8220;/absolutepath/image.vdi&#8221; &#8220;/absolutepath/image.img&#8221; -format raw
qemu-img -f raw -O qcow2 image.raw image.qcow2

```
Or just cut out Vbox as the middle man completely.

qemu-img can convert vdi images (as well as other formats) directly to raw or qcow2.
```

qemu-img convert -f vdi -O qcow2 image.vdi image.qcow2

```
Then you just create a machine to run it, using that vDisk, with type Windows <Version> as the template OS type.

I've used KVM for over 13 years. I stopped using Vbox about 10 years ago, and never regretted it. There is just so much more you can do with that, once you learn how to use it.

I challenge you to install it and learn how to use it. It costs you nothing but the time to explore and learn. See for yourself. Play around ad use your imagination. Have fun.

If you have question, just ask. There are many here who have a wealth of know here to share.

---

### Post by MAFoElffen on 2023-12-31
Now... To get back to fix what you have going on... Do this:
```

sudo apt update
sudo apt install --reinstall linux-headers-$(uname -r) virtualbox-dkms dkms

```

---

### Post by SeijiSensei on 2024-01-01
lsmod shows the driver is loaded. Does VirtualBox still not work for you?

---

### Post by MAFoElffen on 2024-01-01
Not sure. His last posts described a booting problem with the Win10 VM itself, with if he leaves it to reboot on it's own, should really correct itself (most times) with the boot messages he described.

His last comment was asking about KVM.

---

### Post by mikegreen8 on 2024-01-01
> "I challenge you to install it and learn how to use it. It costs you nothing but the time to explore and learn. See for yourself. Play around ad use your imagination. Have fun."

Okay I'm intrigued and I will take up the challenge - soon. Right now I would like to get my Oracle Vbox working. Then I can play and indeed have fun.

As per your latest post, I tried this:

> 
sudo apt update
sudo apt install --reinstall linux-headers-$(uname -r) virtualbox-dkms dkms


I booted., but to no avail:

> automatic repair - your pc did not start correctly ( I hit 'restart')
your pc ran into a problem - will restart for you

It cannot repair itself.

I did this again:
> sudo lsmod | grep vbox

and as expected, got the same:
> vboxnetadp             28672  0
vboxnetflt             32768  0
vboxdrv               638976  2 vboxnetadp,vboxnetflt


Because of my typo, I found out the 'sudo modprobe vboxdrv' caused my latest problem.

As per your advice, these 2 commands did the trick:

> sudo apt update
sudo apt install --reinstall virtualbox-dkms

but then I went ahead and entered this command:


> sudo modprobe vboxdr

and it caused my problem. Is there a module(s) that I should 're'rsync from the my Desktop ubuntu to undo the damage I caused ?

Pretty amazing forum. I'm impressed with the rapid and insightful responses. 

Happy New Year,
M.....

---

### Post by MAFoElffen on 2024-01-01
If is it tring to boot your Windows and has that error, treat is as if it was any other physical machine, mount a Win ISO, go to repair, and then try  Troubleshoot > Advanced Options > Startup repair.

EDIT: It seems to me like the problem with the Windows Guest having a problem booting may have been a problem with the copy of the large vdisk image file. Maybe try rsuncng that file over again?

---

### Post by mikegreen8 on 2024-01-08
VM WORKS!!!

I re-rsync'd the Virtual Box Partition and it worked.

The pressure is off - so now I will look into Linux Virtual Machine. I'm sure I'll have some questions and I know where to get the answers.

Thank you for your time and patience,
M....

---

