---
title: "Reboot command does shutdown system"
date: 2014-04-15
forum: Server Platforms
---

### Post by z-p30p13 on 2014-04-15
Hi.
Have some problem with restart server supermicro on Ubuntu server 13.10.

Command^
```

reboot
shutdown -r now
init 6

```
dont restart my server, but after it shutdown... I need to push power button every time.
What i do to resolve this issue:
[first :]("http://ubuntuforums.org/showthread.php?t=2024096&p=12121966#post12121966") appent file [COLOR=#000000]/etc/modprobe.d/blacklist.conf by [/COLOR][I]
         # Make system reboot
          blacklist mei
[/I]
[second :]("http://ubuntuforums.org/archive/index.php/t-1776484.html") write at /etc/default/grub 
             GRUB_CMDLINE_LINUX_DAFAULT="acpi=force reboot=acpi" or 
             GRUB_CMDLINE_LINUX_DAFAULT="acpi=force reboot=warm"

but it doesn't help me.

any suggestion?

[B]UPD 1
[/B]Just install unbuntu 10.04 LTS - reboot work fine... but it doesn't detect all pci ethernet card and one onboard lan.
and on ```

cat /proc/cmdline

``` show ".... ro queit" - queit is GRUB_CMDLINET_LINUX_DEFAULT param

---

### Post by z-p30p13 on 2014-04-17
Ubuntu 13.10 by default has kernel 3.11.0-12-generic.
SO, problem solved by downgrade kernel to 3.5.7.


here is howto:
1. Create folder for example /home/kernel/3.5.17 and go inside.
2. download kernel
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.7.33-quantal/linux-image-extra-3.5.7-03050733-generic_3.5.7-03050733.201404040652_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.7.33-quantal/linux-image-3.5.7-03050733-generic_3.5.7-03050733.201404040652_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.7.33-quantal/linux-headers-3.5.7-03050733-generic_3.5.7-03050733.201404040652_amd64.deb

```
2.1 install new kernel:
```

dpkg -i *.deb

```
3. remove old kernel by
```

apt-get remove linux-\.\*3\.11\.\*

```
4. update grub
```

update-grub

```
After first reboot system halt.
After new start - system wiil be with new kernel and reboot currectly.

thanks for reading

---

