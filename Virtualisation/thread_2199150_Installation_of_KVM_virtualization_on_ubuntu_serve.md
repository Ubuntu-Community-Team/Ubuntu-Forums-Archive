---
title: "Installation of KVM virtualization on ubuntu server 12.04"
date: 2014-01-12
forum: Virtualisation
---

### Post by gerry429 on 2014-01-12
[URL="http://www.dedoimedo.com/computers/kvm-intro.html"]
http://www.dedoimedo.com/computers/kvm-intro.html[/URL]
 [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)  	

Condolidated the guid from the above two links. 
I have installed on Ubuntu 12.04 server 64bit version. Converted all my production servers from VMWare Server 2.0 to KVM.
I have tried various virtualization products and finally settled on KVM. 

check the CPU for virtualization support - If the following command displays anything other than 0 then it is supported

    	egrep -c '(vmx|svm)' /proc/cpuinfo

   	Next step is to check the virtualization is enabled in the bios. To check issue the following command.   	$ /usr/bin/kvm-ok 
   	or   	$ /usr/sbin/kvm-ok
   	If the command is not available, then install cpu-checker   	$ apt-get install cpu-checker
   	The command should display something like below.   	$ INFO: Your CPU support KVM extensions
$ INFO: /dev/kvm exists
$ KVM acceleration can be used
   	Now install kvm   	$ apt-get install qemu-kvm libvirt-bin bridge-utils virt-manager virtinst
$ apt-get install ubuntu-vm-builder
   	add the current user to the group 'libvirtd'   	$ adduser 'root' libvirtd
   	Next step is to add bridged network interface. By default KVM doesn't come with bridged network interface. Only NAT.   	$ apt-get install qemu libcap2-bin
   	Ubuntu 10.4 (Lucid) and later - Grant specific users the CAP_NET_ADMIN capability. 

This capability should be assigned cautiously, as it will allow those users to disrupt all networking on the  system. 

Give qemu the inheritable CAP_NET_ADMIN capability   	for 64bit systems   	$ sudo setcap cap_net_admin=ei /usr/bin/qemu-system-x86_64
   	for 32bit   	$ sudo setcap cap_net_admin=ei /usr/bin/qemu-system-i386
   	Allow specific users to gain the inheritable CAT_NET_ADMIN capability by editing /etc/security/capability.conf

add the following line.   	cap_net_admin   root    
   	Creating a network bridge on the host   	$ invoke-rc.d networking stop
   	If you are working from a remote host, you might get disconnected, and if there was mistake, you won't get connected. 

If you are working from a remote host, make the following changes, issue the restart command, you will get reconnected 

after a brief period of disconnection.   	auto lo
iface lo inet loopback
   	auto eth0
iface eth0 inet manual
   	auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

   	If you are on DHCP then,   	auto lo
iface lo inet loopback
   	auto eth0
iface eth0 inet manual
   	auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
   	/etc/init.d/networking restart
   	So, from now on when you create a new VM you can choose 'br0' interface, instead of the default one. 

That is all for the host side installation.

To manage a KVM host you need Virtual Machine Manager(VMM)

which we have already installed in the host system. 

Now you can install VMM in any Ubuntu client to manage the KVM Hosts.   	$ apt-get install virt-manager.
   	you are good to go.

You can directly mount .vmdk files in KVM. Don't need any convertion.

---

### Post by TheFu on 2014-01-12
In 12.04, many of the steps above aren't needed in my experience. Perhaps I can outline a few shortcuts?

Just the grep should be enough to validate VT-x extensions. If it is found, then the BIOS is set already. Only if it isn't found are any other steps needed. Am I wrong on this?  KVM does require VT-x extensions (or whatever AMD calls there stuff).

**VM Host**
Installing kvm, bridge-utils and the ssh-server should be enough on the VM host. Whenever I install the ssh-server, also install fail2ban to automatically block any failed ssh attempts. Then just add your userid to the libvirtd group. Do not bother with the root user for anything or any network stuff after modifying the interfaces file for the bridge. Nothing related to the NET_CAP.... is needed.  

