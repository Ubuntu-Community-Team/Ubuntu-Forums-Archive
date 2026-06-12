---
title: "Slow VM Ware networking"
date: 2009-11-02
forum: Virtualisation
---

### Post by RealG187 on 2009-11-02
If I use Bridged networking Samba is slow ([when I don't get this stupid error)]("http://ubuntuforums.org/showthread.php?t=1082148") and when I use NAT the Internet Browsing is slow. When I use both, both are slow. How do I make them both fast?

---

### Post by sdowney717 on 2009-11-03
how did you setup your bridge?
this is my interfaces file using eth2, most people will be eth0
adjust your ip numbers to your system

> #originally just these next 2 lines were in here
#auto lo
#iface lo inet loopback

#static on eth2, static on bridge br0
auto eth2
iface eth2 inet manual

auto br0
iface br0 inet static
        address 192.168.1.100
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth2
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0


---

### Post by RealG187 on 2009-11-03
I am running Ubuntu in the VM and using Windows 7 has the host (the way things at school work now, Windows 7 on all the computers with VM Ware)

---

