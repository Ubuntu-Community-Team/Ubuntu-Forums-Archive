---
title: "firestarter / vista"
date: 2009-03-23
forum: Security
---

### Post by lordgafal on 2009-03-23
Hi 

i have my home server ( samba mostly) witch is under ubuntu 8.10 but i wanted to look at the settings of the firewall so i installed firestarter

now i have some computers running under xp / vista in my house and i cant get them to see the server with firestarter, setting policies i got my other computers to see the server but now when i try to access it it sais the server is busy or path is broken.

something i dont understand is how come if firestarter is only configuring iptable how come when i turn off firestarter GUI my pcs all can access the server again?

is my system safe with only iptable ?

how can i set firestater to let my windows machines access my data ?

thank you in advance

---

### Post by hyper_ch on 2009-03-23
by installing firestarter you did close all ports because it modifies the default iptables.

firestarter is no firewall - its merely a config too for iptables.

are you even sure you need to twinker around with iptables?

ubuntu supports now UFW as a method to alter iptables. Have a look at the stickies.

---

### Post by lovinglinux on 2009-03-23
> **lordgafal said:**
> something i dont understand is how come if firestarter is only configuring iptable how come when i turn off firestarter GUI my pcs all can access the server again?


Turning off is not the same as closing the GUI. If you just close Firestarter GUI, then the iptables rules will still be effective. But if you turn Firestarter off, then it basically will replace all current iptables rules with ACCEPT rules. Which means everything will pass through the firewall.

> **lordgafal said:**
> is my system safe with only iptable ?

Yes, but you need to create the rules for it, otherwise it will allow all traffic. Firestarter and UFW are just firewall managers, which means they just make the process of creating iptables rules easy. The real firewall applications is iptables + netfilter.

> iptables is the name of the user space tool by which administrators create rules for the packet filtering (both inbound and outbound) and NAT modules. While technically iptables is merely the tool which controls the packet filtering and NAT rules within the kernel, the name iptables is often used to refer to the entire firewalling infrastructure, including the kernel-level Xtables (sub)framework that provides the API for match and target modules and the actual firewall table traversal for IPv4, IPv6 and ARP. iptables is a standard component of all modern Linux distributions..


> **lordgafal said:**
> how can i set firestater to let my windows machines access my data ?

It is recommended to use UFW + [GUFW]("http://gufw.tuxfamily.org/index.html") instead of Firtestarter. I'm almost sure it has an option to allow traffic in the port used by Samba. Otherwise, you will have to allow incoming traffic on the ports manually.

If you don't know the port, then you will have to check the logs for blocked connections. Firestarer has a monitoring tool, than can be used to easily spot blocked connections. Just try to connect to the server using the Windows machines and check the blocked connections on Firestarter. While this monitoring tool is nice and easy to use, is not recommended that you use Firestarter GUI for this on daily basis, because there are reports of bugs on Firestarter that could lead to security holes and privilege escalation, since Firestarter GUI needs to be run as root.

---

### Post by cdenley on 2009-03-23
Why are you using a firewall? Is there a service you have running which you need to restrict more than it's configuration allows? You can configure samba to only allow connections from LAN IP's. There is no need for a firewall to secure samba.
[https://help.ubuntu.com/community/SettingUpSamba#/etc/samba/smb.conf](https://help.ubuntu.com/community/SettingUpSamba#/etc/samba/smb.conf)

---

