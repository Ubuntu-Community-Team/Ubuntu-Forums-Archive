---
title: "Ubuntu 16.04, KVM with Intel I350 SR-IOV network card"
date: 2016-10-10
forum: Virtualisation
---

### Post by sazzle2 on 2016-10-10
This network card was working fine with Ubuntu 14.04, I followed this guide 

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Host_Configuration_and_Guest_Installation_Guide/sect-Virtualization_Host_Configuration_and_Guest_Installation_Guide-SR_IOV-How_SR_IOV_Libvirt_Works.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Host_Configuration_and_Guest_Installation_Guide/sect-Virtualization_Host_Configuration_and_Guest_Installation_Guide-SR_IOV-How_SR_IOV_Libvirt_Works.html)

and was able to set the vm network source to the hostdev network.

I have just reinstalled the server with Ubuntu 16.04 and followed the same instructions but when I try to boot a vm using the hostdev network it fails to start.

/var/log/libvirt/qemu/websrv.log

2016-10-10T11:14:38.607572Z qemu-system-x86_64: VFIO_MAP_DMA: -14
2016-10-10T11:14:38.607596Z qemu-system-x86_64: vfio_dma_map(0x55f1c4f8bb00, 0xfe000000, 0x4000, 0x7fa687700000) = -14 (Bad address)
qemu: hardware error: vfio: DMA mapping failed, unable to continue

Syslog

Oct 10 12:13:57 vmsrv2 libvirtd[6497]: internal error: network 'passthrough-1' does not have a bridge name.
Oct 10 12:13:58 vmsrv2 libvirtd[6497]: internal error: network 'passthrough-2' does not have a bridge name.
Oct 10 12:14:07 vmsrv2 libvirtd[6497]: internal error: network 'passthrough-1' does not have a bridge name.
Oct 10 12:14:07 vmsrv2 libvirtd[6497]: internal error: network 'passthrough-2' does not have a bridge name.
Oct 10 12:14:37 vmsrv2 kernel: [128738.108661] igb 0000:02:00.0: setting MAC 52:54:00:55:2e:9a on VF 0
Oct 10 12:14:37 vmsrv2 kernel: [128738.108664] igb 0000:02:00.0: Reload the VF driver to make this change effective.
Oct 10 12:14:37 vmsrv2 kernel: [128738.127466] audit: type=1400 audit(1476098077.225:145): apparmor="DENIED" operation="open" profile="/usr/lib/libvirt/virt-aa-helper" name="/etc/nsswitch.conf" pid=10315 comm="virt-aa-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 10 12:14:37 vmsrv2 kernel: [128738.127476] audit: type=1400 audit(1476098077.225:146): apparmor="DENIED" operation="open" profile="/usr/lib/libvirt/virt-aa-helper" name="/etc/host.conf" pid=10315 comm="virt-aa-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 10 12:14:37 vmsrv2 kernel: [128738.244289] audit: type=1400 audit(1476098077.341:147): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-c9d62316-c98f-4b21-a808-dd5c917aa381" pid=10317 comm="apparmor_parser"
Oct 10 12:14:37 vmsrv2 kernel: [128738.244506] audit: type=1400 audit(1476098077.345:148): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libvirt-c9d62316-c98f-4b21-a808-dd5c917aa381//qemu_bridge_helper" pid=10317 comm="apparmor_parser"
Oct 10 12:14:38 vmsrv2 kernel: [128739.133679] vfio-pci 0000:03:10.0: enabling device (0000 -> 0002)
Oct 10 12:14:38 vmsrv2 virtlogd[4072]: End of file while reading data: Input/output error
Oct 10 12:14:38 vmsrv2 libvirtd[6497]: internal error: End of file from monitor
Oct 10 12:14:38 vmsrv2 virtlogd[4072]: Cannot open log file: '/var/log/libvirt/qemu/websrv.log': Device or resource busy
Oct 10 12:14:38 vmsrv2 libvirtd[6497]: Cannot open log file: '/var/log/libvirt/qemu/websrv.log': Device or resource busy
Oct 10 12:14:38 vmsrv2 virtlogd[4072]: End of file while reading data: Input/output error
Oct 10 12:14:39 vmsrv2 kernel: [128739.955590] audit: type=1400 audit(1476098079.053:149): apparmor="STATUS" operation="profile_remove" profile="unconfined" name="libvirt-c9d62316-c98f-4b21-a808-dd5c917aa381" pid=10332 comm="apparmor_parser"
Oct 10 12:14:39 vmsrv2 kernel: [128739.957486] igb 0000:02:00.0: setting MAC 52:54:00:47:e9:8d on VF 0
Oct 10 12:14:39 vmsrv2 kernel: [128739.957488] igb 0000:02:00.0: Reload the VF driver to make this change effective.
Oct 10 12:14:39 vmsrv2 kernel: [128739.957871] igbvf 0000:03:10.0: enabling device (0000 -> 0002)
Oct 10 12:14:39 vmsrv2 kernel: [128739.988463] igb 0000:02:00.0: VF 0 attempted to override administratively set MAC address
Oct 10 12:14:39 vmsrv2 kernel: [128739.988463] Reload the VF driver to resume operations
Oct 10 12:14:39 vmsrv2 kernel: [128739.989071] igbvf 0000:03:10.0: Intel(R) I350 Virtual Function
Oct 10 12:14:39 vmsrv2 kernel: [128739.989073] igbvf 0000:03:10.0: Address: 52:54:00:47:e9:8d
Oct 10 12:14:39 vmsrv2 kernel: [128739.989945] igbvf 0000:03:10.0 enp3s16: renamed from eth0



Any help would be greatly appreciated.


Edit
I have just realised that the content of the link above has changed slightly since I used it. These are the notes I made on how to set it up.

# Check igb module is loaded
lsmod |grep igb
# Should return some values


# Edit grub
vim /etc/default/grub
# Add this to grub command line options
intel_iommu=on pci=assign-busses
# Update grub
update-grub


# Remove the module to change the variable
modprobe -r igb


# Restart the module with the max_vfs set to 7
modprobe igb max_vfs=7


# Make the Virtual Functions persistent
echo "options igb max_vfs=7" >>/etc/modprobe.d/igb.conf
# Update initramfs
update-initramfs -k all -t -u


# Reboot
shutdown -r now


# Checks
sudo lspci -vv | grep -A 10 "Single Root I/O Virtualization"
ip link show


# Verify devices exist with virsh
virsh nodedev-list | grep p1p


# Make available a pool of all VFs for the SR-IOV adapter
sudo vim /tmp/passthrough-1.xml
# Copy in the network definition
<network>
  <name>passthrough-1</name>
  <forward mode='hostdev' managed='yes'>
    <pf dev='enp2s0f0'/>
  </forward>
</network>


virsh net-define /tmp/passthrough-1.xml
virsh net-autostart passthrough-1
virsh net-start passthrough-1


# View status of new network
virsh net-dumpxml passthrough-1


sudo vim /tmp/passthrough-2.xml
# Copy in the network definition
<network>
  <name>passthrough-2</name>
  <forward mode='hostdev' managed='yes'>
    <pf dev='enp2s0f1'/>
  </forward>
</network>


virsh net-define /tmp/passthrough-2.xml
virsh net-autostart passthrough-2
virsh net-start passthrough-2

---

