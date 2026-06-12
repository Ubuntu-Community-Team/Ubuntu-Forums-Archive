---
title: "Ubuntu server hosting virtual machines (dhcp range problem)"
date: 2011-06-23
forum: Server Platforms
---

### Post by YouBuntToo? on 2011-06-23
Hello all,

I am configuring a network that consists of a physical machine and 10 virtual machines. The physical machine is running ubuntu server (11.04) and I am using qemu/kvm/virt-manager to run the virtual machines.

Here is my problem. I need the physical host to assign IP addresses in a very specific range, using DHCP, to the virtual machines. I don't want the range it defaults to. However, when I set this in virt-manager (under connection settings, and then I create a new virtual network with the desired IP range) I get an error that says I can’t start the network I configured because the interface eth0 is already in use.

What gives!? :confused: I tried changing the settings on the default connection using ‘virsh net-edit default’ and I got the same error. The exact error message in virt-manager is “Error starting network: Internal error Network is already in use by interface eth0”. Any advice at all on how to fix this, or any workarounds would be very helpful. :)

Thank you!

---

### Post by YouBuntToo? on 2011-06-23
So, it turns out that if I set up a bridge in the /etc/network/interfaces file then I don't get this error any more. However, I can't connect to the internet now either. Lol. Any thoughts?

The bridge is set up like this btw:
auto lo
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

(except with my IPs)

---

### Post by YouBuntToo? on 2011-06-24
Ok, nevermind. Bridging it only helped that one time. I tried to do that again and it didn't change anything. I still don't know why. 

Does anyone know what the error "**Error starting network: Internal error Network is already in use by interface eth0**" means? and if I can do anything to get around this? Any help would be greatly appreciated.

---

### Post by Jake.Debord on 2011-06-24
What are you using for the VM's? Virtual box VMware or ?

---

### Post by Dangertux on 2011-06-24
You might want to try restart the dnsmasq service when you change your IP range.  I am not sure if that will work for you but I had a similar issue once that it resolved.

---

### Post by SeijiSensei on 2011-06-25
Why not use static IPs for the VMs rather than DHCP?  Then you get to specify the precise address each machine will be using.

---

### Post by YouBuntToo? on 2011-06-27
Thanks for the responses. So, I tried restarting dnsmasq (I had to install it first!) by typing "/etc/init.d/dnsmasq restart" and it gave the following output: "* Restarting DNS forwarder and DHCP server dnsmasq dnsmasq: failed to create listening socket for port 53: Address already in use  [fail]"

-I'm not using VMware or virtualbox. I'm using qemu/kvm and I'm using the virt-manager GUI.

-Here's why I'm not using static IPs. I actually have more than 10 VMs on my server but I will only be running 10 at once. So, I just want the first 10 VMs that are running to be assigned an IP within a specific range of 10 addreses. I might end up using static IPs, but that just wouldn't be the ideal situation.

Thanks.

---

### Post by YouBuntToo? on 2011-06-28
Thanks for the replies. I finally figured it out. The solution was actually quite simple. In virt-manager when you setup a connection it asks for the network address. The address I had previously setup for eth0 was xxx.xxx.xxx.64/26. I used this same one for the virt-manager connection. Obviously, this is why I was getting the error "Error starting network: Internal error Network is already in use by interface eth0".

To fix it, in virt-manager i just used xxx.xxx.xxx.64/27, giving the connection a different block of addresses. This solved the problem entirely. I can't believe it was that simple.

---

