---
title: "Xen network issue"
date: 2014-02-22
forum: Virtualisation
---

### Post by QR72e on 2014-02-22
Hi all,

ususally I seem to find solutions to my issues by means of google or in these forums, but no luck this time and so I am posting this thread.

I have installed Ubuntu server 13.04 and installed the Xen Hypervisor, Xen-XAPI and QEMU-Common packages.
Then I adjusted grub to always boot into the hypervisor.

From this moment on my network card only picks up an IP address form the DHCP server, but I can not access any other machine on my LAN nor on the Internet. Pinging the own IP address works, pinging the default gateway or any other machine on the network results in "Destination Host Unreachable".

Restarting the machine and booting in "standard" Ubuntu instead of Xen 4.2, by selecting anonther boot option in Grub and not changing anything else the network seems to work just fine.

I have checked IPtables, routing, ifconfig, syslog, but no hint to what may cause this issue.

There are probably some people in here that have much more experience than myself when it comes to Xen and I hope to receive some help from you. I assume that it is an issue within Xen, as it is working when booting without it.

Any hint or advise is highly appreciated.

//QR72e

---

### Post by howefield on 2014-02-22
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?t=2207134](http://ubuntuforums.org/showthread.php?t=2207134)

---

