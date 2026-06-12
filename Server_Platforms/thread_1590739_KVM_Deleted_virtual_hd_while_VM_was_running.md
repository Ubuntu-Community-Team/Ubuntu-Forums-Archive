---
title: "KVM: Deleted virtual hd while VM was running"
date: 2010-10-08
forum: Server Platforms
---

### Post by mstuehrenberg on 2010-10-08
Hi there,

I've accidentally removed (rm -r) the ubuntu-kvm folder that stores the virtual partitions of my VM. The VM itself is still running. The machine is still accessible over the net (it is a webserver) but since there is no more virtual storage I guess there is no way to regain its contents. Are there any steps I can do to regain the machine? I guess if I just reinstall the machine by means of vmbuilder all newly created discs will be more or less blank.

Regards,

---

### Post by HermanAB on 2010-10-08
Howdy,

The files were marked for deletion, but since they were in use, they are still there for the time being.  The moment you stop that machine, it will disappear in a puff of smoke.  So you should log in and copy off anything you need to save, then make a new system.

---

### Post by dtfinch on 2010-10-08
You can use lsof to find details about which process has it open and such, then you can recover it from /proc/[processid]/fd/
[http://www.linuxplanet.com/linuxplanet/tips/6767/1/](http://www.linuxplanet.com/linuxplanet/tips/6767/1/)

---

### Post by mstuehrenberg on 2010-10-11
Thank you both, that did the trick.

Regards,

---

