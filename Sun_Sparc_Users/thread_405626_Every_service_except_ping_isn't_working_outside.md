---
title: "Every service except ping isn't working outside"
date: 2007-04-10
forum: Sun Sparc Users
---

### Post by mecubus on 2007-04-10
I have a strange problem. I've just installed a couple of programs, then decided to uninstall them again, and then reboot. After the reboot, nothing was as it was before.

I can start by saying i'm running on a U5, with 6.06. Everything worked fine, before i've installed/uninstall/rebooted the computer. Now to the problem:

My server:
Ip: 192.168.100.6
default gateway: 192.168.100.100

first of all, i've noticed that my interface changed name from eth0 to eth1, so i've had to change /etc/network/interfaces after the reboot. The problem I have is that when I:

ping/ssh localhost both works
ping/ssh 192.168.100.6 (local ip) both works
ping/ssh 192.168.100.100 (local ip to another, but working, computer (tested from different computers)) only ping works.
ping/ssh 192.168.100.200 same as above

When I've try to ping the computer (192.168.100.6) I get a respone, but I can't ssh to it, or connect to it through either apache or glftpd (ftp-daemon). All of these things worked before.

The same problem goes to apt-get update. It only shows connecting to security....[xxx.xxx] and then it won't get anywhere. But when I ping that server, I get a respons. Ive checked interfaces, resolve. I've even tried disabling IPv6. It's nothing to do with my default gateway as every other computer in my LAN works as it should.

Regards,
Mathias

---

### Post by netztier on 2007-04-10
> **mecubus said:**
> I have a strange problem. I've just installed a couple of programs, then decided to uninstall them again, and then reboot. After the reboot, nothing was as it was before.

I can start by saying i'm running on a U5, with 6.06. Everything worked fine, before i've installed/uninstall/rebooted the computer. Now to the problem:

My server:
Ip: 192.168.100.6
default gateway: 192.168.100.100

first of all, i've noticed that my interface changed name from eth0 to eth1, so i've had to change /etc/network/interfaces after the reboot. The problem I have is that when I:

ping/ssh localhost both works
ping/ssh 192.168.100.6 (local ip) both works
ping/ssh 192.168.100.100 (local ip to another, but working, computer (tested from different computers)) only ping works.
ping/ssh 192.168.100.200 same as above

When I've try to ping the computer (192.168.100.6) I get a respone, but I can't ssh to it, or connect to it through either apache or glftpd (ftp-daemon). All of these things worked before.

The same problem goes to apt-get update. It only shows connecting to security....[xxx.xxx] and then it won't get anywhere. But when I ping that server, I get a respons. Ive checked interfaces, resolve. I've even tried disabling IPv6. It's nothing to do with my default gateway as every other computer in my LAN works as it should.

Regards,
Mathias

... and where does this relate to SPARC? Sounds like a post for "Networking & Wireless" instead.

Changing/swapping eth0/eth1 assignments are best corrected via /etc/iftab by mapping MAC-address(es) to ethX names. 

What about name resolution? Do you obtain your IP address by DHCP? if yes, does the DHCP answer include DNS information? Is this information correctly transferred to /etc/resolv.conf ?

best regards

Marc

---

### Post by mecubus on 2007-04-10
Well, it's running on a sparc ;) But maybe I should have posted it somewhere else.

No, it's static. 
I've noticed a couple of other things too.

I have several computers in my LAN, named:

192.168.100.5
192.168.100.11
192.168.100.12
192.168.100.200
192.168.100.254

etc.

When I've tried pinging those, only 200, and 254 did I get a respone from. The other, I got "Destination unreachable". It's on the same LAN, same switch, same subnet etc. They all can ping each other with out a problem.

Another thing i've noticed that seems a bit strange is:
eth1 has hw adress: ff:ff:ff:ff:ff:ff

And during boot I get:
eth0: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet ff:ff:ff:ff:ff:ff
eth1: Link is up using internal transceiver at 100Mb/s, Full Duplex.

I only have 1 network card installed.

---

### Post by mecubus on 2007-04-10
Just noticed one more thing. I've figured it would be the hw-adress that is causing all the problem, so i've googled it for a while and found that it could be something to do with IDPROM. 

During the boot-sceen (OpenBoot) it shows the right hw-addrs staring with 08:00:20....

but when I've selected Linux in the boot menu, and after the kernel is loaded, it says:

IDPROM: Warning, unknown format type!

---

