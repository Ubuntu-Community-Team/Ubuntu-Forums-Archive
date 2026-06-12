---
title: "ISSUE: GPU Passthrough with Ubuntu 14.04 -&gt; KVM"
date: 2015-05-01
forum: Virtualisation
---

### Post by Littlewillow on 2015-05-01
I'm looking to set up a box I have at home to run Ubuntu desktop currently running 14.04 version. I have installed KVM, which I will use to create a windows VM that I plan to use for gaming. I have two NVIDIA gpu's that Ubuntu can currently see. As I understand it, to get gpu passthrough to work, I have to blacklist one of the gpu's in Ubuntu so it can be exclusively available to the windows vm.  The issue I've been having, is after trying to blacklist one of my gpu's Ubuntu still seems to be using both. I've listed my terminal commands below. Anyone see anything i'm doing wrong? or perhaps know an alternative method I can try?

I used the command[COLOR=#FF0000] lspci -nn | grep NVIDIA  [/COLOR]to display my available cards. *Below isn't my exact output, just an example*
[COLOR=#FF0000]02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK110B [GeForce GTX Titan Black] [10de:100c] (rev a1)
02:00.1 Audio device [0403]: NVIDIA Corporation GK110 HDMI Audio [10de:0e1a] (rev a1)
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK110B [GeForce GTX Titan Black] [10de:100c] (rev a1)
03:00.1 Audio device [0403]: NVIDIA Corporation GK110 HDMI Audio [10de:0e1a] (rev a1)
[/COLOR]
I then took the ID from the end of the line on the first card "10de:100c" and added it to the initramfs in an attempt to blacklist it.
[COLOR=#FF0000]sudo gedit /etc/initramfs-tools/modules[/COLOR]
** adding the following at the end**
[COLOR=#FF0000]pci_stub ids=10de:100c
[/COLOR]After saving the file, I rebuilt the initramfs with the command [COLOR=#FF0000]sudo update-initramfs -u [/COLOR]and rebooted the system.
After reboot, I tried to check that the cards were being claimed by pci-stub correctly using the command [COLOR=#FF0000]dmesg | grep pci-stub [/COLOR]

Now, to my understanding, I should see a list of devices "claimed by stub" which tells me that they are successfully "removed" from Ubuntu? For me, the above command yields zero results.

If I [COLOR=#ff0000]lspci -nn | grep NVIDIA[/COLOR] it still shows both cards.

I'm relatively new to Ubuntu, so I beg the knowledge of the Linux gods! 

System Specs:CPU : AMD FX-8150 Zambezi 8-Core 3.6GHZ
Motherboard: ASUS Crosshair V Formula-Z 990FX
RAM: 24GB DDR3
GPU1: NVIDIA GeForce GTX 760 2GB GDDR5 (Use for Gaming VM)
GPU2: NVIDIA GeForce 8400GS 1GB DDR3 (Use for Ubuntu)

Thank you for your time and help!

---

### Post by TheFu on 2015-05-01
Did you verify all the other prerequisites where met before starting out?  VT-d and IOMMU support in the BIOS and kernel ... and I think there are kernel patched needed still too.  There is a how-to guide in this forum with 20+ steps.

I'm sure you've reviewed: [http://ubuntuforums.org/showthread.php?t=2111175&highlight=kvm+vga+club](http://ubuntuforums.org/showthread.php?t=2111175&highlight=kvm+vga+club)

[https://en.wikipedia.org/wiki/List_of_IOMMU-supporting_hardware#Nvidia](https://en.wikipedia.org/wiki/List_of_IOMMU-supporting_hardware#Nvidia) has the list of tested GPUs. Neither of yours are on that list. That doesn't say it isn't possible, just that it isn't well-tested.

Oh - and please do not use **sudo gedit** for anything. Use **sudoedit** to avoid issues. The permissions damage may have already been done. You'll want to fix any of those issues ASAP.

---

### Post by Littlewillow on 2015-05-01
How would one verify/fix these permissions damages you speak of?

---

### Post by TheFu on 2015-05-02
> **Littlewillow said:**
> How would one verify/fix these permissions damages you speak of?

Find any files that are owned by root that shouldn't be owned by root and change them back to the correct userid:groupid ownership. Unfortunately, you shouldn't just change all file permissions, since there are some that need to be owned by root for things that demand it - like CPAN installs, port scans (nmap/zenmap), encrypted file systems or aptitude cache files.  Things like that. Setting some of those things to be owned by a normal userid might cause security issues.  OTOH, having some files with root ownership can also be a security issue.

This command will provide a list of *suspect* files.```
find $HOME -user root -ls
```
Look for editor and GUI program config files and directories that are in the list - THOSE are the problems.

As another example, running and managing KVM VMs does not require root.  virsh and virt-manager work great for userids with the correct group permissions, namely they are in libvirtd on the KVM host and on any network-based system running virsh/virt-manager (it isn't necessary to run those tools ON the KVM host machine).

Does this all make sense? Sometimes I'm not good at explaining these things.

---

### Post by KillerKelvUK on 2015-05-02
lspci will always list the PCI devices ubuntu can see regardless of what modules has been loaded for them or not hence your check using this tool to ensure they are effectively blacklisted isn't correct, stick with grep'ing the dmesg output as you should see something like this...

```

[    2.334446] pci-stub: add 10DE:11C8 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.334456] pci-stub 0000:01:00.0: claimed by stub
[    2.334459] pci-stub: add 10DE:0E0B sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    2.334474] pci-stub 0000:01:00.1: claimed by stub

```

I'd recommend changing the way you assign the devices to the pci-stub driver, instead of modifying the modules list in /etc/initramfs-tools/modules I use kernel parameters...I believe this way is considered more robust as the assignment to pci-stub is earlier in the process than your current method.  The how-to is simple... sudoedit /etc/default/grub and append to the "GRUB_CMDLINE_LINUX_DEFAULT=" line your pci-stub ids.  Mine looks like this...

```

GRUB_CMDLINE_LINUX_DEFAULT="intremap=no_x2apic_optout intel_iommu=on pci-stub.ids=10de:11c8,10de:0e0b"

``` 

Regards whether you need to modify your kernel or not for pass-through depends on a few conditions...

[LIST=1]
[*]You need to ensure your gfx card is the only assignable device within the IOMMU group its allocated to.  Use the attached sh script to list your PCI devices by IOMMU group, if your gfx card is the only one in the group your good.  If not there is a good change you need to patch your kernel for ACS Override.
[*]VGA Arbitration is another issue with gfx pass-through, the way to avoid this problem and thus kernel patching is by ensuring your gfx card has an EFI compatible BIOS on it and then configuring your Win7 vm to us OVMF/EFI for boot instead of the default seabios.
[/LIST]

[ATTACH]261712[/ATTACH] - Not of my creation, I've pinched someone else's work but can't recall who to credit them sorry.

[http://vfio.blogspot.co.uk/2014/08/iommu-groups-inside-and-out.html](http://vfio.blogspot.co.uk/2014/08/iommu-groups-inside-and-out.html)
[http://vfio.blogspot.co.uk/2014/08/whats-deal-with-vga-arbitration.html](http://vfio.blogspot.co.uk/2014/08/whats-deal-with-vga-arbitration.html)

---

### Post by KillerKelvUK on 2015-05-02
Once you have pass-through working you may struggle with the Windows driver for NVIDIA cards on Ubuntu 14.04 if you have the stock KVM and QEMU packages installed.  If I recall the stock qemu version is pre 2.1.0 (or 2.1.1 I don't recall properly) which doesn't incorporate some KVM module options needed to spoof the NVIDIA drivers into working...the problem is the drivers detect KVM and don't load properly and Windows reports a driver error code=43 (I think, could be code=12).  My rig was working on Ubuntu 14.10 which does incorporate the minimum version levels required, obviously if you're building your own binaries from source you may very well have addressed this problem.

[http://www.linux-kvm.org/wiki/images/b/b3/01x09b-VFIOandYou-small.pdf](http://www.linux-kvm.org/wiki/images/b/b3/01x09b-VFIOandYou-small.pdf) - Check this out for a summary of the driver problems and KVM options necessary to address.

---

