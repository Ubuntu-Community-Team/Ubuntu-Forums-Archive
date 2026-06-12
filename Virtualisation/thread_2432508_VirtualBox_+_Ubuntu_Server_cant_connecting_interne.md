---
title: "VirtualBox + Ubuntu Server cant connecting internet"
date: 2019-12-03
forum: Virtualisation
---

### Post by maksel on 2019-12-03
Ubuntu server 18.04 lts
When trying to download openssh-server, do not connect [https://imgur.com/a/1OYa9lL](https://imgur.com/a/1OYa9lL)
screen ifcongig [https://imgur.com/a/1M4qmyS](https://imgur.com/a/1M4qmyS)
screen 50-cloud-init.yaml [https://imgur.com/a/iEKps6b](https://imgur.com/a/iEKps6b)
Settings screen (tried everything) [https://imgur.com/a/o4l4UwP](https://imgur.com/a/o4l4UwP)

---

### Post by wildmanne39 on 2019-12-03
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by SeijiSensei on 2019-12-03
It appears you're using Bridged Networking? Try NAT.

Also try a different server for Ubuntu. Maybe the server for RU is having problems.

---

### Post by maksel on 2019-12-03
"[COLOR=#000000]It appears you're using Bridged Networking? Try NAT.[/COLOR]" - i tryed all choises

---

### Post by SeijiSensei on 2019-12-03
Can you not connect to any web sites from the VM, or just the RU Ubuntu repository server?  I believe Ubuntu Server comes with the elinks text-based browser by default.  

In bridged mode, the VM should get an IP address in the same address space as the host computer. If you can connect from the latter, you should be able to connect from the VM, too.

You're not running any firewalls on either the host or the guest, are you? If so, turn them off and see what happens.

---

