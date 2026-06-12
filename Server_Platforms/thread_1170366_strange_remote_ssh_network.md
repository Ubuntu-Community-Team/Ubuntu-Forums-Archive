---
title: "strange remote ssh network"
date: 2009-05-26
forum: Server Platforms
---

### Post by salim.madni on 2009-05-26
dear gurus

yesterday i build a new machine vmware workstationm, it is ubuntu 8.10 server.

- i install with openssh,dns,samba server option
- then i install webmin,axigen,clamav some related packages
- now the whole day i work fine

now today when i come to office, machine was as it is, i found i cant connect ssh,putty, even not only this. we cant reach to machine and machine cant reach to us. however the virtual machine works fine, network is ok.

i check all network config also fine.

kindly advise all possible files,health checkup what could be reason the machine is on network and no response of ping,ssh.

kindly advise
salim

---

### Post by LepeKaname on 2009-05-26
Did your vmware ubuntu server is using a static IP? if so, uninstall the dhcp3-client (and any other dhcp client you may have installed), then kill it from memory or restart. Be sure your /etc/resolv.conf has a nameserver there. 

What ethernet device are you using in your .vmx ?
I have:

ethernet0.virtualDev = "vlance"

---

