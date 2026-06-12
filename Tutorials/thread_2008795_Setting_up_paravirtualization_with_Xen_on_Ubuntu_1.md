---
title: "Setting up paravirtualization with Xen on Ubuntu 11.10"
date: 2012-06-23
forum: Tutorials
---

### Post by WitchCraft on 2012-06-23
This tutorial is about how to paravirtualize an Ubuntu 12.04 guest on a Ubuntu 11.10 host.
 
Now before you study this tutorial, if you don't really need paravirtualization, because the processor of your computer/noteboox supports virtualization, I strongly recommend you leave Xen be and use VirtualBox instead. It's just that much easier.
 
If you're unsure what kind of processor your machine has, just open a console and type
```

/proc/cpuinfo

```
 
And in combination with Google, you will know all you have to know about your processor, even if you initially hadn't the slightest idea what kind of processor you actually have.
 
In order to right away know whether your processor supports hardware virtualization, open a console and grep for vmx (Intel VTx) or smv (AMD-v)
```

egrep '(vmx|svm)' /proc/cpuinfo

```
 
 
If the above command returns "vmx" (Intel) or "svm" (AMD), possibly amongst other results, then your CPU supports hardware acceleration, and you can use VirtualBox. If not, then either your processor doesn't support hardware acceleration, or the option in the BIOS is switched off.
 
If there isn't any such option - then you can't really use VirtualBox (either that, or it uses software virtualization, and then it will be so damn slow that you can just leave it be right away).
 
 
However, you can still use virtualization.
But not the normal hardware(-accelerated) virtualization, only the much more difficult paravirtualization.
 
So first things first: 
Paravirtualization requires a modified Guest and Host operating system. Modified because it needs some drivers for paravirtualization. 
 
In other words: Since Linux-drivers are in the kernel, both the guest and the host must have a Xen Linux kernel. As of Linux-kernel 3.0, Xen is in the mainstream kernel. So both the Ubuntus 11.10 and 12.04 support paravirualization.
 
 
 
Since I built my server myself with the cheapest and most power-preserving hardware (Intel Atom), it didn't come at too much of a surprise to me that it didn't support hardware acceleration.
 
So unfortunately, that meant I needed to use Xen.
Now the catch-22 is not that it's that difficult, but when I tried, I had to gather all the necessary infos from no less than about 20 different sites (not an exaggeration).
 
So I thought I would do everybody else a favour (especially myself if I have to do this again later when I reinstall and have everything forgotten), and write a tutorial here:
 
 
First, we need to install all dependencies
```

sudo apt-get install xen-hypervisor-4.1-amd64 xen-utils-4.1 xenwatch xen-tools xen-utils-common xenstore-utils virtinst virt-viewer virt-manager

```
 
 
Then, open a console, and type:
```

gksu geany /etc/xen/xend-config.sxp

```
and append this at the end of the file:
```

(xend-http-server yes)
(xend-unix-server yes) 

```
 
