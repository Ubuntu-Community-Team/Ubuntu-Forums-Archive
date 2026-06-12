---
title: "Announcing the Release of ChromiumOS64 with Xen Virtualization Support"
date: 2009-12-03
forum: The Cafe
---

### Post by Teo En Ming on 2009-12-03
[U]Announcing the Release of the World's First 64-bit Build of Google's Chromium OS with Xen Virtualization Support

[/U]I have integrated the open source Xen hypervisor 3.4.3 RC1-pre and Jeremy Fitzhardinge's pv-ops dom0-patched kernel 2.6.31.6 into my 64-bit build of ChromiumOS. With the integrated Xen virtualization support, you can now create and run virtual machines or guest operating systems in Google's Chromium OS. If you do not have a need to create virtual machines, you can simply run ChromiumOS64 as a Xen domU virtual machine. 

To run Windows XP, Windows Vista, Windows 7, Windows 2000, Windows Server 2003 and/or Windows Server 2008 as a hardware virtual machine (HVM), you need to have a processor with hardware virtualization support, e.g. Intel VT-x or AMD Pacifica. 

To enable PCI/PCI-e and/or VGA pass-through to HVM virtual machines, you need to have a motherboard with a supporting chipset capable of Intel Virtualization Technology for Directed Input/Output (VT-d). VGA passthrough is more involved and may require you to modify the code to properly support your specific PCI Express x16 graphics card and recompile the Xen hypervisor and Xen tools. 

Download your copy now! Please note that this is a pre-alpha release. 

Download links:

