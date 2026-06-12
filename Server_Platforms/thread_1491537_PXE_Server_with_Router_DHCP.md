---
title: "PXE Server with Router DHCP"
date: 2010-05-23
forum: Server Platforms
---

### Post by ncwilde43 on 2010-05-23
I'm trying to setup a PXE server using Ubuntu Server 9.10.  The catch is that I have to use an unmodified router as the DHCP server.  

I tried to combine the following two tutorials but failed to do so
[LIST]
[*][UbuntuLTSP/ProxyDHCP]("https://help.ubuntu.com/community/PXEInstallMultiDistro")
[*][PXEInstallMultiDistro]("https://help.ubuntu.com/community/PXEInstallMultiDistro")
[/LIST]
When booting a client using PXE, I get the following.
```
Press F8 for boot menu (3)
Boot from network
Boot from local hard disk

```
But when I choose to boot from the network, I get the following errors:
```
PXE-T01 not found
PXE-E3B not found
PXE-MOF not found
```

These are my conclusions:
[LIST]
[*]The DHCP service on the router successfully points to the PXE server.
[*]The ltsp.conf is read correctly.
[*]The ltsp.conf file does not point to the correct tftp directory?
[/LIST]

I personally think my problem is in my ltsp.conf file
```
 ...
# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
pxe-service=X86PC, "Boot from network", [COLOR="Red"]/var/lib/tftpboot/pxelinux[/COLOR]
 ...
```
[SIZE="4"]Here are my settings:[/SIZE]

[SIZE="3"]File locations[/SIZE]
[INDENT]/etc/network/interfaces
/etc/dnsmasq.d/ltsp.conf
/opt/ltsp/i386/boot/pxelinux.cfg/default
/opt/ltsp/i386/etc/lts.conf
/opt/ltsp/i386/etc/ltsp/update-kernels.conf
/var/lib/tftpboot/pxelinux.0
/var/lib/tftpboot/pxelinux.cfg/pxe.conf
/var/lib/tftpboot/pxelinux.cfg/default
/var/lib/tftpboot/Ubuntu/Ubuntu.menu[/INDENT]

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

## This is the network bridge declaration

## Start these interfaces on boot
auto lo br0

iface lo inet loopback

iface br0 inet static
  address 192.168.1.100
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
```

/etc/dnsmasq.d/ltsp.conf
```
# Sample configuration for dnsmasq to function as a proxyDHCP server,
# enabling LTSP clients to boot when an external, unmodifiable DHCP
# server is present.
# The main dnsmasq configuration is in /etc/dnsmasq.conf;
# the contents of this script are added to the main configuration.
# You may modify the file to suit your needs.

# Don't function as a DNS server:
port=0

# Log lots of extra information about DHCP transactions.
log-dhcp

# Set the root directory for files available via FTP.
tftp-root=/var/lib/tftpboot

# The boot filename.
dhcp-boot=/var/lib/tftpboot/pxelinux.0

# rootpath option, for NFS
dhcp-option=17,/srv/install

# kill multicast
dhcp-option=vendor:PXEClient,6,2b

# Disable re-use of the DHCP servername and filename fields as extra
# option space. That's to avoid confusing some old or broken DHCP clients.
dhcp-no-override

# PXE menu
pxe-prompt="Press F8 for boot menu", 3

# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
pxe-service=X86PC, "Boot from network", /var/lib/tftpboot/pxelinux

# A boot service type of 0 is special, and will abort the
# net boot procedure and continue booting from local media.
pxe-service=X86PC, "Boot from local hard disk", 0

# This range(s) is for the public interface, where dnsmasq functions
# as a proxy DHCP server providing boot information but no IP leases.
# Any ip in the subnet will do, so you may just put your server NIC ip here.

```

/opt/ltsp/i386/boot/pxelinux.cfg/default
/var/lib/tftpboot/pxelinux.cfg/default
```
DEFAULT vesamenu.c32
IPAPPEND 3
TIMEOUT 600
ONTIMEOUT BootLocal
PROMPT 0
MENU INCLUDE pxelinux.cfg/pxe.conf
NOESCAPE 1
LABEL BootLocal
        localboot 0
        TEXT HELP
        Boot to local hard disk
        ENDTEXT
