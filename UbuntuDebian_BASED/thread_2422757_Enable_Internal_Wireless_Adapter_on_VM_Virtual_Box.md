---
title: "Enable Internal Wireless Adapter on VM Virtual Box IN KALI LINUX (Wlan0..)"
date: 2019-07-12
forum: Ubuntu/Debian BASED
---

### Post by benjaminout on 2019-07-12
Hi i'm totally new in this world of ubuntu and linux , i did install Kali Linux on Virtual box and i want to enable the wireless connection
i did switch to Bridged Adapter too ,
I did download this file( compat-wireless-2010-06-26-p.tar) and excuted the steps in youtube video [[https://www.youtube.com/watch?v=tWslvnI4SwA]](https://www.youtube.com/watch?v=tWslvnI4SwA])
1) cd desktop
2)ls
3)tar -jxvf 
4)ls 
5)make unload
6)make load
all went good except the last step after making command "make load" i get this message at the end  

[COLOR=#111111][FONT=Roboto]Active: inactive (dead) 
[/FONT][/COLOR][COLOR=#111111][FONT=Roboto]Docs:  man:bluetoothd(8) 
[/FONT][/COLOR][COLOR=#111111][FONT=Roboto]make:  [/FONT][/COLOR][COLOR=#111111][FONT=Roboto]***[/FONT][/COLOR][COLOR=#111111][FONT=Roboto] [makefile:344:load] Error 3

images: [/FONT][/COLOR]https://prnt.sc/oe2fiw    [https://prnt.sc/oe2gn1](https://prnt.sc/oe2gn1)   [https://prnt.sc/oe2iiz](https://prnt.sc/oe2iiz)[COLOR=#111111][FONT=Roboto]
please help

 soryy for the unorganisaton of my Thread [/FONT][/COLOR]

---

### Post by jeremy31 on 2019-07-12
Moved to Ubuntu/Debian based

---

### Post by TheFu on 2019-07-13
Inside a VM, access to the real hardware isn't possible without doing something extra.  I don't know what vbox supports in the way of PCIe passthru, but you might be able to passthru a USB2 wifi device.  When you do the passthru, it must be exclusive access, so either the host has it or the VM has it. Both cannot share it.  This applies to all hardware being passed thru - network cards, GPUs, storage controllers.  Many laptops don't have the necessary hardware on the motherboard to support PCIe passthru, so you'd want to check that before doing anything else.
```
$ dmesg |grep -i iommu
```

Also, when posting commands, please post the exact command used and please wrap in "code tags". See my example.  That tar command #3 above won't do anything without more arguments.

---

