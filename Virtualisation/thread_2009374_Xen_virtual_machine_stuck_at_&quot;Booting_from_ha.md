---
title: "Xen virtual machine stuck at &quot;Booting from hard disk...&quot;"
date: 2012-06-24
forum: Virtualisation
---

### Post by DRWhite on 2012-06-24
I have a desktop with Windows XP installed in one partition (/dev/sda1) and Ubuntu 12.04 LTS Server installed in another (/dev/sda2).  I can choose which operating system to run at boot time, and both work.  In Ubuntu, I have installed Xen and Virtual Machine Manager.  I can create a Windows XP virtual machine using a file as the virtual disk, and it works fine.  However, when I try to create a Windows XP virtual machine using /dev/sda1 as the virtual disk, the virtual machine won't start; it's stuck at the message that says "Booting from Hard Disk..."

I know that the Windows XP operating system in /dev/sda1 is good because I can boot it directly (not as a virtual machine).

I know that Xen is working because I can create a virtual disk image, install Windows XP to it, and boot it from within Xen.

I know that I can attach a physical partition to a virtual machine, because I can take my existing virtual machine that boots from a virtual disk image, attach the physical partition as a second virtual disk, and boot it.  From within the virtual OS, I can see the files on the second virtual drive (which is the physical partition /dev/sda1).

The only thing I can not do is boot a virtual machine that uses the physical partition /dev/sda1 as the virtual boot device.  The virtual machine definition is exactly the same -- I just remove the virtual disk image and attach the physical partition, and the virtual machine will not boot.

I even tried to boot into Windows XP directly (not through Xen) and configure it so that it gives me a boot menu when it starts up, so that I can choose to boot into Safe Mode if necessary.  When I try to boot it through Xen, I don't even get to that boot menu.

What else can I try to get this working?

---

### Post by tumik on 2012-06-25
Hi,

I believe I have the same problem. I have also installed Windows without XEN and then try to start the Windows as a XEN HVM domU.

I am getting exactly the same behavior (Stuck in "Booting from hard disk...") when converting a VirtualBox .vdi image to a raw image file, and trying to boot that with XEN (as a HVM domU). The image has Windows 7 installed.
The original image works well in Virtualbox, and I am able to mount partitions from converted image without problems.

When booting, I am getting the following errors in /var/log/xen/qemu-dm-XX.log:
```
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0
I/O request not ready: 0, ptr: 0, port: 0, data: 0, count: 0, size: 0

```
Do you have these same errors?

Log files:
qemu-dm-45.log: [http://pastebin.com/fzuPynDp](http://pastebin.com/fzuPynDp)
xend.log: [http://pastebin.com/t4NfGZHa](http://pastebin.com/t4NfGZHa)

---

### Post by DRWhite on 2012-07-04
I've tracked down the source of this problem to the way the virtual computer sees the disks and partitions and how Windows XP's boot.ini file points to the location of the operating system directory.

When I boot into Windows directly, the physical computer has one hard disk and two partitions, and the Windows operating system is on the first partition of the first disk.  Windows can use the boot.ini file to successfully locate the operating system.

When I boot into Ubuntu, create a Xen virtual machine for Windows, and attach the physical partition as the virtual drive, then the virtual computer has one hard disk that doesn't have a partition table and probably doesn't even have a master boot record, so the virtual computer can't boot, and I'm not sure how Windows would interpret the drives and partitions even if it could.

So I rebuilt my physical machine using this configuration to try to make it work:

    /dev/sda1 - 1GB FAT16 for Windows XP's C: drive
    /dev/sda2 - 1GB ext4 for Ubuntu's /boot
    /dev/sda3 - linux swap partition
    /dev/sda4 - extended partition
    /dev/sda5 - NTFS for Windows XP's D: drive - installing Windows to D:\Windows
    /dev/sda6 - ext4 for Ubuntu's /
    /dev/sda7 - NTFS for Windows XP's E: drive - for user's Documents and Settings
    /dev/sda8 - ext4 for Ubuntu's /home

My hope was that I could use one small physical boot partition and one small virtual boot drive and share the large partition that has the actual Windows installation between the physical machine and the virtual machine.

I installed Windows XP to D:\Windows on the physical machine.  The C: drive contains only the minimum files needed to boot the operating system: boot.ini, ntldr, etc.

I installed Ubuntu 12.04 server on the physical machine and set up everything I needed for Xen.

I created a Xen virtual machine with two virtual disks.  Initially, each disk was mapped to a file in /var/lib/libvirt/images: winxp-c.img (1GB) and winxp-d.img (8GB).  I started the virtual machine and installed Windows similarly to how I installed it on the physical machine: the C: drive contained only the boot files, and Windows was installed to D:\Windows. 

Comparing the two boot.ini files illustrates the difference between how the physical computer sees the drives and how the virtual computer sees the drives, and why it's so difficult to get this to work:

physical boot.ini (one disk, 8 partitions)

    [boot loader]
    timeout=30
    default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
    [operating systems]
    multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

virtual boot.ini (two disks, 1 partition on each disk)

    [boot loader]
    timeout=30
    default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
    [operating systems]
    multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Then I shut down the virtual machine, detached the virtual D: drive, and reattached /dev/sda5 as the virtual machine's second disk.  I was hoping that the virtual C: drive would be able to use the physical D: drive just like the virtual D: drive and that everything would work.  Well, the virtual computer did get past the "Booting from hard disk" message, but then I got this error:

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.

After some more experimenting, I realized that there is still a problem with the virtual drives.  The virtual C: drive is fine; it is still one disk with a master boot record and one partition, so the virtual machine can boot it, but the virtual D: drive (which is mapped to a physical partition), instead of being one disk with one partition, is still one disk without a partition table.  I detached the physical partition, reattached the winxp-d.img file, restarted the virtual machine, and edited the virtual boot.ini file to look like this:

    [boot loader]
    timeout=30
    default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
    [operating systems]
    multi(0)disk(0)rdisk(1)partition(0)\WINDOWS="Microsoft Windows XP Professional (physical disk)" /noexecute=optin /fastdetect
    multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional (virtual disk)" /noexecute=optin /fastdetect

Now when I boot the virtual machine, I get a boot menu, and I can pick the option for the virtual disk when I'm using the virtual disk file as the second virtual drive, and I can pick the option for the physical disk when I'm using the physical partition as the second virtual drive.  The virtual machine can now locate the D:\Windows directory and start the boot process.

Unfortunately, it still doesn't work.  I get to the initial graphical "Microsoft Windows XP" splash screen with the progress bar indicating that Windows is loading, but then I get the infamous blue screen of death: "A problem has been detected and Windows has been shut down to prevent damage to your computer."  That's as much as I can read before the virtual machine turns off and the display goes away.  I suspect the virtual machine doesn't like the video, audio, and network drivers that I installed on the physical machine.  I suppose I could try to install the Windows operating system on the physical partition from within the virtual machine and then boot Windows on the physical machine to see if it works, but I'm about ready to give up on this and just concede that it's not going to work like I want it to work.

---