MENU BEGIN Ubuntu
MENU TITLE Ubuntu
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE Ubuntu/Ubuntu.menu
MENU END
```

/opt/ltsp/i386/etc/ltsp/update-kernels.conf
```
BOOTPROMPT_OPTS='quiet splash'
IPAPPEND=3
PXELINUX_CMDLINE='DEFAULT vesamenu.c32
IPAPPEND 3
TIMEOUT 600
ONTIMEOUT BootLocal
PROMPT 0
MENU INCLUDE pxelinux.cfg/pxe.conf
NOESCAPE 1
LABEL BootLocal
        localboot 0
        TEXT HELP
        Boot to local hard disk
        ENDTEXT
MENU BEGIN Ubuntu
MENU TITLE Ubuntu
        LABEL Previous
        MENU LABEL Previous Menu
        TEXT HELP
        Return to previous menu
        ENDTEXT
        MENU EXIT
        MENU SEPARATOR
        MENU INCLUDE Ubuntu/Ubuntu.menu
MENU END'
```

/var/lib/tftpboot/Ubuntu/Ubuntu.menu
```
LABEL 10
        MENU LABEL Ubuntu 10.04 (32-bit)
        KERNEL Ubuntu/10.04/i386/vmlinuz
        APPEND boot=casper netboot=nfs nfsroot=192.168.1.100:/srv/install/Ubunt$
        TEXT HELP
        Boot the Ubuntu 10.04 32-bit DVD
ENDTEXT
```

/opt/ltsp/i386/etc/lts.conf
```
[Default] XSERVER            = auto
        SERVER             = 192.168.1.100
        X_MOUSE_PROTOCOL   = "PS/2"
        MODULE_01          = "sb irq=10 io=0x300"
        X_MOUSE_DEVICE     = "/dev/psaux"
        X_MOUSE_RESOLUTION = 400
        X_MOUSE_BUTTONS    = 3
        USE_XFS            = N
        LOCAL_APPS         = N
        RUNLEVEL           = 5
```

/var/lib/tftpboot/pxelinux.cfg/pxe.conf
```
MENU TITLE  PXE Server
MENU BACKGROUND pxelinux.cfg/logo.png
NOESCAPE 1
ALLOWOPTIONS 1
PROMPT 0
menu width 80
menu rows 14
MENU TABMSGROW 24
MENU MARGIN 10
menu color border               30;44      #ffffffff #00000000 std
```

Note: I did make sure that the ftpf daemon is running
```
sudo /etc/init.d/tftpd-hpa start
```
Any help is greatly appreciated!

---

### Post by sylvester_0 on 2010-05-23
Holy information overload. I've never used ProxyDHCP myself. I'd try running wireshark then running a dhclient eth0 on another machine to see if the correct DHCP options (bootserver, bootfile etc)

---

### Post by ncwilde43 on 2010-05-24
Okay, so I've solved the initial problem, and I'm onto the next.

The problem was with the TFTP path.  It's a relative path rather then an absolute.
```
 ...
# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
pxe-service=X86PC, "Boot from network", [COLOR="Red"]pxelinux[/COLOR]
 ...
