---
title: "Windows 10 not booting after installing Ubuntu 16.04 Xenial"
date: 2017-10-05
forum: Windows
---

### Post by punam on 2017-10-05
Hi all,

I am a newbie in the forum and I am not sure if I am posting in the correct section but please feel to move the post if my posting is at the wrong place.

I was given a laptop by my company for work purposes which came with default OS Windows 10. The hard disk was encrypted using Kaspersky encryption which I had to verify with my password before booting to windows.

Since I love Ubuntu so much, I installed it on one of my existing partition on the same hd. Ubuntu is booting and working just fine. The only problem is I can't get my system to boot into windows which still exists in a different partition.

I've tried boot-repair and did manual entry on grub, to no success. While I still am not bothered about windows not booting up, there are a couple of reasons why I need it to boot. The main reason being some of the applications installed in the windows are enterprise applications and are licensed by the company. I have come to realize that I need to use that application quite often than my expectations.

Can you guys please look into it and suggest if there are any possibilities of recovering booting into windows.

The output from boot-repair is [http://paste.ubuntu.com/25678883](http://paste.ubuntu.com/25678883)

Best Regards,
Suraj

---

### Post by Bucky Ball on 2017-10-06
Welcome. Open a terminal. Paste this in and hit return.

```
sudo update-grub
```

Reboot. Do you now see Win on your grub menu at boot? Are you even getting a selection of kernels/OSs to boot when you start your machine? You should be. If not, hit 'shift' just after boot and that should get you there. (If that doesn't work, try 'escape' key as one is for UEFI installs, the other for legacy and I can't remember which is which and not sure which mode you've installed in.)

---

### Post by punam on 2017-10-06
> **Bucky Ball said:**
> Welcome. Open a terminal. Paste this in and hit return.

```
sudo update-grub
```

Reboot. Do you now see Win on your grub menu at boot? Are you even getting a selection of kernels/OSs to boot when you start your machine? You should be. If not, hit 'shift' just after boot and that should get you there. (If that doesn't work, try 'escape' key as one is for UEFI installs, the other for legacy and I can't remember which is which and not sure which mode you've installed in.)
I 've tried the grub update before as well. Although I can find the partition, it doesn't recognize the windows installation.
```

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-35-generic
Found initrd image: /boot/initrd.img-4.10.0-35-generic
Found linux image: /boot/vmlinuz-4.10.0-28-generic
Found initrd image: /boot/initrd.img-4.10.0-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

The grub Kernels/OS selection menu only displays Ubuntu OS and not the windows option.

---

### Post by QIII on 2017-10-06
Hello!

Did you install Ubuntu in UEFI mode or legacy BIOS?    The fact that there is no /boot/efi partition in your boot repair report suggests that you installed Ubuntu in legacy BIOS mode.

Windows 10 installed by an OEM is typically installed in UEFI mode by default.  If you installed Ubuntu in legacy mode, you won't be able to boot to Windows 10.  In fact, if you installed Ubuntu in legacy mode, you would have gotten a warning to that effect -- something like "Ubuntu found a previous OS installed in UEFI mode.  If you continue to install Ubuntu in legacy mode, you may not be able to boot the other OS."

Do you remember seeing something like that?

Also, for a more concise diagram, could you please post the results of 

```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

```

What we are going to look for is a line like this:

```
sda5 vfat     237M /boot/efi 
```

---

### Post by punam on 2017-10-06
> **QIII said:**
> Hello!
In fact, if you installed Ubuntu in legacy mode, you would have gotten a warning to that effect -- something like "Ubuntu found a previous OS installed in UEFI mode. If you continue to install Ubuntu in legacy mode, you may not be able to boot the other OS."

Hi QIII, I am pretty sure I didn't see the warning mentioned. As far as I remember, it actually mentioned Ubuntu found no previous OS installed or something similar when I was installing it.
```

NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           465.8G            
&#9500;&#9472;sda2        209.1G            
&#9500;&#9472;sda3 ext2   256.1G /          
&#9492;&#9472;sda1          500M            

```
The partition sda2 is where windows installation resides.

---

### Post by ajgreeny on 2017-10-06
If your Windows was in the default hibernation that it goes to if you did not disable fast startup (or whatever it is called) the Ubuntu live system will not be able to read those partitions.

You **MUST** turn that off if you wish to dual-boot.

---

### Post by oldfred on 2017-10-06
You say encrypted Windows. 
That often also adds an encrypted boot loader to MBR and that is then the only way to boot into Windows. Or grub cannot boot encrypted Windows.
Some encrypted Windows have a repair tool to fix boot loader, but you cannot even install/reinstall a standard Windows type boot loader.

Those wanting to dual boot have installed grub2 bootloader to a flash drive or any other hard drive. If flash drive and only boot loader, you can fully use flash drive for data as only MBR is overwritten.

---

### Post by punam on 2017-10-06
> **ajgreeny said:**
> If your Windows was in the default hibernation that it goes to if you did not disable fast startup (or whatever it is called) the Ubuntu live system will not be able to read those partitions.

You **MUST** turn that off if you wish to dual-boot.
This seems to be the reason why grub was unable to detect Windows partition. I've tried to mount the partition but to no success. Is there any way to boot into windows to disable the hibernation?

[QUOTE=oldfred]
[COLOR=#000000]You say encrypted Windows. 
[/COLOR][COLOR=#000000]That often also adds an encrypted boot loader to MBR and that is then the only way to boot into Windows. Or grub cannot boot encrypted Windows.
[/COLOR][COLOR=#000000]Some encrypted Windows have a repair tool to fix boot loader, but you cannot even install/reinstall a standard Windows type boot loader.[/COLOR][COLOR=#000000]
[/COLOR]
[/QUOTE]
Yea there is a kaspersky encryption in place for the windows installation. I am assuming, by now, there is no possible way for me to boot into windows with the current challenges. The best bet will be to hand over my hard drive to the system guys who encrypted the windows and request them to fix the mbr for windows.

---

### Post by oldfred on 2017-10-06
You probably need this, which I only found with Google search on Kaspersky boot repair:
[https://support.kaspersky.com/8092](https://support.kaspersky.com/8092)

Probably cannot be done from Linux, as it has its own  tools to create repair USB flash drive.

---

### Post by punam on 2017-10-10
> **oldfred said:**
> You probably need this, which I only found with Google search on Kaspersky boot repair:
[https://support.kaspersky.com/8092](https://support.kaspersky.com/8092)

Probably cannot be done from Linux, as it has its own  tools to create repair USB flash drive.
I've tried the kaspersky rescue disk and it didn't solve the issue. It can't detect the encrypted partition at the first place so nothing can be done. I've given up this issue is resolvable from my end.

Thanks all for trying though. I appreciate that.

Regards,
Punam

---

### Post by vishu1171vad on 2018-04-14
So what can be done in this case? I have same problem and not able to boot with windows os.

> **QIII said:**
> Hello!

Did you install Ubuntu in UEFI mode or legacy BIOS?    The fact that there is no /boot/efi partition in your boot repair report suggests that you installed Ubuntu in legacy BIOS mode.

Windows 10 installed by an OEM is typically installed in UEFI mode by default.  If you installed Ubuntu in legacy mode, you won't be able to boot to Windows 10.  In fact, if you installed Ubuntu in legacy mode, you would have gotten a warning to that effect -- something like "Ubuntu found a previous OS installed in UEFI mode.  If you continue to install Ubuntu in legacy mode, you may not be able to boot the other OS."


Do you remember seeing something like that?

Also, for a more concise diagram, could you please post the results of 

```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

```

What we are going to look for is a line like this:

```
sda5 vfat     237M /boot/efi 
```

---

### Post by oldfred on 2018-04-14
@vishu1171vad 

Please start your own thread as boot issues are almost always unique. Different hardware, different configurations, etc.

---

