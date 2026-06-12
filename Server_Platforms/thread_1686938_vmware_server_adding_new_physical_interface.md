---
title: "vmware server adding new physical interface"
date: 2011-02-13
forum: Server Platforms
---

### Post by creatureofthedark on 2011-02-13
hey i have vmware server 2.0 installed on a ubuntu server... when i installed vmware server 2.0 i only had 1 interface configured... i would now like to enable the other interface and make a new vswitch for it.... can anyone tell me how this is done??


i installed vmware server using this [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

from my searching around the internet i found that if i run vmware-config.pl i should be able to.... but.. when i try this i get the following error...


creature@mew:~/raducotescu-vmware-server-linux-2.6.3x-kernel-71f8b66$ sudo vmware-config.pl
The following VMware kernel modules have been found on your system that were
not installed by the VMware Installer.  Please remove them then run this
installer again.

vmmon
vmnet
vmci

I.e. - 'rm /lib/modules/2.6.32-24-server/misc/<ModuleName>.{o,ko}'

Execution aborted.


i dont want to remove these files in case they are important....

any help hear would be amazing!!!

---

### Post by creatureofthedark on 2011-02-13
SOLVED :P

i re installed :P

---

