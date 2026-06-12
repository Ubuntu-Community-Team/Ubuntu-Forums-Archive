---
title: "File transfer from linux to OS in VMWare Help"
date: 2014-08-06
forum: Virtualisation
---

### Post by firas2 on 2014-08-06
[COLOR=#000000][FONT=Lucida Grande]Good day[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]I was fallowing a tutorial on how to transfer folders and files from Youtube [/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]every thing went well but cant see the folder on windows [/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]I have Linux Mint 17 on a virtual machine ,, the virtual machine is connected to the internet through a bridge connection so it looks like i have the same ip address , could this be the problem ??[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]my main concern is that I would Like to transfer files from mint 17 to windows if any one here can recommend anything I will be thankful[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I  am using VM workstation 10 [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]so i install linux mint on the vm and i think both of them are using the same ip address it looks like it [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]sorry for not giving enough info Forgive me im new and yes both are connected to the same router with one T6 cable [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]so what would u suggest ? how can we make this work ??[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]any recommendations ??


and because I am new and maybe i am not putting all the info out  please look here 

[/FONT][/COLOR][http://i58.tinypic.com/xcisz6.jpg](http://i58.tinypic.com/xcisz6.jpg)

thank u

---

### Post by TheFu on 2014-08-07
If the VM and the hostOS run on the same subnet, then you can use any of the normal network-based file sharing methods with the server on either Windows or on Linux - your choice.  It sounds like you've setup a VM NAT network, so the guests are on a different private network. That's fine, but it restricts how network connections can be made.  I prefer to use bridged mode that allows my VMs to appear just like any other physical hosts on the network, but the VMs have the same risks of being hacked as all the other systems that way.

Or  I'm fairly certain that VMware Workstation supports sharing hostOS storage with guest OSes.  I haven't touched Workstation since the 1990s, but in Virtualbox, it is the last tab in the VM settings that configures that. It is a security risk for both the guest and the hostOSes - whatever - then just mount the storage inside the guestOS just like any other new storage would be mounted.  I'm assuming that because you are using virtualization AND Linux that you already know how to do that.

---

### Post by firas2 on 2014-08-07
> **TheFu said:**
> If the VM and the hostOS run on the same subnet, then you can use any of the normal network-based file sharing methods with the server on either Windows or on Linux - your choice.  It sounds like you've setup a VM NAT network, so the guests are on a different private network. That's fine, but it restricts how network connections can be made.  I prefer to use bridged mode that allows my VMs to appear just like any other physical hosts on the network, but the VMs have the same risks of being hacked as all the other systems that way.

Or  I'm fairly certain that VMware Workstation supports sharing hostOS storage with guest OSes.  I haven't touched Workstation since the 1990s, but in Virtualbox, it is the last tab in the VM settings that configures that. It is a security risk for both the guest and the hostOSes - whatever - then just mount the storage inside the guestOS just like any other new storage would be mounted.  I'm assuming that because you are using virtualization AND Linux that you already know how to do that.


Thanks for the explanation    solved

---

