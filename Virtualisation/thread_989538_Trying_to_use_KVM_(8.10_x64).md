---
title: "Trying to use KVM (8.10 x64)"
date: 2008-11-21
forum: Virtualisation
---

### Post by Dan1317 on 2008-11-21
Hello I am trying to impress my boss with KVM.  Sadly I cannot get it to work.  I have followed the steps in the mega thread and in the ubuntu KVM wiki.  Still I am missing something.  Here's what I have so far.  I installed ubuntu-virt-server and ubuntu-virt-mgmt.  I added myself as a user to libvirtd group (And logged out)

here is what my /etc/network/interface is:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
#auto lo
#iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

#Above has been disabled by DAN, uncomment auto lo and auto eth0 to return to factory setting

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto br0
#iface br0 inet static
#	address 192.168.0.125
#	network 192.168.0.0
#	netmask 255.255.255.0
#	broadcast 192.168.0.255
#	gateway 192.168.0.1
#	bridged_ports eth0
#	bridge_fd 9
#	bridge_hello 2
#	bridge_maxage 12
#	bridge_stp off

auto br0
iface br0 inet dhcp
	bridge_ports eth0
	bridge_fd 9
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off
```

(I couldn't get static br0 to work so I just used dhcp)

I open up Virtual Machine Manager from System Tools. I have localhost(System) and localhost(User).  I connect localhost(System) to the QEMU hypervisor. It connects.  Now I make a machine (Windows XP)  I set my architecture to x86_64 and only KVM for hypervisor is available. I set the IMG to be in my home folder (the default) When I start the machine it loads the windows installer up.  The installer sees the virtual disk and installs the setup files to it.  But when it restarts to begin installing XP, it doesn't start back up.  When I manually start it I get this message:

```
Plex86/Bochs VGABios current-cvs 25 Sep 2008
This VGA/VBE Bios is released under the GNU LGPL

Please visit:
  http://bochs.sourceforge.net
  http://nongnu.org/vgabios

currus-compatible VGA is detected

QEMU BIOS - build: 09/25/08
$Revision: 1.182 $ $Date: 2007/08/01 17:09:51 $
Options: apmbios pcibios eltorito rombios32

ata0master: QEMU HARDDISK ATA-7 HARD-DISK (4000 MBytes)
ata1master: QEMU DVD-ROM ATAPI-4 CD-Rom/DVD-Rom

Booting from Hard Disk...

A disk read error occured
Press Ctrl+Alt+Del to restart
```

And that is all that happens.  Any information would be greatly appreciated.  I could find no help on this.  The only thing that I can think of (And I am pretty inexperienced)  is maybe a permission is wrong somewhere or the hypervisor isn't connected right.  

Also another note is that when I try to build a virtual server on localhost(User) no option for network is given.  It only says user.  (It also does the same thing when installing XP)


Again thanks for anyone that can help me or point me in the right direction

---

### Post by bodhi.zazen on 2008-11-21
Well, this is why I use teh command line to launch KVM. I do not find virsh or virt-manager are quiet there yet ...

kvm -hda ~/windows.qcow2 -cdrom /dev/cdrom -m 512 etc ...

I have not tried windows with KVM (although I should ....)

---

### Post by dvdcupgo339 on 2008-11-22
The home of [[color=#800080]Professional DVD Retail[/color]](http://www.dvdcup.com/), [[color=#800080]DVD Wholesale[/color]](http://www.dvdcup.com/catalog_8.html) and [[color=#0000ff]DVD Dropshipping[/color]](http://www.dvdcup.com/catalog_18.html). At last, a genuine DVD DROPSHIP company that actually makes you money. World-wide, reliable delivery, and a personal service. We offer you top quality DVDs and related products at great prices with good old-fashioned customer service. Our state of the art system will provide you with all of the information you need to have in order regain full control of YOUR customer&#8217;s orders. We all know that happy customers are more likely to come back to us.You now have the perfect platform to make an additional income by becoming a member of DVDCUP.com. People joining  DVDCUP.com   to earn extra income include: stay-at-home mums/dads, students, retired,     professionals, business owners, etc. etc. Basically, anyone wanting to earn more money will benefit from joining us.Our website is famous amongst eBay sellers, and we are also a closely guarded trade secret. We are the DVD Dropshipper to many world-wide eBay Powersellers.        Dropship on eBay If you have a store or sell on eBay, our [[color=#0000ff]DVD Dropship[/color]](http://www.dvdcup.com/catalog_18.html) Company can increase your profit margins. Want to make more money, and increase your revenue? You can quickly do this, when you use   our services to [[color=#0000ff]Dropship DVDs[/color]](http://www.dvdcup.com/catalog_18.html) and Software, direct to your customers.We have members joining our service every day, and established members who are earning a very comfortable income from using our services. We have members who sell on their own websites; own shops; car     boot sales; eBay & other auction sites such as Amazon, and many others. The scope, and potential for making a serious income with us is totally unlimited.If you have ever wondered where successful sellers on eBay buy their stock?.....

---

### Post by zietbukuel on 2008-11-27
You're lucky. I only see a black window... I've done the same thing as you have. I have no clue. My hardware does support virtualization, please help. If you need anything just tell me and i'll post it, thank you very much.

---

### Post by Faith_IT on 2009-03-20
Hello to all,

I tried a lot to use KVM under x86_64 and MS Windows and this are my findings (valid for PCs that support virtualization technologies only):

In various forum and HOWTOs is reported that currently KVM and Windows have incompatibilities. The first issue is due to ACPI. If you have ACPI enabled the emulated machine is really slow and clumsy. You may disable it by hitting F5 when the Windows installer ask "press F6 to install third party SCSI drivers" just at the beginning. An "hidden" menu pops up where you may choose "Standard PC" and thus disable ACPI.
Even with this my emulated WinXP machine is not lightning fast but it's usable (I also removed the background image to save on resources).

Even with this I never ever managed virtsh and virt-install to run the machine correctly. I currently use kvm directly on my machine, even if I have no XWindows on it and use shell commands only. 
I put the following in a startXP file to call it when I want to start the virtual machine.

```

sudo kvm \
        -no-acpi \
        -m 1024 \
        -cdrom /home/NETKVM-20081229.iso \
        -boot c /root/vm1/vdisk.img \
        -localtime \
        -vnc :0 \
        -net nic,model=virtio,macaddr=00:16:36:51:64:40,v \
        -net tap \
        -usb \
        -usbdevice tablet \
        -daemonize

```

The NETKVM-yyyymmdd.iso file is the ISO image of the virtual network adapter drivers you may find following this link and instructions:

[http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers](http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers)

To install your virtual machine you may refer to the following website:

[http://www.cmready.com/polyoperable/?p=6](http://www.cmready.com/polyoperable/?p=6)

using only kvm related commands (no qemu).

I hope this helps!

---

