---
title: "qemu/kvm bridge not selectable in guest configuration"
date: 2020-07-15
forum: Virtualisation
---

### Post by franknfurter2 on 2020-07-15
Hallo,

in the attachment you can see my host network adapters (lo, enp0s31f6, virbr0,virbr0-nic,anbox0) in the upper left terminal window, the virtual network of qemu in the lower left corner (virt-manager), the nm-connection-editor in the lower middle and the NIC configuration possibilities of the Lubuntu guest system.
As you can see
1. in the guest configuration the virbr0 devices are not selectable
2. the virbr0-nic and anabox0 are not listed in the virt-manager window
3. virbr0-nic and anabox are also not listet in the nm-connection-editor

Who can explain this?

My main goal is to set up my guests in a way that they get the ip from the DHCP my host is connected with. They should be in the same network as my host.
I have tried to create a bridge by myself with nm-connection-editor and it worked, but after rebooting the host there was neither the new crated bridge nor does the host NIC get connected/started. I do not understand this and need help. Network setup is not my daily job and is not well known.

Regards

Frank

---

### Post by TheFu on 2020-07-15
Setup br0 using manual methods or the netplan config file.
All those options above are NAT, not bridges.

NM can't do this to my knowledge.

---

### Post by franknfurter2 on 2020-07-16
Dear TheFu,

thx a lot. To make it clear to me: How do you see that all above is NAT? Where can I see it? The nm-connection-editor declared virbr0 and anbox0 as bridges.

And what do you mean with "manual methods"? What are manual methods to you? Maybe you try to give a wider answer so that one can understand better, what you mean. That would be helpful.

Are you also able to answer my other questions off the original post?

Regards

Frank

---

