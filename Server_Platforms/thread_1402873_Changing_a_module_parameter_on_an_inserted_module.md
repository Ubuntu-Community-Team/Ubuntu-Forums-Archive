---
title: "Changing a module parameter on an inserted module"
date: 2010-02-09
forum: Server Platforms
---

### Post by alecm3 on 2010-02-09
I need do change a module parameter on the module that is already inserted in the kernel. What is the least invasive way to do this, since it's on a production machine that I cannot reboot?
I was going to do
```
modprobe -r ipt_recent
modprobe ipt_recent ip_list_tot=500
```
(I need to change ip_list_tot parameter)
but I get 
```
# modprobe -r ipt_recent
FATAL: Module ipt_recent is in use.
```

---

### Post by kiranmurari on 2010-02-10
Hi,

> # modprobe -r ipt_recent
FATAL: Module ipt_recent is in use.This tells that the ipt_recent module is being used by some other module.
Before removing a module using modprobe, the "Used by" count should be zero for that module.
From lsmod output check which other module is using xt_recent (xt_recent &
ipt_recent are aliases of each other)
First remove the module which is using xt_recent(ipt_recent) module.
```
$ modprobe -r <MODULE USING xt_recent>
$ modprobe -r ipt_recent
$ modprobe ipt_recent ip_list_tot=500
```Don't forget to re-insert the module which was using xt_recent.
```
$ modprobe <MODULE USING xt_recent>
```Hope this helps.

---

### Post by alecm3 on 2010-02-11
> **kiranmurari said:**
> Hi,

This tells that the ipt_recent module is being used by some other module.
Before removing a module using modprobe, the "Used by" count should be zero for that module.
From lsmod output check which other module is using xt_recent robe ipt_recent ip_list_tot=500[/CODE]Don't forget to re-insert the module which was using xt_recent.
```
$ modprobe <MODULE USING xt_recent>
```Hope this helps.

Thank you. It shows that it's used by 18! modules
```
# lsmod 
xt_recent              18848  18
```
Removing and re-inserting 18 modules is almost equivalent to rebooting the machine. Is it possible to just modify its parameter without removing it, while it's loaded in the kernel?

---

### Post by kiranmurari on 2010-02-22
Hi,
 
In order to change the module parameter, even if the module is loaded. You can do this by making changes to /sys/module/xt_recent/parameters/ip_list_tot file.
```
sudo echo 500 > /sys/module/xt_recent/parameters/ip_list_tot
```But to do this, you need to have write permissions enabled on that file.      

Hope this helps.

---

