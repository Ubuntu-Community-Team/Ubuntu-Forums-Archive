---
title: "Using Ubunto As a Vitrutl Machine"
date: 2022-04-26
forum: Virtualisation
---

### Post by Complete on 2022-04-26
I have just installed*VMWARE Workstation 16 Pro to move files.* How do I move files from the hosting computer to the Virtual Machine?* My computer is a Windows 10 Enterprise and the OS of my vitrual machine is Ubuntu 22.04* 64-bit*

---

### Post by QIII on 2022-04-26
Moved to ***Virtualisation*** as a more appropriate sub-forum.

---

### Post by CharlesA on 2022-04-29
It sounds like you need to set up VMWare Guest Tools, but it that doesn't work, you can always installed openssh-server on the box and transfer files over scp.

---

### Post by TheFu on 2022-04-29
There are multiple ways.

Usually, I treat my VMs like they are normal physical systems and would use a network protocol between them.  For a quick and dirty solution, I'd run sftp server on either system, then use an sftp client on the other system to pull the files.  **sudo apt install ssh** on the ubuntu system will install and setup ssh, scp, sftp, clients and servers.  

However, according to the 22.04 release notes, ssh has deprecated RSA-based keys for ssh, so that would mean that the client would need to support an alternative key type. There are a bunch to choose from. I've been using ed25519 for about 4 yrs. A password can also be used, but it is much less convenient and much less secure than using keys.

You can also setup normal Windows CIFS file sharing. 22.04 is too new, so I don't know if there are any gotchas using Windows sharing from the new version of samba Ubuntu comes with. I know that 'browsing' of shares ... that's pointing an clicking was broken by MSFT about 2 yrs ago when they decided to change the announcement protocol on a LAN.  Since then, most people trying to connect from Linux to Windows have used direct CIFS mounts, not browsing.  For someone new, that would probably be a steep learning curve. Of course, it could all be fixed in 22.04 and a complete non-issue. A new samba is available. Just need to install it.  The release notes for 22.04 has more details.

There is probably some built-in VMware-only method to connect the VM guest to the VM host storage. That would certainly require installing the VMware guest additions. Sometimes, especially for very new releases, VMware isn't ready and needs a few months - sometimes a new release of VMware Workstation is required.

Win10 does support ssh, so if it were me, I'd use one of the scp/sftp methods. Most Windows people would be more comfortable using something like the free **WinSCP** application for Windows that will connect to any other scp/sftp server either on the LAN or over the internet. 

All of these options will require a specific network setup for the guest machine that is host-only or bridged.  You'll need to know the IP address for the guest VM, since that's how all network protocols work.

If you need to connect to scp or sftp systems from Ubuntu, almost any file manager (nautilus, caja, thunar, muon, .... ) can be used. Each uses a different URL prefix, but something like sftp:// or scp:// or ssh:// would be expected.  Then it is all drag-n-drop to copy between the different systems.

---

### Post by Complete on 2022-04-30
> **CharlesA said:**
> It sounds like you need to set up VMWare Guest Tools, but it that doesn't work, you can always installed openssh-server on the box and transfer files over scp.

I am very new to all of this.  Can you unpack this a little more and direct me to some material where I can learn?  I think there are at least two technologies  you have mentioned that I am not familiar with.

---

### Post by Complete on 2022-04-30
I think a major issue is that I do not have any network connections on the Ubuntu VM.  This has caused some errors where performing a solution with network connections are assumed.

---

### Post by CharlesA on 2022-04-30
> **Complete said:**
> I am very new to all of this.  Can you unpack this a little more and direct me to some material where I can learn?  I think there are at least two technologies  you have mentioned that I am not familiar with.

It looks like they only support installing a package if you use a package manager that uses rpms, which Ubuntu does not.

You will need to compile the tools via the instructions found here:
[https://kb.vmware.com/s/article/1018414](https://kb.vmware.com/s/article/1018414)

I don't know if you need internet access from the guest or not, however.

---

### Post by TheFu on 2022-04-30
> **Complete said:**
> I think a major issue is that I do not have any network connections on the Ubuntu VM.  This has caused some errors where performing a solution with network connections are assumed.

Not having internet inside a VM when the host networking is fine means there's a misconfiguration of the VM. I haven't used VMware Workstation since the 1990s, but other, similar, tools have a selection box in the VM hardware setup for networking that usually has
[LIST]
[*]Bridged
[*]NAT
[*]Host-only
[*]and something else.
[/LIST]
If you select bridged or nat, and use the virtio device for the NIC adapter type, networking should work. I've never NOT seen that work on any hypervisor.
If you choose 'bridged', all sorts of solutions become possible.  BTW, these changes don't require reinstalling the guest OS.

---

### Post by SeijiSensei on 2022-05-01
You'll need to create a virtual network adapter and have it use DHCP to get an IP address and other information. Usually DHCP queries happen by default, but I've never used VMWARE.

The two most-common options are

NAT - the virtual machine hides behind the host computer. All of its traffic with any outside network is routed through the host computer. That means other devices on your network will not be able to see the virtual machine.

Bridged - the virtual machine is visible on the same network as the host computer. The virtual machine interacts with your local network and the Internet just like the host computer. All the devices on your network can see the virtual machine.

---

