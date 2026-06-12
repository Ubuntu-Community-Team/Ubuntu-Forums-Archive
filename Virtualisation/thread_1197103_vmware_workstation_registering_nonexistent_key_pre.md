---
title: "vmware workstation registering nonexistent key presses?"
date: 2009-06-25
forum: Virtualisation
---

### Post by pythonscript on 2009-06-25
I'm running vmware workstation 6.5 on ubuntu jaunty as the guest and host (don't ask me why, I use the virtual machine for creating live CD's with specific software configurations, and this way, I don't have to keep changing my system every time). However, I'm having a problem with my keyboard typing when I don't want it to... as in, I open up a terminal, firefox, whatever, in the guest, and it suddenly starts typing one letter (different every time) like the key is being pressed down. Ctrl+Alt doesn't work to pull me out of the virtual machine, so I have to open a virtual terminal (that works for some reason) and kill every vmware process. Once I'm out of vmware, it still looks like the key is being pressed down!
 I haven't had this problem at all before I installed vmware, and I've had vmware installed for about 3 months (working perfectly) before this problem materialized. Is there something I'm doing wrong? I just changed the settings in vmware to only use my computer's RAM, not swap space, but that's the only change I've made (and I can't change it back, since then vmware just freezes up all the time and is barely functioning). Any one else having this issue? I've tried installing, uninstalling, reinstalling,etc, Vmware tools, and that doesn't make any difference. Sorry about the long post, but having to do a hard reboot of my *host system* because the keyboard is typing for me is really frustrating when I'm trying to produce CD's. Thanks in advance!

---

### Post by n5wy on 2009-08-04
Anyone have any ideas? I have Ubuntu 9.04 64 bit as a host with the latest VMWare WS 6.5.2 installed. When I create a WinXP guest and reboot it after it completes the install, I had the same problem. 

I would then randomly experience mouse and keyboard craziness in both the guest and the host OS. The only way to make it stop was to reboot and not start VMware again. Once I started the VM guest the sticky key behavior or mouse stuck in guest window would start up again. 

Need help if anyone has figured this out.

---

### Post by pythonscript on 2009-08-04
I haven't been able to find any information about this being a bug with vmware 6.5, but maybe it just hasn't been reported that much yet. I'll let you know if I find anything else, and hopefully others in the community will have this problem. It was simply unusable for me, so I moved to the virtualbox closed source edition.

---

