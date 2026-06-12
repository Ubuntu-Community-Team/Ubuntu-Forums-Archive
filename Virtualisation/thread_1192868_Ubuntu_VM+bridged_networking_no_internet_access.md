---
title: "Ubuntu VM+bridged networking: no internet access"
date: 2009-06-20
forum: Virtualisation
---

### Post by KhurramF on 2009-06-20
I have installed Ubuntu 7.10 as a VM on XP Pro and am using bridged networking. I cant access internet from the VM, but name resolution works. I have used both dhcp and static ip assignments for the VM but it makes no difference. For example, nslookup in the VM resolves [www.google.com](www.google.com), but browsing to it in firefox does not work. Firefox just keeps on showing "connecting to www.google.com..." forever.

A wireshark trace shows the VM making successfull dns queries to the dns server (which runs on the XP host) and then sending tcp syn packets to the website address; there are no return packets from the website. I have disabled the firewall on the XP host but again it makes no difference.

I am really confused why it does not work. What could be wrong with it?

Thanks,
Khurram.

---

### Post by bodhi.zazen on 2009-06-20
Hard to guess. 7.10 is an old version of Ubuntu and I would suggest you try at least 8.04, if not 9.04.

---

### Post by KhurramF on 2009-06-21
> **bodhi.zazen said:**
> Hard to guess. 7.10 is an old version of Ubuntu and I would suggest you try at least 8.04, if not 9.04.
Ok, downloaded 9.04 and installed it in a VM In vmware. But it is exactly the same. I should mention that my XP machine is dual homed (the 2nd interface is connected to the internet through a cable modem) and is running a 3rd party internet sharing software (winproxy). I can ping the addresses in both directions between the host and the VM. If I use a proxy server in the Ubuntu VM, it connects to the internet. Its only the direct connection which does not work :confused:

---

### Post by KhurramF on 2009-06-22
A little update. Installed the latest version of VirtualBox and it just worked right out of the box :) No need for pesky Vmware.

---

