---
title: "Unable to load kernel module"
date: 2009-09-08
forum: Virtualisation
---

### Post by sirajrathore on 2009-09-08
Hi
 
 
I am using ubuntu 8.04 with kernel 2.6.24 server. The NIC (Intel PRO/1000 quad port PT server adapter)  is working properly here and shows all four Interfaces.The driver modules are also loaded correctly
#lsmod | grep e1000
output:
e1000
e1000e

But when i installed openvz virtualization setup . openvz uses a kernel based on kernel 2.6.18. In openvz environment this NIC is not detected.
#uname -r
2.6.18-14-ovz-amd-smp
#lsmod | grep e1000
output:
e1000 
here it only showed e1000. And e1000e did not exists which was required driver for this card,i installed it explicitly. it installed successfull and e1000e.ko had been created. Now when i tried to load this module.It threw an error.
 
#modprobe e1000e

---------------------
output:
e1000e: version magic '2.6.18-14-ovz-amd64-smp SMP mod_unload gcc-4.2' should be '2.6.18-14-ovz-amd64-smp SMP mod_unload gcc-4.1'
FATAL:Error inserting e1000e (/lib/modules/2.6.18-14-ovz-amd64-smp/kernel/drivers/net/e1000e/e1000e.ko): Invalid module format
-----------------------------------------
gcc information: (the following gcc packages are installed on my machine)
#dpkg --get-selections |grep gcc
gcc install
gcc-3.4 install
gcc-3.4-base install
gcc-4.1 install
gcc-4.2 install
gcc-4.2-base install
libgcc1 install
-----------------------------------------
 
Can any body suggest how to handle this problem.

Thanks & Regards
Siraj Rathore

---

### Post by hal10000 on 2009-09-08
I have heard that you can create your own linux kernel for your needs if you install the package [COLOR="Red"] linux-patch-openvz[/COLOR] but i don't know where you can get it from, it's not in the ubuntu repositories.

---

### Post by bodhi.zazen on 2009-09-08
The openvz kernel patch is a bit tricky to manually install.

I suggest you take a look at Proxmox, it is Debian + KVM + OpenVZ.

Otherwise, yes you will probably need to build your own kernel, start with the working kernel and Ubuntu openvz kernel, look to see what the differences are 

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29](http://wiki.openvz.org/Compiling_the_OpenVZ_kernel_%28the_Debian_way%29)

---

### Post by sirajrathore on 2009-09-12
Problem solved:
i used following command:
#modprobe -f e1000e

---

### Post by bodhi.zazen on 2009-09-13
> **sirajrathore said:**
> Problem solved:
i used following command:
#modprobe -f e1000e

Glad you got it working and thank you for posting back the solution.

---

