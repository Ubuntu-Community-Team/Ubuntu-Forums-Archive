---
title: "KVM Networking Confusion"
date: 2018-07-29
forum: Virtualisation
---

### Post by nowell29 on 2018-07-29
Okay, so I have been trying to figure this out for a few days.  I have run ubuntu VMs for several years, but this is the first time I have used it for KVM host.  I am having issues with networking that I cannot solve.  Additionally, I am not fond of netplan.  boo.  

Here is my setup:
DSL --> VM of PFsense as gateway --> LAN
KVM host is 18.04
I have multiple hosts on the LAN wired and not wired, and all work, except the VMs and the host itself!  
I setup one NIC on my 18.04 host to be a LAN adapter.  I setup the second NIC on my 18.04 to be a dedicated interface to the pfsense VM which does my DSL PPPoe and gets my public IP.  All the hosts/clients/VMs get their IPs either dhcp or by static assignment and use this pfsense as their gateway.  I have used this setup successfully for year+ but was using CentOS as my KVM host.  

Problem:
All hosts on the LAN can use the network just fine.  This includes laptops, Roku, xbox, cell phone wifi, others.  On my KVM host I have a handful of VMs.  One is Windows 7 with rdp.  I have a couple ubuntu vms for various things.  I started this fight because I could not translate ports into my lan from WAN to these ubuntu vms.  Ironically I can rdp through, but I cannot SSH or http through.  So I started troubleshooting firewall issues (with no success) until I noticed that my ubuntu VMs and my ubuntu KVM host could not get updates.
I began troubleshooting them and they all timed out when running updates.  I found that I could ping outside of the LAN, and I can resolve via DNS, but traffic doesnt seem to be passing.  There is where I am stumped.  I was able to setup a squid proxy on a different machine on the LAN, and I could get updates on both VMs and KVM host through that, but not without it.  I was able to do a wget from the host to a VM webserver, which confuses things.  Why would a wget work, but updates would not.  From a ubuntu VM i cannot reach anything by browser.

So, I have disabled IPv6, tried rebooting many times, did get the updates through the proxy and rebooted, cleared iptables that were defaulted.  I am stumped.

Here is my /etc/network/interfaces (I could not get netplan to even connect, so I installed the ifupdown that it states to do in the conf file):

duke:~ # cat /etc/network/interfaces
# ifupdown has been replaced by netplan(5) on this system.  See
# /etc/netplan for current configuration.
# To re-enable ifupdown on this system, you can run:
#    sudo apt install ifupdown
#


auto lo
auto eno1
auto br0

iface lo inet loopback
#address 127.0.0.1
#netmask 255.0.0.0

iface eno1 inet manual 

iface br0 inet static
bridge_ports eno1
bridge_stp off
bridge_fd 0
bridge_maxwait 0
address 10.10.10.17
netmask 255.255.255.0
gateway 10.10.10.1
dns-nameservers 10.10.10.1


10.10.10.1 is the pfsense VM that is on the KVM host, it is my DSL gateway and DNSresolver (which as I stated before worked before on CentOS KVM host, and works currently for LAN clients).

pfsense:
    <interface type='bridge'>
      <mac address='52:54:00:a1:28:a0'/>
      <source bridge='br0'/>
      <model type='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <interface type='direct'>
      <mac address='52:54:00:d0:84:4e'/>
      <source dev='eno2' mode='passthrough'/>
      <model type='e1000'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </interface>

and host ubuntu KVM:

duke:~ # ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 00:1e:c9:2b:3a:2d brd ff:ff:ff:ff:ff:ff
3: eno2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 52:54:00:d0:84:4e brd ff:ff:ff:ff:ff:ff
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 00:1e:c9:2b:3a:2d brd ff:ff:ff:ff:ff:ff
    inet 10.10.10.17/24 brd 10.10.10.255 scope global br0
       valid_lft forever preferred_lft forever