If you don't append (xend-http-server yes), then Xen will work, but the virt-manager GUI will not.
 
 
Also in this file, if you want bridged networking (that the IP of the VM is visible in the entire network, for example because it's to become your webserver), do this:
```

#(network-script 'network-bridge netdev=wlan0')
(network-script 'network-bridge netdev=eth0')

```
and set vif-script to
```

(vif-script vif-bridge)

```
 
 
Also, for bridged-mode networking, you need to bridge the network.
So to create a new virtual network adapter, edit /etc/network/interfaces
and add this:
```

auto xenbr0
iface xenbr0 inet dhcp
    bridge_ports eth0

```
Save the file and close geany.
 
Then you need to create a symlink to /usr/lib/xen-<your version here> in /usr/lib64/xen
```

ln -sf /usr/lib/xen-4.1 /usr/lib64/xen

```
 
 
Reboot, and test if you are on a Xen System:
```

xm dmesg

```
 
If you get this:
> 
WARNING! Can't find hypervisor information in sysfs!
Error: Unable to connect to xend: No such file or directory. Is xend running?

 
Then it's not as bad as it sounds.
Apparently, the .deb package missed to move the config file in /etc/grub.d/ (it does).
 
 
 
So just update grub to start with the xen option first, then update grub
```

sudo mv /etc/grub.d/10_linux /etc/grub.d/50_linux
update-grub2

```
 
 
 
Then restart and do xm dmesg again, and you should get:
> 
root@amdvision:~# xm dmesg
(XEN) Xen version 4.1.1 (Ubuntu 4.1.1-2ubuntu4.2) (stefan.bader@canonical.com) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) Mon Jun 18 14:06:58 UTC 2012
(XEN) Bootloader: GRUB 1.99-12ubuntu5
(XEN) Command line: placeholder
(XEN) Video information:
(XEN) VGA is text mode 80x25, font 8x16
(XEN) VBE/DDC methods: V2; EDID transfer time: 1 seconds
(XEN) Disc information:
(XEN) Found 1 MBR signatures
(XEN) Found 1 EDD information structures
(XEN) Xen-e820 RAM map:
(XEN) 0000000000000000 - 000000000009f800 (usable)
(XEN) 000000000009f800 - 00000000000a0000 (reserved)
(XEN) 00000000000e0000 - 0000000000100000 (reserved)
(XEN) 0000000000100000 - 00000000de59d000 (usable)
(XEN) 00000000de59d000 - 00000000de79d000 (ACPI NVS)
(XEN) 00000000de79d000 - 00000000df70d000 (usable)
(XEN) 00000000df70d000 - 00000000dfb16000 (ACPI NVS)
(XEN) 00000000dfb16000 - 00000000dfd3f000 (usable)
(XEN) 00000000dfd3f000 - 00000000dfdbf000 (reserved)
(XEN) 00000000dfdbf000 - 00000000dfebf000 (ACPI NVS)
(XEN) 00000000dfebf000 - 00000000dfef7000 (ACPI data)
(XEN) 00000000dfef7000 - 00000000dff00000 (usable)
(XEN) 00000000f8000000 - 00000000f9000000 (reserved)
(XEN) 00000000fec00000 - 00000000fec01000 (reserved)
(XEN) 00000000fec10000 - 00000000fec11000 (reserved)
(XEN) 00000000fee00000 - 00000000fee01000 (reserved)
(XEN) 00000000ffe00000 - 0000000100000000 (reserved)
(XEN) 0000000100000000 - 0000000220000000 (usable)
(XEN) ACPI: RSDP 000FE020, 0024 (r2 TOSQCI)
(XEN) ACPI: XSDT DFEF6120, 005C (r1 TOSQCI TOSQCI00 3 1000013)
(XEN) ACPI: FACP DFEF5000, 00F4 (r4 TOSQCI TOSQCI00 3 MSFT 1000013)
(XEN) ACPI: DSDT DFEE2000, F6C5 (r1 TOSQCI TOSQCI00 F0000000 MSFT 1000013)
(XEN) ACPI: FACS DFE9C000, 0040
(XEN) ACPI: HPET DFEF4000, 0038 (r1 TOSQCI TOSQCI00 1 MSFT 1000013)
(XEN) ACPI: APIC DFEF3000, 0084 (r2 TOSQCI TOSQCI00 1 MSFT 1000013)
(XEN) ACPI: MCFG DFEF2000, 003C (r1 TOSQCI TOSQCI00 1 MSFT 1000013)
(XEN) ACPI: BOOT DFEE1000, 0028 (r1 TOSQCI TOSQCI00 1 MSFT 1000013)
(XEN) ACPI: SLIC DFEE0000, 0176 (r1 TOSQCI TOSQCI00 1 MSFT 1000013)
(XEN) ACPI: SSDT DFEDF000, 088C (r1 AMD POWERNOW 1 AMD 1)
(XEN) System RAM: 8182MB (8379256kB)
(XEN) Domain heap initialised
(XEN) Processor #0 0:5 APIC version 16
(XEN) Processor #1 0:5 APIC version 16
(XEN) Processor #2 0:5 APIC version 16
(XEN) Processor #3 0:5 APIC version 16
(XEN) IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
(XEN) Enabling APIC mode: Flat. Using 1 I/O APICs
(XEN) Table is not found!
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Detected 1795.571 MHz processor.
(XEN) Initing memory sharing.
(XEN) AMD-Vi: IOMMU not found!
(XEN) I/O virtualisation disabled
(XEN) ENABLING IO-APIC IRQs
(XEN) -> Using new ACK method
(XEN) Platform timer is 14.318MHz HPET
(XEN) Allocated console ring of 16 KiB.
(XEN) HVM: ASIDs enabled.
(XEN) SVM: Supported advanced features:
(XEN) - Nested Page Tables (NPT)
(XEN) - Last Branch Record (LBR) Virtualisation
(XEN) - Next-RIP Saved on #VMEXIT
(XEN) HVM: SVM enabled
(XEN) HVM: Hardware Assisted Paging detected.
(XEN) do_IRQ: 1.231 No irq handler for vector (irq -1)
(XEN) do_IRQ: 2.231 No irq handler for vector (irq -1)
(XEN) Brought up 4 CPUs
(XEN) do_IRQ: 3.231 No irq handler for vector (irq -1)
(XEN) mtrr: your CPUs had inconsistent fixed MTRR settings
(XEN) Xenoprofile: AMD IBS detected (0x0000001f)
(XEN) *** LOADING DOMAIN 0 ***
(XEN) Xen kernel: 64-bit, lsb, compat32
(XEN) Dom0 kernel: 64-bit, PAE, lsb, paddr 0x1000000 -> 0x2043000
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN) Dom0 alloc.: 0000000210000000->0000000214000000 (2007682 pages to be allocated)
(XEN) Init. ramdisk: 000000021cac8000->000000021ffffc00
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN) Loaded kernel: ffffffff81000000->ffffffff82043000
(XEN) Init. ramdisk: ffffffff82043000->ffffffff8557ac00
(XEN) Phys-Mach map: ffffffff8557b000->ffffffff86506dd0
(XEN) Start info: ffffffff86507000->ffffffff865074b4
(XEN) Page tables: ffffffff86508000->ffffffff8653f000
(XEN) Boot stack: ffffffff8653f000->ffffffff86540000
(XEN) TOTAL: ffffffff80000000->ffffffff86800000
(XEN) ENTRY ADDRESS: ffffffff81cd0200
(XEN) Dom0 has maximum 4 VCPUs
(XEN) Scrubbing Free RAM: .done.
(XEN) Xen trace buffers: disabled
(XEN) Std. Loglevel: Errors and warnings
(XEN) Guest Loglevel: Nothing (Rate-limited: Errors and warnings)
(XEN) Xen is relinquishing VGA console.
(XEN) *** Serial input -> DOM0 (type 'CTRL-a' three times to switch input to Xen)
(XEN) Freed 224kB init memory.
(XEN) traps.c:2388:d0 Domain attempted WRMSR 00000000c0010004 from 0x0000edfd3eb45b3e to 0x000000000000abcd.
root@amdvision:~# 

 
BTW info - the log files are here:
```

/var/log/xen/xend.log
/var/log/xen/qemu-dm-demo.log

```
 
 
 
 
WARNING: The machine might hang when you restart with the xen kernel (you're locked out if you're connected via ssh...):
> 
Primary Master Hard Disk S.M.A.R.T. Status Bad. 
WARNING: Immediately back-up your data and replace your hard disk drive.
 
