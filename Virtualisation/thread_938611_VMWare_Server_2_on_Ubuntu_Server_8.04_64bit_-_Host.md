---
title: "VMWare Server 2 on Ubuntu Server 8.04 64bit - Host network detection is not running"
date: 2008-10-05
forum: Virtualisation
---

### Post by bkortleven on 2008-10-05
Hi,

I installed VMWare Server 2.0 on a Ubuntu Hardy 64bit server, and installation seemed to have completed fine, no errors..
Now, when starting VMWare server, no errors either, but when I check the vm net status (/usr/lib/vmware/net-services.sh status) I get

Bridged networking on /dev/vmnet0 is running
Host network detection is not running

And there is no connection to the 'outside' in the Guest Windows 2003 Server we are virtualising.

VMWare is using eth0, which is an Intel Gigabit network card in our server (SuperMicro Blade), host connectivity is fine, guest is non-existant...

Any help would really be appreciated, the VM guest needs to be up and running tomorrow morning :s

Thanks!

---

### Post by veloce on 2008-10-05
What does ipconfig /all on the guest show?

You shouldn't need host networking if you're just wanting to connect to "the outside" - bridged is all that is required.

Is your DHCP server on your main network set up to provide the vm with an address?

---

### Post by talishka on 2009-11-19
No news about this?!

---

### Post by dcstar on 2009-11-21
> **talishka said:**
> No news about this?!

If people refuse to provide the information requested to diagnose the problem, then how can any "news" be of any use?

---

