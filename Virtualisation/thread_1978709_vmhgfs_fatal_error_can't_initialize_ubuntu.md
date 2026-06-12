---
title: "vmhgfs fatal error: can't initialize ubuntu"
date: 2012-05-12
forum: Virtualisation
---

### Post by Enot on 2012-05-12
This morning i found that i can't initialize anymore my virtual machine, i think i have a problem issue with virtual machine addition or something like that: cannot load vmhgfs and vmsync modules, anyway i can't set up terminal for reinstall virtual machines or remove, what could i do? anyone with the same issue? I hope you could help me, i take a snapshot for show up what's happening:

[IMG]http://i47.tinypic.com/1zgx7ib.jpg[/IMG]


Regards!

---

### Post by Enot on 2012-05-12
Well, i fix it finally making an uninstall though the recovery mode with the below command:

vmware-uninstall-tools.pl


Just only left reinstalling again with "sudo apt-get install open-vm-tools" i don't know why Ubuntu and VMware have so many problems of compatibility.

---