[http://www.chromiumos64.org](http://www.chromiumos64.org)
[http://www.chromiumos64.com](http://www.chromiumos64.com)

---

### Post by Teo En Ming on 2009-12-03
It's a Xen 3.4.3-RC1-pre Type 1 hypervisor Live USB image + 64-bit Google Chrome OS bundled together.

---

### Post by Teo En Ming on 2009-12-03
Featured on Xen's community blog:

[http://blog.xen.org/index.php/2009/12/03/announcing-the-release-of-the-worlds-first-64-bit-build-of-googles-chromium-os-with-xen-virtualization-support/](http://blog.xen.org/index.php/2009/12/03/announcing-the-release-of-the-worlds-first-64-bit-build-of-googles-chromium-os-with-xen-virtualization-support/)

---

### Post by Teo En Ming on 2009-12-04
[SIZE=4]_**Detailed Instructions for Using the Bundled Xen 3.4.3-RC1-pre and 64-bit Google Chrome OS Live USB Image to Create a Fedora 11 Linux PV Virtual Machine/Guest Operating System/DomU**_[/SIZE]

After you have transferred the ChromiumOS64-Xen VMDK image file to a USB external harddisk or an IDE/SATA/SCSI internal harddisk or a USB thumb drive/flash memory (let's say /dev/sdc in this tutorial) using WinImage, and assuming you still have plenty of free space on that same harddisk/thumb drive/flash memory, you may use that free disk space to store the virtual disk images for all of your virtual machines.

# fdisk /dev/sdc

Create a new primary partition. It will be partition number 4. The 64-bit Google Chrome OS will occupy the first 3 partitions on your harddisk.

Type "n" and press enter.
Type "p" and press enter.
Press enter again.

Assuming you have 100 GB free space left on the harddisk, type "+100G" and press enter.

Type "w" and press enter.

# reboot

After rebooting, you need to create a filesystem on /dev/sdc4. In this tutorial, we will use the ext3 filesystem.

# mke2fs -j /dev/sdc4

After completing the above steps, you are now ready to boot into the Bundled 64-bit Google Chrome OS + Xen 3.4.3-RC1-pre hypervisor Live USB.

After displaying the blue graphical login screen with "chromium os", press CTRL+ALT+F2 to switch to virtual terminal 2.

Login as username "chronos" with the password of "enming". 

You are now ready to begin creating and running your very own virtual machines!

First, you need to remount the root filesystem (/) as read-write.

$ sudo mount -o remount,rw /

Uninstall the chromeos-connman package.

$ sudo dpkg -r chromeos-connman

Terminate the connmand and dhclient daemons/processes.

$ sudo kill -9 <process ID of connmand)

$ sudo kill -9 `pidof dhclient`

Start the xend daemon.

$ sudo service xend start

$ sudo xm list

You should see Domain 0 listed. In Windows Server 2008 R2 Hyper-V speak, it is referred to as the parent partition.

$ sudo mkdir /virtualmachines

We will need to mount the free disk space we created earlier to run our virtual machines.

$ sudo mount /dev/sdc4 /virtualmachines

$ cd /virtualmachines

Create a virtual harddisk space of 10G for the Fedora 11 Linux virtual machine.

$ sudo dd if=/dev/zero of=fedora11-pv.img bs=1 count=1 seek=10G

$ sudo mkdir -p /var/cache/apt/archives/partial

We must ensure peth0 is up but without any IP address configured.

$ sudo ifconfig peth0 0.0.0.0

$ sudo ifconfig peth0 down

$ sudo ifconfig peth0 up

Now, we will bring up the ethernet bridge eth0.

$ sudo ifconfig eth0 up

Get a dynamic IP address for the network interface eth0 from your router.

$ sudo dhclient eth0

Install the Apache HTTP web server. This will be required for your virtual machine installation later.

$ sudo apt-get install apache2

Start the Apache HTTP server.

$ sudo /etc/init.d/apache2 start

$ sudo mkdir /var/www/fedora11

Insert the Fedora 11 Linux DVD into your DVD drive and mount it.

$ sudo mount /dev/sr0 /var/www/fedora11

$ cd /var/www/fedora11/images/pxeboot

We will need the kernel image and the initial ramdisk image to pxeboot your virtual machine installation.

$ sudo cp vmlinuz initrd.img /virtualmachines

$ cd /etc/xen

Create the virtual machine configuration file.

$ sudo vi fedora11-pv

Configuration file for Fedora 11 PV virtual machine:

name="fedora11-pv"
memory=1024
disk = ['file:/virtualmachines/fedora11-pv.img,xvda,w' ]
vif = [ 'bridge=eth0' ]
vfb = [ 'vnc=1,vncunused=1,vncdisplay=0,vnclisten=<IP address of your Domain 0>,vncpasswd=' ]
vncconsole=0
#bootloader = "/usr/bin/pygrub"
kernel = "/virtualmachines/vmlinuz"
ramdisk = "/virtualmachines/initrd.img"
vcpus=2
on_reboot = 'restart'
on_crash = 'restart'

Allow incoming VNC and HTTP connections in the firewall.

$ sudo iptables -I INPUT 4 -p tcp --dport 5900 -j ACCEPT

$ sudo iptables -I INPUT 5 -p tcp --dport 80 -j ACCEPT

Change the default firewall policy for the FORWARD and OUTPUT chains to ACCEPT.

$ sudo iptables -P FORWARD ACCEPT

$ sudo iptables -P OUTPUT ACCEPT

Start your virtual machine installation.

$ sudo xm create fedora11-pv

Using a laptop or another computer, vnc into the Fedora 11 installation using a vncviewer.

For example,

$ vncviewer <IP address of Dom0>:<Display Number>

During the Fedora 11 Linux virtual machine installation process, select HTTP or URL as the source of installation. Do not select CD/DVD or any other method.

E.g.,

http://<IP address of Dom0>/fedora11

After you have finished the Fedora 11 Linux virtual machine installation, you need to

$ sudo xm list

$ sudo xm destroy <domain ID of rebooted F11 guest operating system>

Edit the virtual machine configuration file *again*.

$ sudo vi /etc/xen/fedora11-pv

name="fedora11-pv"
 memory=1024
 disk = ['file:/virtualmachines/fedora11-pv.img,xvda,w' ]
 vif = [ 'bridge=eth0' ]
 vfb = [ 'vnc=1,vncunused=1,vncdisplay=0,vnclisten=<IP address of your Domain 0>,vncpasswd=' ]
 vncconsole=0
 bootloader = "/usr/bin/pygrub"
 #kernel = "/virtualmachines/vmlinuz"
 #ramdisk = "/virtualmachines/initrd.img"
 vcpus=2
 on_reboot = 'restart'
 on_crash = 'restart'

You may now start your newly installed Fedora 11 Linux virtual machine.

$ sudo xm create fedora11-pv

You will need to VNC into your virtual machine again.

The above tutorial demonstrates the installation process for a Fedora 11 Linux virtual machine. However, you may also install Windows XP, Windows Vista, Windows 7, Windows 2000, Windows Server 2003, and/or Windows Server 2008 as a HVM virtual machine. Other Linux and UNIX guest operating systems are supported too.

---

### Post by Teo En Ming on 2009-12-04
[SIZE=5][B]Xen slips in Google Chrome OS (sort of)

[/B][SIZE=3]<QUOTE www.virtualization.info>[/SIZE][/SIZE]
Google [didn&#8217;t release yet]("http://googleblog.blogspot.com/2009/11/releasing-chromium-os-open-source.html") its lightweight operating system for netbooks, Chrome OS, and many people already rushed to customize [the early source code]("http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/getting-the-chromium-os-source-code") to create fully-functional images that can [boot inside a virtual machine]("http://lifehacker.com/5408932/chrome-os-virtual-machine-build-ready-for-your-testing") or [on real hardware]("http://en.community.dell.com/blogs/direct2dell/archive/2009/11/25/chrome-os-wi-fi-support-running-on-a-mini-10v-source-code-available.aspx").
  One of these early experiments is particularly interesting for the virtualization community because it modifies the Chromium OS open source code to include Xen.
  The one that released this project, called ChromiumOS64, is Teo En Ming, who hacked the code to support 64bit platforms (the Google code only supports 32bit architectures at the moment because it targets Intel Atom CPUs that powers most netbooks) and integrate Xen 3.4.3 RC1.
   This 64bit Xen-powered Chromium OS build is able to run Windows virtual machines (from XP to 7, including Server 2000, 2003 and 2008) as long as the physical CPU has Intel VT-x or AMD-V. 
It even supports I/O virtualization as long as the CPU has Intel VT-d and the PCI Express graphic card has its drivers included in the build.
  Of course the project is available [for free]("http://www.chromiumos64.com/") and you can even run in from a USB thumb drive.
</QUOTE>


Source: [http://www.virtualization.info/2009/12/xen-slips-in-google-chrome-os-sort-of.html](http://www.virtualization.info/2009/12/xen-slips-in-google-chrome-os-sort-of.html)

---

