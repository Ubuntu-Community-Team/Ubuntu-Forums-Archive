---
title: "Virtual Box issues on Ubuntu 12.04"
date: 2012-01-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by girisharam on 2012-01-30
Because I could not get Ubuntu 11.x to install on my new Dell XPS 702 laptop, I downloaded and installed the latest version of Ubuntu 12.04 that is still in beta. The new version of Ubuntu runs well.

I then installed VirtualBox 4.1.8 r.75467, ceated a couple of VM's running Windows XP and it works well. I then decided that i wanted a CentOS guest OS.

I found that the CentOS guest is unable to get an IP address. I've tried the various network settings on the virtual box but I'm unsuccessful to make a connection outside. I'm not sure if the issues is related to VirtualBox or with Ubuntu or with CentOS. I know there is nothing wrong with CentOS because I had installed another VM on a different machine running Ubuntu 10.04 and it works flawlessly. 

Any advice for me?

Thanks
Girish

---

### Post by jbicha on 2012-01-30
Ubuntu 11.10 32-bit inside VirtualBox inside Ubuntu 12.04 64-bit works fine here, including networking.

---

### Post by effenberg0x0 on 2012-01-30
It could be a number of things. I'll try to mention some that come to mind. 

In VirtualBox / Settings / Network you get to choose how the VM will use the network. Make sure "Adapter 1"/"Enable Network Adapter" is checked, of course. It would be interesting to know what are your settings there for this VM and if all your working Linux VMs (the ones that can get an IP) share the same settings (NAT, Bridged, etc). 

If you run VMs simultaneously, make sure they're not set to use the same MAC (and IP) in your DHCPd server.

In case you're relying on an external DHCP server, like a home router or another server, you gotta make sure this DHCPd is ready to accept connections from the VM fake MAC address and has an available IP to give to it.

In my setup: each of my VMs NICs has a different fake MAC Address and my isc-dhcpd-server (on another server, but also running UBuntu PP) has a fixed IP/Host set for each of this MACs configured in /etc/dhcp/dhcpd.conf. And that implies that the server firewall (UFW) is set to accept connections from the VMs IPs in the standard ports (DHCPd, DNS, etc). If you're running UFW or any other firewall locally, check its log to make sure DHCP ports are allowed.

As an easier approach: Using NAT, VirtualBox should give it a fake IP address, like 10.x.x.x. In Bridged mode, it will share the PC real IP address. And in Internal Network mode, it will only see the host. The first two should work out of the box for a working IP.

If you have this machine or other in the LAN running dnsmasq, make sure its basic DHCPd capabilities are disabled in /etc/dnsmasq.conf if you already have a working dhcp in your network (isc-dhcpd or a router, windows server, etc). While XP is less strict to accept DHCP leases, Linux can simply refuse to get an IP in a network with a confusing topology.

And, obviously, CentOS should be set to get an IP address. It must have a working DHCP client started. I wouldn't be able to help you with that, as I use Ubuntu.

Also, make sure you have the necessary VirtualBox kernel modules loaded. You should see this:
```
[01:29 AM][ahsl:AL-DESK:~/dev/ccsm-test]
$ sudo lsmod | grep -i vbox
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
```

If you don't have the modules loaded like you see above, you can try to sudo apt-get install --reinstall virtualbox-dkms (or virtualbox-ose-dkms, depending on how you have installed VirtualBox).

OBS: You can click on Devices / Network Adapters in VirtualBox while the CentOS VM is running, and you can change network settings on the fly. XP/Ubuntu recognize and work perfectly when I change network modes and even NIC type. CentOS probably will too, so you can test stuff while the VM is running. Example: start a local dhcpd, start logging UFW and change the VM mode to Generic. Inside CentOS try to get an IP via DHCP client. See if it works and what's in logs, etc.

---

### Post by girisharam on 2012-01-31
Thank you for the feedback!

The network settings on the Windows XP and the CentOS (6.2 64 bit) is the same (NAT). I've tried changing it to Bridged (for the CentOS VM) and it did not work.

The vbox networking modules are installed:
#lsmod | grep -i vbox
 vboxpci                23200  0 
 vboxnetadp             13382  0 
 vboxnetflt             23441  1 
 vboxdrv               282739  4 vboxpci,vboxnetadp,vboxnetflt

I'm going to attempt installing a Ubuntu 11.10 vm and see if its running into similar issues.

Thanks
Girish

---

### Post by girisharam on 2012-01-31
Ubuntu 11.10 vm inside Ubuntu 12 works well. Networking is working well. I now wonder if the issue is related to CentOS 6.2. I'm now trying to setup  CentOS 5.7 machine.

Will keep you posted of my findings.

Thanks
Girish

---

### Post by girisharam on 2012-02-01
Here is the update on my issue.

Looks like the build from Ubuntu yesterday resolved my networking issue. I can now connect from my CentOS 6 vm.


Thank you all for your suggestions.

Thanks
Girish

---