5: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:f4:76:63 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
6: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:f4:76:63 brd ff:ff:ff:ff:ff:ff
7: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:a4:ab:e8 brd ff:ff:ff:ff:ff:ff
8: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:a1:28:a0 brd ff:ff:ff:ff:ff:ff
9: macvtap0@eno2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 500
    link/ether 52:54:00:d0:84:4e brd ff:ff:ff:ff:ff:ff

---

### Post by jakkuk on 2018-07-30
can you ping from duke to 8.8.8.8? Does duke resolve DNS names properly?

I understand that you connect your VMs to the br0 bridge - is that right? 

Can you ping every VM from the LAN network? Can every VM connect to some other service on the VM network? Or ping 10.10.10.17?

Can you post screenshots from network configuration in KVM of one of the VMs?

Do you have any other network cards configured in NetworkManager?

---

### Post by nowell29 on 2018-07-31
Interesting change in circumstances.  I could:
I could ping externally, and yes DNS resolved from KVM host.
I can ping VMs from the LAN to VM guests, and I can even SSH from one VM to another.  this is what was most weird to me.  Basic connectivity seemed to be working!
I am not using NetworkManager on the KVM host, nor on some of the VMs.  I have one of these VMs statically assigned:
jump ~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:a4:ab:e8 brd ff:ff:ff:ff:ff:ff
    inet 10.10.10.6/24 brd 10.10.10.255 scope global eth0
       valid_lft forever preferred_lft forever
jump ~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 10.10.10.6
    netmask 255.255.255.0
    gateway 10.10.10.1
    dns-search local 
    dns-nameservers 10.10.10.1

So here is the interesting part.  I started looking for any clues through logs.  I saw grief about apparmor.  :(  so, while apparmor, like selinux, is great and all, I tend to turn it off for silly situations like this, especially during troubleshooting.
So now that I have it disabled (and fully rebooted), I can now use my VMs but my KVM host itself wont take its IP assignment!  Nothing is different than what i posted above about the br0 static assignment, but now the output of 'ip a' says that br0 has no IP assigned.  A simply ifup br0 says that the interface is already configured and up, but I have zero connectivity from the KVM host.  nothing to or from now with standard expected message of "network unreachable"

So, apparmor.  grrr.  My pfsense gateway still works just fine, including the connection I am using to write/post this.  My 'jump' vm that I posted above I can SSH to.  Both of these VMs share that br0 interface for LAN IPs.  Clients on my LAN get their DHCP from the pfsense gateway just fine and get their DNS.  Only difference between now and prior posting is the toggling of apparmor.  My 'jump' VM still cannot apt update unless I use the proxy.  I'll be troubleshooting apparmor configs now.

---

### Post by TheFu on 2018-08-10
I had a similar issue with a 14.04 KVM host a few weeks ago.  All VMs worked fine, except for (1) 16.04 VM.  It worked perfectly on the LAN, but couldn't ping the internet by IP or with DNS.  DNS resolution was working fine, but I run an internal LAN DNS that also caches internet IPs.  The problem VM had been relatively unmodified, except weekly patching for months - like 6-12 months.  I patched on a Saturday and that single VM probably started having the issue.

Then 2 days later, it started working again and has been fine all this time.  I didn't reboot the VM host.  I didn't alter any network settings on the VM host, router, or any switching.  It just started working.

I posted here with the issue details. [https://ubuntuforums.org/showthread.php?t=2396877](https://ubuntuforums.org/showthread.php?t=2396877)  Didn't get any responses.  I did notice that on my VM host, network performance was about 50% less than normal which lead me to notice the bridge wasn't using PR0/1000 Intel NICs, but an onboard Marvell.
During the next maintenance period, I switched the networking off the Marvell to where it belongs on the Intel and cleaned up a few extra unused bridges. I doubt this did help or will in the future, but Intel e1000e drivers are pretty stable.

18.04 is too new for my use, so I can't help specifically with this issue.

---

