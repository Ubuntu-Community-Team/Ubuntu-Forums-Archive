---
title: "Hardy KVM Failed to add tap interface"
date: 2008-05-06
forum: Virtualisation
---

### Post by srodden on 2008-05-06
Hi folks,

I have a pretty vanilla Hardy install and I started playing around with KVM/QEMU tonight. I've set up XP and Vista VMs and they work a treat. While sorting out networking, I've run into a problem. Following the instructions on the 'official' page allows me to set up a bridged interface br0 which virt-manager recognises (the details on the VM show br0 as the interface) however when I start the VM I get an error as pasted below. My user account is a member of the kvm and libvirtd groups. 

This looks like the CAP_NET_ADMIN issue from kernel 2.6.18+ as documented on this link: [http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/FrequentlyAskedQuestions#head-2511814cb92c14dbe1480089c04f83c281117a86](http://calamari.reverse-dns.net:980/cgi-bin/moin.cgi/FrequentlyAskedQuestions#head-2511814cb92c14dbe1480089c04f83c281117a86)

I figure this would've been addressed for the Hardy release so I'm guessing I've missed or messed something. Any advice, please? I do not wish to have to run the VMs with root privs.

Thanks,
Sean 

Error starting domain: virDomainCreate() failed Failed to add tap interface 'vnet%d' to bridge 'br0' : Permission denied

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 480, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 379, in startup
    self.vm.create()
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 240, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: virDomainCreate() failed Failed to add tap interface 'vnet%d' to bridge 'br0' : Permission denied

---

### Post by srodden on 2008-05-08
I can confirm that if I run virt-manager with gksudo that it's able to fire up the TAP and get an address just fine.

Any ideas? Surely I'm not unique :)

---

### Post by srodden on 2008-05-13
Gee, I guess I am unique after all :(

---

### Post by n8bounds on 2008-05-15
I'm getting the same error:

This is from my vm's xml file:
    
    <interface type='bridge'>
	    <mac address='00:16:3e:63:cc:49'/>
	    <source bridge='br0'/>
    </interface>

This is the error I get:

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 480, in run_domain
    vm.startup()
  File "/usr/share/virt-manager/virtManager/domain.py", line 379, in startup
    self.vm.create()
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 240, in create
    if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: virDomainCreate() failed Failed to add tap interface 'vnet%d' to bridge 'br0' : Permission denied

---

### Post by n8bounds on 2008-05-15
Running as root avoids the error on my end as well....grrrr

---

### Post by srodden on 2008-05-15
> **n8bounds said:**
> Running as root avoids the error on my end as well....grrrrYes, I'm thinking it's to do with the method we're using to get the networking happening. Since 2.6.18 they've changed the authority needed to run certain apps.

The real mystery is how are other folks running their VMs under QEMU/KVM such that they are not running into this problem? Is there an easier way to get the VMs on the LAN? Do other folks simply not use networking?

Mac guy at work runs Parallels for his VMs which provides a graphical tool for managing the VLANs etc. /dreams

---

### Post by thelusiv on 2008-05-21
I'm having the same problem. Even though I'm in the kvm and libvirtd groups I still get "permission denied" when trying to start a VM with bridged networking. In fact when creating a new VM I am not even given the option to set up bridged networking, unless I am running virt-manager as root.

Running as root I am unable to start up the VMs I set up as my regular user. What's the best way to copy the configuration over? I tried copying the xml files to /etc/libvirt/qemu/ with no luck.

---

### Post by thefool808 on 2008-05-22
So, you're saying your /etc/network/interfaces looks something like this ->

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

iface eth0 inet static
        address 172.16.5.0
        netmask 255.255.255.0

---

### Post by thelusiv on 2008-05-22
> **thefool808 said:**
> So, you're saying your /etc/network/interfaces looks something like this ->

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

iface eth0 inet static
        address 172.16.5.0
        netmask 255.255.255.0

I started off with all the bridge_* options but slimmed it down to just the "bridge_ports eth0" and it works well as root now. I was able to load my old VM as root by recreating the VM and then choosing the same disk image I had been using before.

---

### Post by srodden on 2008-05-23
The problem of course, being that we'd rather not have to run KVM as root just to get our VMs on network!

Anyone know where we might get more responsive support on KVM networking?

---

### Post by dendrobates on 2008-05-23
your user needs to be in the libvirtd and kvm groups for this to work.

The #ubuntu-virt channel on FreeNode is a good place to get help.  The developers hang out there.

Rick

---

### Post by srodden on 2008-05-23
My user is in those two groups. Thanks for the tip on the channel. Will ask there.

---

### Post by deadguy on 2008-05-30
I'm getting the same error, but running as root does not help for me.  Also, it's happening on a per-vm basis.  I have one VM which starts up just fine as any user, and another which won't start up at all.

---

### Post by cfmunster on 2008-08-02
I have the same problem and did some searching. This issue has been logged as a bug in Hardy:

[https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/247677](https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/247677)

---

### Post by IntuitiveNipple on 2008-08-02
If you're using tun/tap the user needs to be a member of the **tun** group *and* the tun device needs to give the tun group permissions too.

As it happens I've just documented these steps as part of an article on how to configure VDE networking for KVM.

Try the steps in the sections "[Add User(s) to Groups](http://tjworld.net/wiki/Linux/Ubuntu/VirtualMachinesWithVDENetworking#AddUserstoGroups)" and "[Give New Devices tun Group Ownership](http://tjworld.net/wiki/Linux/Ubuntu/VirtualMachinesWithVDENetworking#GiveNewDevicestunGroupOwnership)" in my Wiki article.

Because the udev rule has changed you can either go through a full reboot or manually change the permissions with:
```

sudo chown :tun /dev/net/tun
ls -l /dev/net/tun
crw-rw---- 1 root tun 10, 200 2008-07-02 10:49 /dev/net/tun

```
and then do a log-out/log-in to refresh the user's groups membership.

This works on Gutsy and Hardy at least, that I know of.

---