Newer versions of libvirt will create a bridge, but those seem to be less stable for many systems. Manually creating the bridge is the best answer, as you outline. The key is to always use the bridge (manually overriding it) for each VM setup inside the network settings.  The standard linux bridges are pretty good and efficient. My reading about 10G networks implies that OpenvSwitch is more efficient and capable for those higher bandwidth networks.

**VM Management System**
On the client side, install virt-manager and the ssh-client, then use ssh-copy-id to push your userid ssh-keys to the server. If the management system is the same as the VM host system, no need for ssh anything. Use the normal ssh-keygen to make keys, if needed.

No need for vm-builder or virt-inst for most people. Just use the virt-manager GUI to build any VMs desired.  Those other tools are good for automation, but most people won't be using that.

[This article explains]("http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization") how to more efficiently access desktop OS installs under KVM and provides some tuning information to get better performance. For SSD HDDs, it is fine NOT to pre-allocate the storage since SSDs are so very fast or if you don't like the customers too much. For Linux clientOS installs, use virtio for disk and network access.  There are other tips in that article too around caching and VM settings based on years of use and reading different "best practice" guides.

For faster remote GUIs into KVM clientOS installs on the same LAN, the spice protocol can be a great GUI performance enhancer. I found it non-intuitive to get working and had to drop back to the cirrus video version with VNC a few times. In the end, the spice keyboard mapping lost a few important keys in my setup, so going back to FreeNX and an NX client is what I did. I also prefer that NX uses ssh-based connections, so remote management of VMs can be performed from anywhere in the world with reasonable safety. I wouldn't contemplate that without fail2ban or denyhosts protecting the connections.

Anyone know how to get those articles updated? The [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) is definitely outdated for 12.04. Things are much easier now.

Anyway, good post. Hopefully we can get more folks to use KVM instead of other technologies.  KVM is really great for servers and definitely great for server-on-server VMs.

---

### Post by Doug S on 2014-01-13
> **TheFu said:**
> Anyone know how to get those articles updated? The [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) is definitely outdated for 12.04. Things are much easier now.If you have a launchpad ID, you should be able to edit that page yourself, and it would be great if you would. I don't think you need to be a member of some team, but I might be wrong. Any suggestions for corrections or improvements of the related area of the [Ubuntu Serverguide]("https://help.ubuntu.com/13.10/serverguide/virtualization.html") would be also be appreciated (either via launchpad bug report or via me).
> **TheFu said:**
> For Linux clientOS installs, use virtio for disk and network access.My host Ubuntu server 12.04 sometimes shows ridiculously high load averages. From what I have found on the subject (right or wrong, I do not know), using virtio for disk should fix the issue. I not figured out how to use virsh edit to change the config xml file to change it. (Note: I did not read the article you linked to yet, I will).
> **TheFu said:**
> ...and had to drop back to the cirrus video version with VNC a few times.The cirrus video driver [does not work properly for me]("http://ubuntuforums.org/showthread.php?t=2172337"). I know there are older bug reports about issues with the vmvga driver, and I think that is what led to the cirrus driver by default. However, I think those issues have been fixed. I use virsh edit and change the video driver to vmvga.
> **TheFu said:**
> No need for vm-builder or virt-inst for most people. Just use the  virt-manager GUI to build any VMs desired.  Those other tools are good  for automation, but most people won't be using that. ... KVM is really great for servers and definitely great for server-on-server VMs.My VMs run on my Ubuntu 12.04 server. Since it has no GUI, I can not use virt-manager.

Yes, good post.

---

### Post by TheFu on 2014-01-13
> **Doug S said:**
> If you have a launchpad ID, you should be able to edit that page yourself, and it would be great if you would. I don't think you need to be a member of some team, but I might be wrong. Any suggestions for corrections or improvements of the related area of the [Ubuntu Serverguide]("https://help.ubuntu.com/13.10/serverguide/virtualization.html") would be also be appreciated (either via launchpad bug report or via me).