### Post by franknfurter2 on 2020-07-16
just to share it here: I found myself some good info about virbr0 and virbr0-nic
[https://unix.stackexchange.com/questions/523245/whats-the-function-of-virbr0-and-virbr0-nic](https://unix.stackexchange.com/questions/523245/whats-the-function-of-virbr0-and-virbr0-nic)

It would be nice if someone can point me to the original documentation, where this is described.

---

### Post by TheFu on 2020-07-16
**route -n** or **ip route** for ugly output.  Network-Manager is for typical uses.  Bridge setup is NOT a typical use.

Manual method to me means by _modifying a text config file_ for the system.

On my 16.04 systems, creating a bridge happens in /etc/network/interfaces, but that doesn't help for someone using 18.04 or 20.04.

Since 17.10, netplan is used, not the interfaces file.  So look up netplan and create the bridge that way for systems newer than 17.10.  I'd google for *netplan bridge libvirt* to see what comes up. The netplan main project page has examples, I think.  I've never used it, so I'm not comfortable posting a guess here. 

The original questions were about network-manager and a version of virt-manager that I've never seen or used.  I purge from all my systems after problems with it.

I've always had to type in "br0" for the interface to be used in virt-manager AFTER I manually set it up. 10 yrs ago, using the automatically generated network stuff from libvirt produced terrible network performance, whereas manually setting up a bridge got 100% of the expected performance on a GigE network.  For higher speed networks, use OpenvSwitch.

Does that explain better why my answers were less exact than you may have wanted, but only as much as I could provide?  In the Unix world, GUIs usually have about 20% of the capabilities that the full program provides.  If that 20% is what you need, fantastic!  If it isn't, especially for a server-oriented tool like KVM VMs, then we users need to be flexible and prepared to edit some text files, if necessary. 

As for documentation about **virt-manager** and **libvirt**, the project pages are all that I've seen.
[https://virt-manager.org/](https://virt-manager.org/)
[https://libvirt.org/](https://libvirt.org/)

In a last effort, I googled for a solution and found this: 
   [https://www.cyberciti.biz/faq/how-to-add-network-bridge-with-nmcli-networkmanager-on-linux/](https://www.cyberciti.biz/faq/how-to-add-network-bridge-with-nmcli-networkmanager-on-linux/)
They didn't provide sufficient before-after differences for the networking, so I can't tell whether that creates a true bridge or not.  Seems much harder than just editing the interfaces or netplan file. Seriously. The virsh steps they used aren't how I'd do it.  If virt-manager didn't work, which it always has, I'd use **virsh edit {domain}** then modify the XML.  This bypasses some update issues.

Sorry, I'm not much help.

---

### Post by franknfurter2 on 2020-07-17
Dear TheFu,

thanks for being that kind and for spending your time giving me not a short answer. So now i know what you mean.

I'm dealing with many problems here:
[LIST=1]
[*]Migrating from VirtualBox to QEMU/KVM while not knowing QEMU/KVM very well yet 
[*]Trying to set up a network while not really knowing the difference between NAT and Bridge 
[*]Dealing with old threads in support-forums not focusing on the todays Ubuntu version 18.04 ore even 20.04, that are different (systemctl, Networkmanager i.e.) 
[/LIST]

My hope was, to find someone in this forum that could quickly help in setting up my environment. Now I guess that I will not be able to avoid reading a lot of documentation (while there is less or none about virt-manager)
 This virtualisation forum here is not very busy.

Regards and thanks

Frank

---

### Post by TheFu on 2020-07-17
We've all been there, seeking the shortest answers, without also gaining the understanding.  On Unix, that seldom works out well.

NAT - creates a new private subnet that is different from the upstream subnet.
Bridge - passes traffic, including DHCP and IP unmolested between the upstream and downstream systems.

With a bridge, the hostOS firewall rules do not get applied to any traffic specifically not sent to the host.  Anything sent to any guest virtual machine will be passed through so you'll need firewalls on each.  With a bridge, it is best to treat each VM as though it is a physical machine for most things.

The virt-manager documentation is that sort that doesn't provide any great hints. It basically just says "here's the window for X", which isn't exactly useful documentation.  OTOH, it is just a GUI that passes input data to libvirt, so it is really the libvirt documentation which matters most.  Remember the 20% rule for Unix GUI programs.  For example, if we need to control the order that the VMs are started after the OS boots, then we can't control that using virt-manager.  We really need to make a script to control it, with whatever checks/delays are necessary to the sequencing.  A few people have made complex scripts which do just that.  But in the end, I find it has been just as effective to create a script like this:
```
virsh start dns-01
virsh start dns-02
sleep 10s
virsh start dbms-01
virsh start dbms-02
sleep 20s
virsh start web-01
virsh start web-02
sleep 20s
virsh start web-03
virsh start web-04
```
I bet you can guess what the orderly shutdown script looks like - it is the opposite order and has longer delays since shutting down usually takes longer.  If you run all "01" servers on one physical VM host, and "01" servers on a different physical VM host, then it can be a little easier depending on any load balancing or heartbeat software needed between the multiple VM nodes.

At some point, I really should add checks that the dependent services are actually working before launching the next VM group.

---

### Post by franknfurter2 on 2020-07-19
Dear TheFu,

thank you very much.
Until now I have not found a way, to put the guests into the same network than the host. All I can see is bridges or NAT with their own dhcp. What I want is that the guests get their IP from the DHCP thats running for the network of the host as well.
It's also possible, caused by my missing knowledge, that this is not a good idea or sounds weird to someone, who has a deep knowledge about network and virtualization. So let me know, if its so. 

Regards

Frank

---

### Post by TheFu on 2020-07-19
Perhaps what you think the ideal networking is for each VM and the host?
Here's a table to fill in:
```
Hostname    IP/netmask         Gateway        Notes
hostA       192.168.20.10/24  192.168.20.1   Normal LAN; VM-host
hostB       192.168.20.20/24  192.168.20.1   Normal LAN
hostC       192.168.20.30/24  192.168.20.1   Normal LAN
hostD       192.168.20.40/24  192.168.20.1   Normal LAN
hostE       192.168.10.10/24                 Host-Only Network
```

---