```

The problem I have now is that the screen sticks on "Loading" when I choose to boot from Ubuntu from the menu.  Also, the background image, Logo.png, does not show up, but the pxe.conf is loading, because the menu title shows up, "PXE Server".

---

### Post by ncwilde43 on 2010-05-25
I ended up solving my problem by deleting my entire /var/lib/tftpboot directory and then following [this]("http://ubuntuforums.org/showthread.php?t=1413126") post from the **fetching the boot files** section onward.  I was able to get to the install menu, but I haven't yet tested the actual install.

---

### Post by vikjon0 on 2010-10-17
Hello!

I am looking to do exactly that.
PXEInstallMultiDistro, but with proxy dhcp. Seems like the perfect solution but the all wiki guides goes for the "old?" way that doesnt allow active dhcp on the router.

Do you mind sharing the installation procedures? It will take me ages to figure it out by myself. 

If you still need more info here is a script that does it all automatically, but it boots a LiveCD:
[https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot)

Very elegant.

//J

---

### Post by bakegoodz on 2010-10-17
This is how PXE works, it asks the DHCP server were the tftp server is, so it know where to download the boot kernel. So either you have to somehow to tweak your DHCP server/device to do that, or you have to use another DHCP server for your PXE clients. In Linux you add the correct line in dhcpd.conf ( ex. next-server 192.168.0.2; ) You easily can make the PXE server the router/DHCP server if you have two network cards.

---

### Post by vikjon0 on 2010-10-18
Yes, thats the old way. It IS possible to do it without modifying the existing dchp. 
It is called proxy dhcp
[https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP](https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP)

> 
A proxy DHCP server is defined by the PXE specification as a server which sends auxiliary boot information to clients, like the boot filename, tftp server or rootpath, but leaves the task of IP leasing to the normal DHCP server. This functionality perfectly matches certain LTSP configurations where an external, unmodifiable DHCP server is present (e.g. a router). 

Here is an implementation that I have tested on my own network.
[https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot)

---

### Post by ncwilde43 on 2010-10-18
> **vikjon0 said:**
> ...
Do you mind sharing the installation procedures? It will take me ages to figure it out by myself. 
...
//Jvikjon0,

Due to the many trials and errors that I experienced during the PXE boot, I cannot tell you exactly how I solved it (for I do not know), but I will do my best to help.

I believe the solution to the DHCP problem lies in dnsmasq.  I remember following the guide located [here]("https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP") to help setup dnsmasq because I didn't know which conf file to use/modify.  The next application that I use is tftpboot.

I'll post my current server setting files for you to references.

First off, I'm using Ubuntu Server 9.10.  I installed dnsmasq using the ProxyDHCP guide, and I created the current conf file.

[FONT="Courier New"]/etc/dnsmasq.d/ltsp.conf[/FONT]
```
# Sample configuration for dnsmasq to function as a proxyDHCP server,
# enabling LTSP clients to boot when an external, unmodifiable DHCP
# server is present.
# The main dnsmasq configuration is in /etc/dnsmasq.conf;
# the contents of this script are added to the main configuration.
# You may modify the file to suit your needs.

# Don't function as a DNS server:
port=0

# Log lots of extra information about DHCP transactions.
log-dhcp

[COLOR="Red"]# Set the root directory for files available via FTP.
tftp-root=/var/lib/tftpboot

# The boot filename.
dhcp-boot=/var/lib/tftpboot/pxelinux.0[/COLOR]

# rootpath option, for NFS
dhcp-option=17,/srv/install

# kill multicast
dhcp-option=vendor:PXEClient,6,2b

# Disable re-use of the DHCP servername and filename fields as extra
# option space. That's to avoid confusing some old or broken DHCP clients.
dhcp-no-override

# PXE menu
# pxe-prompt="Press F8 for boot menu", 3

# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
pxe-service=X86PC, "Boot from network", pxelinux

# A boot service type of 0 is special, and will abort the
# net boot procedure and continue booting from local media.
# pxe-service=X86PC, "Boot from local hard disk", 0

# This range(s) is for the public interface, where dnsmasq functions
# as a proxy DHCP server providing boot information but no IP leases.
# Any ip in the subnet will do, so you may just put your server NIC ip here.
[COLOR="Red"]dhcp-range=192.168.1.100,proxy[/COLOR]
```

Main options that you want to pay attention to are listed in red. tftpboot, I believe, is the program used to actually send the image file to the booting client.

The [FONT="Courier New"]dhcp-range[/FONT] option is the same as my server's static IP.  Please see [FONT="Courier New"]/etc/network/interfaces[/FONT] file posted in my [first]("http://ubuntuforums.org/showthread.php?p=9989711#post9349053") post.

Next I installed tftpboot.

I copied the entire [netboot cd structures]("http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/netboot/") to my tftpboot directory.  The only thing I did differently was put the lucid files into the tftpboot/ubuntu-installer/lucid directory and the maverick files into tftpboot/ubuntu-installer/maverick directory.

My tftpboot directory structure looks like this:
```
/var/lib/tftpboot/boot.img.gz
/var/lib/tftpboot/mini.iso
/var/lib/tftpboot/netboot.tar.gz
/var/lib/tftpboot/pxelinux.0
/var/lib/tftpboot/pxelinux.cfg
/var/lib/tftpboot/ubuntu-installer/lucid
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/adtxt.cfg
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/exithelp.cfg
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f10.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f1.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f2.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f3.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f4.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f5.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f6.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f7.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f8.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/f9.txt
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/menu.cfg
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/prompt.cfg
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/rqtxt.cfg
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/splash.png
/var/lib/tftpboot/ubuntu-installer/maverick/i386/boot-screens/stdmenu.cfg 
/var/lib/tftpboot/ubuntu-installer/maverick/i386/index.html
/var/lib/tftpboot/ubuntu-installer/maverick/i386/initrd.gz
/var/lib/tftpboot/ubuntu-installer/maverick/i386/linux
/var/lib/tftpboot/ubuntu-installer/maverick/i386/pxelinux.0
/var/lib/tftpboot/ubuntu-installer/maverick/i386/pxelinux.cfg/default
/var/lib/tftpboot/ubuntu-installer/maverick/i386/syslinux.cfg
/var/lib/tftpboot/ubuntu-installer/maverick/i386/txt.cfg
/var/lib/tftpboot/ubuntu-installer/maverick/i386/vesamenu.c32
/var/lib/tftpboot/xen/initrd.gz
/var/lib/tftpboot/xen/vmlinuz
/var/lib/tftpboot/xen/xm-debian.cfg
```

My default file looks like this:

[FONT="Courier New"]/var/lib/tftpboot/pxelinux.cfg/default[/FONT]
```
default ubuntu-installer/lucid/i386/boot-screens/vesamenu.c32