I have no interest in having a launchpad account. Shouldn't "SSO" handle that?  I already have a few hundred accounts to manage.

> **Doug S said:**
> My VMs run on my Ubuntu 12.04 server. Since it has no GUI, I can not use virt-manager.

Just because the hostOS doesn't have a GUI, doesn't mean that any other Linux machine on the network ... or the internet can't use virt-manager.  My KVM servers are pure servers too - no GUI.  Click that provided link for a diagram that explains more clearly how it works.
Also, virsh can be used from remote systems too.

You can use virsh if you like.  Just export the machine XML file (dumpxml), edit it, then reimport the XML (define).  **man virsh** explains.  Looks like they've made an "edit" command to do these commands for us. However, it is much easier to use virt-manager ... or any other libvirt-based GUI, IMHO.

---

### Post by bertan2 on 2014-01-15
> **TheFu said:**
> Am I wrong on this?

I have had problems on this point with an Acer Aspire laptop. The grep of /proc/cpuinfo indicates that the processor supports virtualization. However, I keep getting a message to say "KVM disabled in BIOS" when I try to actually use this feature. And -- guess what -- the Acer Aspire BIOS has been locked down so that you can't enable it! Needless to say, I am not best pleased.

---

### Post by TheFu on 2014-01-16
> **bertan2 said:**
> I have had problems on this point with an Acer Aspire laptop. The grep of /proc/cpuinfo indicates that the processor supports virtualization. However, I keep getting a message to say "KVM disabled in BIOS" when I try to actually use this feature. And -- guess what -- the Acer Aspire BIOS has been locked down so that you can't enable it! Needless to say, I am not best pleased.

I knew that a few BIOSes didn't allow toggling the VT-x, but I was not aware that cpuinfo would not reflect the actual, current, capabilities. Seems like a bug to me.

---

### Post by Doug S on 2014-01-23
I continue to have grief with my Ubuntu 14.04 Desktop VM. While everything was broken again a few days ago, now at least Unity is working again (I did nothing, other than the daily 14.04 updates, via a secure shell session). However, GNOME is not. At least part of the issue is, yet again, the video driver, if I switch back to the ciruss driver, then GNOME works, but the video display is terrible, with extremely limited resolution options. The vmvga video driver works fine with Unity, but GNOME is virtually unusable. GNOME was working just fine with the vmvga driver, before updates a few days ago.

> **TheFu said:**
> Just because the host OS doesn't have a GUI, doesn't mean that any other Linux machine on the network ... or the internet can't use virt-manager.  My KVM servers are pure servers too - no GUI.  Click that provided link for a diagram that explains more clearly how it works.I do not have any other GUI based Linux computer on my lan, just several servers. I have been doing everything with command line stuff. I wonder if I can run virt-manager on the VM desktop itself?

> **TheFu said:**
> You can use virsh if you like.  Just export the machine XML file (dumpxml), edit it, then reimport the XML (define).  **man virsh** explains.  Looks like they've made an "edit" command to do these commands for us. However, it is much easier to use virt-manager ... or any other libvirt-based GUI, IMHO.Yes, I have been using "virsh edit". However sometimes, even often, it is not clear to me how to edit the file to achieve what I want. I have gone so far as to install a new VM from scratch, then compare the two .xml files then use "virsh edit" to make changes to the original VM's .xml file.

---

### Post by TheFu on 2014-01-23
14.04 - alpha?  No thanks.  Won't touch that until June-ish. Let others debug stuff. I did my early adoption time from 1993-1999 when there wasn't any other choice.

Yes, you can run virt-manager inside a GUI, inside a VM. Is my diagram not clear?  I do it that way over an NX connection. There are NX clients for Windows, Linux and OSX. There is a beta for Android, but I couldn't get it working with my FreeNX servers.

I used only the CLI methods of VM management with Xen, but after switching to KVM and using virt-manager, I've never looked back. It has been 2 yrs, at least now.

---