Press F1 to continue

 
And as this is a BIOS message, you cannot handle it via ssh...
So connect to the physical machine, press F1, enter the BIOS setup, and switch off (not so) "S.M.A.R.T.".
Afterwards, the system will reboot just fine.
 
 
Now, you should be able to start virt-manager (admin GUI).
So on gnome-terminal, type 
```

virt-manager

```
 
Now in virt-manager, click on new, click from network
and use this URL for 64 Bit Ubuntu 12.04:
```

http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/

```
(for 32 bit it's installer-i386 instead of installer-amd64, and note that amd64 is also correct for x86-64 intel processors, just in case...)
 
 
In the last setup, leave NAT in and make sure virtualization mode is on paravirtualization (should be that by default).
 
Now it should take some time to create a virtual machine, then it will start a black window and start the installation.
 
However, it's buggy so the screen will remain black.
So close the black screen and virt-manager.
 
 
 
 
 
Now create a directory in your home directory, and call it as you please, e.g. "xensucks" (i recommend no non-ASCII characters and no whitespaces in neither the directory nor the username)
```

mkdir -p /home/username/xensucks    

```
 
 
Get the kernel, initrd, and xen config
These files are required:
```

wget http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/xen/xm-debian.cfg
 
wget http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/xen/initrd.gz
 
wget http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/xen/vmlinuz

```
 
 
and get the file name of your previous failed attempt. 
Be default, it resides in
```

/var/lib/libvirt/images/

```
 
 
Then go into your xensucks directory, and open 
```

xm-debian.cfg

```
 
edit memory, name and disk parameters to your liking.
 
The disk parameter should point to your image created in the previous failed attempt.
 
 
Note that if you use the same name parameter as you used to create the .img file, you will get an error, saying this name already exists. So just append a 1 to it, problem solved.
 
 
In my case, the name of the image that failed was websrvtest, so I used this configuration:
```

memory = 1024
name = "websrvtest1"
disk = ['file:/var/lib/libvirt/images/websrvtest.img,xvda,w']

```
Save and close xm-debian.cfg
 
Start the actual installation process:
```

xm create -f xm-debian.cfg -c install=true install-kernel="/root/xensucks/vmlinuz" install-ramdisk="/root/xensucks/initrd.gz" install-mirror="http://ca.archive.ubuntu.com/ubuntu" install-arch=amd64 install-method=network

```
 
(where you need to substitute /root/xensucks with /home/YOUR_USERNAME/xensucks, if you don't work as root)
 
Follow the normal installation process and restart.
When you restart, it will crash.
Nothing unusual, it always does on the first restart.
 
BTW this won't help
```

/etc/init.d/xend restart
/etc/init.d/networking restart

```
 
So just reboot the main machine.
If it still doesn't work, reboot again.
 
Once rebooted, open virt-manager, and right-click your virtual machine, start it, wait a few seconds, then right-click again and select open.
 
You should see the login prompt of your newly created VM.
Once you're finished and see saw that it worked, stop the vm.
 
Right click the shut-down machine again, click on open.
Click on the info icon, and select the network card configuration (NIC:xxxxxx)
set the bridge name to xenbr0, and click apply.
 
Then restart the VM. If it doesn't work, restart the the host.
If after restart, you log-in to your vm, you will see it now has a IP from the DHCP server, and it's publicly accessible from every machine inside your home network.
 
BTW, take a look at "Boot Options". 
There you can click "Start virtual machine on host boot-up".
 
 
Additional information for wlan:
You can use brctl in package bridge-utils to set up bridges:
 
```

brctl addif xenbr0 eth0
brctl show

```
 
If you use wlan instead of ethernet, theoretically it should suffice to do this:
```

brctl addif xenbr0 wlan0
brctl show

```
 
However, you will probably get:
```

can't add wlan0 to bridge xenbr0: Operation not supported

```
 
This is because with kernel >= 2.6.33, you cannot bridge a wireless interface in managed mode at all unless you enable 4addr mode. 
 
So the solution is to switch 4addr to on.
This can be done with the iw package.
```

iw dev wlan0 set 4addr on

```
 
However, the version of iw in the Ubuntu repository (0.9) is very old (several years actually), so you will get a syntax error.
 
So kindly download the latest version (3.4 at the time of writing) of iw from:
```

http://linuxwireless.org/download/iw/

```
 
and unpack the sources to a directory of your chosing,
and in there, type 
```

make

```
 
and when it compiled without error (it did on my machine), then install it
```

make install

```
 
Now you should be able to do
```

iw dev wlan0 set 4addr on

```
 
 
If your network starts to act wired, you can shut it off again with
```

iw dev wlan0 set 4addr off

```
 
 
Now you can do
```

brctl addif xenbr0 wlan0

```
 
And
```

brctl show

```
will show that the interface is now bridged.
 
Theoretically it should work now, but instead the entire wireless connection breaks down and you cannot access the internet from neither host nor guest.
 
I guess this is either a kernel or a gnome network-manager malfunction, and I haven't yet found a solution to this.
So if you use wireless LAN with Xen, you just have to stick to NAT. That works without problems.
 
However, NAT sucks because you cannot access your virtual machine from any other machine than the host.
 
It sucks because that way there is no way to look at the hosted websites (on my development computer) with another browser from another computer (eg. Internet Explorer 9/10 from a windows machine), which I can assure you is quite fatal, especially if unchecked in the long run.

---

### Post by WitchCraft on 2012-06-29
I hope it is better in 12.04, as in 11.04, it crashes the host operating system often. Every time on laptop standby, and every second time on server restart...

---

