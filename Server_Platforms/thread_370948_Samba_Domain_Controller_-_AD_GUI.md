---
title: "Samba Domain Controller - AD GUI?"
date: 2007-02-26
forum: Server Platforms
---

### Post by gRoberts on 2007-02-26
Hi all,

We currently have a Windows 2000 SBS Domain Controller but we need to install an Linux based Firewall (IPCOP). Because of the way we have setup our Firewall, we can't use the SBS 2000 machine for DNS/DHCP/WINS but apparently we also cannot run a PDC without those being on the same machine.

Because of this, we need to look into a Linux based PDC, but I need to research how hard/easy it would be to administer. 

So... If I were to use Linux (Samba) as my PDC, could I use the standard AD Users and Computers (in Windows) to connect to the PDC and do what I would normally do?

Can I (as an administrator) in Windows, right click on a Folder I want to share across the network, and make changes as if it was a Windows based PDC?

Any help would be greatfully appareciated.

TIA

Gav

---

### Post by jonathan.lees on 2007-02-26
You can't use AD Users and Computers for a Samba PDC, they are two totally different things. I don't see what IPCOP has to do with you running DNS/DHCP/WINS on your Windows 2000 SBS since it's a firewall. If need be you could let IPCOP be the DHCP and DNS server and you can configure your Win2000 DNS to forward to it. DHCP will work, just that your Win2000 DNS will not get any updates from IPCOP. Also, do you really need WINS?

---

### Post by gRoberts on 2007-02-26
ISA is the Firewall/Proxy. SBS is a PDC/DNS/DHCP etc.

I was informed that DHCP, DNS and WINS need to be enabled on the SBS machine for a PDC to work correctly.

I assumed WINS was required.

---

