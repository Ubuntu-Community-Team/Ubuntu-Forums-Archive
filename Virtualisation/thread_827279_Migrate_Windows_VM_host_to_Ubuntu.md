---
title: "Migrate Windows VM host to Ubuntu"
date: 2008-06-12
forum: Virtualisation
---

### Post by robgolding63 on 2008-06-12
Hi,
I currently have a Windows Server, which is a VMware host to 3 VMs that run my network. The Windows host is a Domain Controller and File Server. The Virtual machines are an Exchange server, Windows web server and Ubuntu Cacti monitoring server. I plan to backup the file server, and migrate the DC onto a Virtual machine, and reinstall the host O/S with Ubuntu Server. I understand that Ubuntu will make a better host – and I will be able to run the Cacti services on the host, thus keeping the number of VMs at 3. This will mean that hopefully less RAM is used by the host, so more is free for the Virtual Machines.

The server has three 80GB IDE drives, and two 500GB SATA drives. I plan to use mdadm to configure software RAID with these drives, as follows:

 - 80GB RAID1 array from two of the IDE drives
 - 500GB RAID1 array from the two SATA drives
 - Single 80GB drive for the Ubuntu Server O/S

I plan to store the Virtual Machines on the 80GB RAID array, and the file server data on the 500GB RAID array. My post relates to whether this is, in your opinion, the best configuration for my server. I wish to separate the host, VMs and File Server data – to ensure maximum performance of the servers.

The host has 2.5GB of RAM, which is almost all utilized when running the Windows host. I know linux manages memory very differently to Windows, and therefore I expect to see near 100% memory utilization – but I hope I can get the swap usage down to a minimum. I may upgrade the RAM to 3GB if necessary.

Mostly, I want to know about using a .vmdk file as a file server drive. I cannot imagine this is a particularly desirable configuration, but I need to use Windows as a file server – to take advantage of the domain and NTFS ACLs. I will mainly be storing documents, music and large AVI files on the server, as it is a home server. Basically I am looking for any input, opinions, or experience anyone has on this matter.

Thanks in advance for any help,

Rob

---

