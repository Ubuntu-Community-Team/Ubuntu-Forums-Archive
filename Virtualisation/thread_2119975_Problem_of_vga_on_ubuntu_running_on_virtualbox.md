---
title: "Problem of vga on ubuntu running on virtualbox"
date: 2013-02-25
forum: Virtualisation
---

### Post by lastonepanama on 2013-02-25
hello all!
i have  a vga problem with my ubuntu currently running on virtual box.
i don't have a vga installed and i can't solve the problem on my own, please i need your help.
below are the few things i checked on my terminal while trying to fix the problem but couldn't.
**kernel info**
root@passccielab:~# uname -a
Linux passccielab 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
_**vga info**_
root@passccielab:~# sudo lshw -c display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=0
       resources: memory:e0000000-e0ffffff

please help me out.........

---

### Post by lmarmisa on 2013-02-25
If your Ubuntu is desktop edition, try to install GuestAdditions:

[http://www.virtualbox.org/manual/ch04.html#idp11154112](http://www.virtualbox.org/manual/ch04.html#idp11154112)

I do not install the additions in VMs running Ubuntu server.

BTW. I get just the same message in my different Ubuntu VMs. So, don't panic :D:

```
 
sudo lshw -c display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=0
       resources: memory:e0000000-e0ffffff

```

---

### Post by TheFu on 2013-03-03
Sorry, but I do not understand the issue. Let me ask some questions to get a better understanding.

* Which OS is running directly on the hardware?  Server or Desktop edition?
* Which version of Ubuntu are you trying?  12.xx and desktop or server?
* Is there a VGA card inside the PC?
* Are you trying to access the Ubuntu VM on the same PC or remotely, over the network?
* Did you install the VirtualBox Guest Additions into the VM or not?

Is there a reason you are logged in a root?  This is not necessary and actually a terrible idea for 99.99999% of users.  Your normal account should be used.  If you are running as "root", **sudo** is not needed.

---

