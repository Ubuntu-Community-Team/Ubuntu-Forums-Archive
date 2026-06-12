---
title: "dnsmasq does not serve up remote tftp ip"
date: 2010-10-25
forum: Server Platforms
---

### Post by vikjon0 on 2010-10-25
Testing on both karmic & lucid.

I have it working fine when tftp and dhcp are installed on the same server but when trying to forward to a remote tftp it does not work. Dnsmasq insist on giving its local ip.

I have added to config:
dhcp-boot=pxelinux.0,pxetest2,192.168.0.130

and I tried with and without the original 
dhcp-boot=/var/lib/tftpboot/pxelinux.0


Not much on this topic on the google nor on the dnsmasq homepage.
Anyone have it working?

---

### Post by vikjon0 on 2010-10-26
OK, I got it to work. It was not enough to change the dhcp-boot option. Some cleaning up was neededd to convince dndmasq it is not in any way the tftp server.

EDIT: Looks like it has to do with the multicast kill. If I uncomment that line it stops working.

This is working:
```
####################################################################
# Copied from https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP
# Modified by vikjon0 2010-10-22 for PXE install server
# This version for remote tftp
#####################################################################
# Sample configuration for dnsmasq to function as a proxyDHCP server,
# enabling PXE clients to boot when an external, unmodifiable DHCP
# server is present.
# The main dnsmasq configuration is in /etc/dnsmasq.conf;
# the contents of this script are added to the main configuration.
# You may modify the file to suit your needs.

# Don't function as a DNS server:
port=0

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Dnsmasq can also function as a TFTP server. You may uninstall
# tftpd-hpa if you like, and uncomment the next line:
#enable-tftp

# Set the root directory for files available via FTP.
# tftp-root=/var/lib/tftpboot



# An example of dhcp-boot with an external TFTP server: the name and IP
# address of the server are given after the filename.
# Can fail with old PXE ROMS. Overridden by --pxe-service.
# Enable for remore tftp server
#dhcp-boot=/var/lib/ftpdboot/pxelinux.0,boothost,192.168.0.3
dhcp-boot=pxelinux.0,boothost,192.168.0.130

# The boot filenam When tftp server is on the same server
#dhcp-boot=/var/lib/tftpboot/pxelinux.0


# rootpath option, for NFS
#dhcp-option=17,/var/www/PXE

# kill multicast
#dhcp-option=vendor:PXEClient,6,2b

# Disable re-use of the DHCP servername and filename fields as extra
# option space. That's to avoid confusing some old or broken DHCP clients.
dhcp-no-override

# PXE menu
# Chnage delay to 0 for quick boot of next menu
#pxe-prompt="Press F8 for boot menu", 3
pxe-prompt="Press F8 for boot menu", 0

# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
#pxe-service=X86PC, "Boot from network", pxelinux

# A boot service type of 0 is special, and will abort the
# net boot procedure and continue booting from local media.
#pxe-service=X86PC, "Boot from local hard disk", 0

# If an integer boot service type, rather than a basename is given, then the
# PXE client will search for a suitable boot service for that type on the
# network. This search may be done by multicast or broadcast, or direct to a
# server if its IP address is provided.
#pxe-service=x86PC, "Install windows from RIS server", 1

# This range(s) is for the public interface, where dnsmasq functions
# as a proxy DHCP server providing boot information but no IP leases.
# Any ip in the subnet will do, so you may just put your server NIC ip here.
dhcp-range=192.168.0.0,proxy

# This range(s) is for the private network on 2-NIC servers,
# where dnsmasq functions as a normal DHCP server, providing IP leases.
#dhcp-range=192.168.0.20,192.168.0.250,8h

# For static client IPs, and only for the private subnets,
# you may put entries like this:
#dhcp-host=00:20:e0:3b:13:af,10.160.31.111,client111,infinite
```

---

