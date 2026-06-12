---
title: "Vmware server on Server 2008+Ubuntu"
date: 2010-04-23
forum: Virtualisation
---

### Post by LebLinux on 2010-04-23
Hello,

I have a problem with my setup. I have 2 Network Cards on Server 2008 machine which is a Host machine. I have installed Ubuntu server but I want to bridge its network to the physical network card number 2 on my Host Machine (server 2008). I would like to ping the static ip of the assigned network card 2 on Server 2008 which would act as if am pinging the static IP on ubuntu. So how do I accomplish that.

Technical part:

Windows Server 2008 as Host:
 2 NICS.

NIC 1 has the network of 192.168.X.X.
NIC 2 has the network address of 193.188.Y.Y.

Both networks can Ping each other.

I want Ubuntu Server the Guest to has the NIC 2 address.

I tried bridging and Host only and Natting didn't work in the Vmware's network manager.
But I believe I have bad configuration in the vmware network manager. Anyone could help me on this.

I want Ubuntu to get the ip of NIC 2 and act part of the 193.188.Y.Y Network.

I installed the vmware-tools from ubuntu open-vmware-tools and it loaded vmxnet into the modules but running ifconfig -a doesn't display the vmxnet it displays on eth0. I want eth0 to be pointed to NIC 2 on Server 2008 so it can find its way to the LAN.

Here is my lsmod output:

>  lsmod
Module                  Size  Used by
xt_dscp                 2140  0
iptable_nat             5500  0
nf_nat                 17808  1 iptable_nat
nf_conntrack_ipv4      13352  3 iptable_nat,nf_nat
nf_conntrack           67608  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
iptable_mangle          3452  0
ipt_LOG                 5344  4
acpiphp                22480  0
vmsync                  3992  0
vmmemctl                8636  0
vmhgfs                 50772  0
iptable_filter          3100  1
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16544  4 xt_dscp,iptable_nat,ipt_LOG,ip_tables
ppdev                   6688  0
psmouse                56180  0
serio_raw               5280  0
parport_pc             32228  1
lp                      8964  0
intel_agp              27748  1
vmxnet                 17984  0
shpchp                 32336  0
parport                35340  3 ppdev,parport_pc,lp
agpgart                35020  1 intel_agp
i2c_piix4              10124  0
vmci                   29280  0
mptspi                 17764  3
mptscsih               34556  1 mptspi
mptbase                89348  2 mptspi,mptscsih
floppy                 54980  0
scsi_transport_spi     23036  1 mptspi


Ifconfig -a shows only eth0 which is currently on NAT.
I want it to display the virtual networks which I could pinpoint it to the birdged physical network. Any ideas?

Dpkg-query shows:

ii  open-vm-modules-2.6.31-14-generic-pae 2009.07.22-179896-2+2.6.31-14.48  open-vm modules for Linux (kernel 2.6.31-14-
ii  open-vm-source                        2009.07.22-179896-2               Source for VMware guest systems driver
ii  open-vm-tools                         2009.07.22-179896-2               tools and components for VMware guest system

Any ideas why I can't configure eth0 to point it to the physical network address of the Host?





Regards,

Saad

---

### Post by LebLinux on 2010-04-29
Guys Any ideas really I need to get it worked out.

---

