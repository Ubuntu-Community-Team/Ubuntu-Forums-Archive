---
title: "kvm + virtual machine manager, cant select bridged network"
date: 2009-05-15
forum: Virtualisation
---

### Post by Pnuts on 2009-05-15
I've been searching google and going in circles for a while now, so perhaps someone can shed some light on this for me.

I have a 9.04 server with openssh-server, kvm, bridge-utils and uml-utilities installed.

I configured my /etc/network/interfaces like so:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# The Bridged network interface for Guest VM's
auto br0
iface br0 inet static
        address 192.168.1.11
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```

on a separate machine, I can connect via virt-manager fine.

on the network selection page the only choice is a virtual network, which is basically sticking the vm behind a nat using the host as a router.

The "Shared physical device" bullet is greyed out and not selectable. From my understand after searching google to death, it should be an available choice listing br0.

If this might be the cause, root is still disabled per the standard ubuntu install. I am a member of the kvm group. I would like to keep root disabled.

Could anyone offer any suggestions I can try to get the bridged network accessible here?

Thanks,
Pnuts

---

### Post by Pnuts on 2009-05-15
well, still no luck, continueing to search for info but I think i've exhausted google.

i enabled root on the host and connected from virt-manager using root to see if maybe it was a permissions thing somewhere, but I had the same results.

I have also tried creating a guest, then editing the configuration xml and changing:

```
<interface type='network'>
<mac address='54:52:00:74:82:fe'/>
<source network='default'/>
</interface>
```
to
```
<interface type='bridge'>
<mac address='54:52:00:74:82:fe'/>
<source network='br0'/>
</interface>
```

After making that change and restarting, the guest image no longer shows under the host in virt-manger. If I reverse the change and restart, it shows once again.

I believe this is because virt-manager is not able to see the br0 bridge. If anyone has any suggestions for which I can try, please let me know.

-Pnuts

---

### Post by yazidarezki on 2009-05-25
When you created your VM, did you create as User or System?
 
It should be system
 
Cheers
Yaz

---

### Post by Pnuts on 2009-05-26
> **yazidarezki said:**
> When you created your VM, did you create as User or System?
 
It should be system
 
Cheers
Yaz

I am not quite sure what you mean and technically I never found a solution to this through the Virt-Manager gui. I was able to create the image correctly using the bridge network via the command line and then see it functioning correctly in Virt-Manager with the bridge network. I was still unable to create a new image with the bridged network.

For now, if I need to create an image with the bridged Network, I simply do it from the command line and then use the Virt-Manager as normal after this.

-Pnuts

---

### Post by Explodinglemur on 2009-06-03
Make sure you are also a member of the libvirtd group.  If not, "sudo adduser you libvirtd" and log out/in.

Next, launch virt-manager, go to File, Add Connection, and add a local QEMU connection.  You should now see two connections listed, "localhost (System)" and "localhost (User)".  Create a new VM in the system context (unsure if that's the right term) and you'll be able to add bridged network devices.

---

### Post by Pnuts on 2009-06-03
> **Explodinglemur said:**
> Make sure you are also a member of the libvirtd group.  If not, "sudo adduser you libvirtd" and log out/in.

Next, launch virt-manager, go to File, Add Connection, and add a local QEMU connection.  You should now see two connections listed, "localhost (System)" and "localhost (User)".  Create a new VM in the system context (unsure if that's the right term) and you'll be able to add bridged network devices.

I am a member of the libvirtd group. It might be because I am connecting from another machine and there is no gui on the server itself. Maybe there is another group or other permissions I need to give myself?

I'm getting around ok creating the guests via the command line as this is far and few between anyways. Once created, I can pretty much use virt-manager on my laptop normally.

-Pnuts

---

### Post by veloce on 2009-06-04
I now run virt-manager as root (added the icon to the toolbar and changed the command to gksu virt-manager).

Now I only get the localhost(System) tree.

---

### Post by kensonman on 2009-08-27
Try to modifiy into this:
> 
<interface type='bridge'>
<mac address='YOUR_MAC_ADDRESS'/>
<source bridge='br0'/>
<model type='virtio'/>
</interface>

---

### Post by nitish_goyal on 2009-09-23
please tell me how to install sugar .82 on 9.04 through qemu install....i hve no idea about it.....

---

### Post by gtdaqua on 2010-05-20
Is this solved?

I am having the exact same problem as the opening post.

Am using Ubuntu 10.04 Lucid x64 with KVM. 

"Shared Physical device" is greyed on my virt-manager GUI Desktop - Ubuntu 9.10. 

Can anyone help pls?

---

### Post by Pnuts on 2010-05-20
I was never able to find a solution. As I mentioned above, my work around was to just ssh into the machine and create the new VM via the command line. Once created virtual machine manager worked fine.

I have since moved to using VMWare ESXi which actually gave me better performance and is a lot easier to use and manage. Its also free after registering on their site.

---

### Post by deepakgarg on 2011-11-01
HI,
I am having the same problem with ubuntu 11.10 server and kvm.
My Network Interfaces GUI in virt-manager says 'libvirt connection does not support interface management'? Does anybody has any hint on that ?

---

### Post by nothingspecial on 2011-11-01
Hi, please create a thread of your own rather than bumping old ones to the top.

Closed.

---

