---
title: "VMware Player on Windows 7 host internet connection problems"
date: 2012-03-27
forum: Virtualisation
---

### Post by kameradin on 2012-03-27
Hi all,
I've been using VMware to run Ubuntu but can't get an internet connection in Ubuntu while at school. My school's internet seems to give only one IP to each mac address, so I assume I have to use a NAT network connection. However, I'm having trouble setting this up; I'm assuming I have to do more than simply switch the vm's settings to "NAT" but I'm not sure what those other things are. I have Windows firewall disabled. Any help would be appreciated.

---

### Post by nothingspecial on 2012-03-30
*Thread moved to **Virtualization**.*

---

### Post by dcstar on 2012-03-31
> **kameradin said:**
> Hi all,
I've been using VMware to run Ubuntu but can't get an internet connection in Ubuntu while at school. My school's internet seems to give only one IP to each mac address, so I assume I have to use a NAT network connection. However, I'm having trouble setting this up; I'm assuming I have to do more than simply switch the vm's settings to "NAT" but I'm not sure what those other things are. I have Windows firewall disabled. Any help would be appreciated.

Simply selecting NAT in the VM's options should work for basic network access - assuming that the NAT networking was set up when VMware (whatever?) was installed.

Most schools use Proxy Servers for Internet access, so if you have not set that up in Ubuntu then it will not work.

---