menu hshift 13
menu width 49
menu margin 8

Menu Title Boot Menu
include ubuntu-installer/lucid/i386/boot-screens/stdmenu.cfg
label lucidunattended
    menu label ^Lucid Unattended
    menu default
    kernel ubuntu-installer/lucid/i386/linux
    append preseed/url=http://url/to/lucid.cfg debian-installer/locale=en_US netcfg/choose_interface=auto vga=normal initrd=ubuntu-installer/lucid/i386/initrd.gz priority=critical --

label lucidmanual
   menu label ^Lucid Manual
   kernel ubuntu-installer/lucid/i386/linux
   append vga=normal initrd=ubuntu-installer/lucid/i386/initrd.gz --quiet

label maverickunattended
    menu label ^Maverick Unattended
    menu default
    kernel ubuntu-installer/maverick/i386/linux
    append preseed/url=http://url/to/maverick.cfg debian-installer/locale=en_US netcfg/choose_interface=auto vga=normal initrd=ubuntu-installer/maverick/i386/initrd.gz priority=critical $

label maverickmanual
   menu label ^Maverick Manual
   kernel ubuntu-installer/maverick/i386/linux
   append vga=normal initrd=ubuntu-installer/maverick/i386/initrd.gz --quiet

label Local_drive
   localboot 0
   menu label ^Local Drive

prompt 0
timeout 0
```

An example of the Lucid preseed file can be found [here]("https://help.ubuntu.com/10.04/installation-guide/example-preseed.txt") and the guide can be found [here]("https://help.ubuntu.com/10.04/installation-guide/i386/appendix-preseed.html").

HTH,

---

### Post by vikjon0 on 2010-10-18
Hello!

Thank you very much.
Since we dont have a complete gudie I decided I have to learn more before I attempt to implement dhcp proxy.

This morning I tried this guide.
[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

One concern is that pxelinux.cfg did not exist after following the guide exactly (?).
EDIT: I see that you have boot.img.gz etc in the root, I suppose that what I need.

As soon as I can get that to work I will continue.
I am running it in a VM ware host only network so dhcp from the router is not a problem while testing.

I actually get the ip but then I get 
PXE-E11 ARP timeout
PXE-E38 TFTP cannot open connection.
EDIT2: It was a stupid mistake in the dhcp config. It is now booting and I have hit the next issue. I will work and this and if I ever get as far as Proxydhcp I will post a how-to.

---

### Post by vikjon0 on 2010-10-25
Ok! I have it working and I made some notes in case someone need it.

The only thing I am struggling with is to have dnsmasq installed on another server than tftp. 
This should do it:
dhcp-boot=pxelinux.0,pxetest2,192.168.0.130

But does not...

---

### Post by vikjon0 on 2010-10-27
ok, all working. This is what I did:
[http://ubuntuforums.org/showthread.php?t=1606910](http://ubuntuforums.org/showthread.php?t=1606910)

---

