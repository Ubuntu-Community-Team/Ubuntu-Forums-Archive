---
title: "vmware player - no ethernet after kernel upgrade"
date: 2009-04-12
forum: Virtualisation
---

### Post by jdaum on 2009-04-12
Hi,

(I think) since the kernel upgrade to 2.6.24-23 I don't have ethernet anymore in my Win Vista VM in VMWare Player. I also can't find the vmware-config.pl script anymore that I used for vmware server. A website I found says that there is now a graphical interface for this, but I can't see one. I got Player 2.5.1 build-126130.

I also found a script to compile the kernel headers manually, but when I go sudo /etc/init.d/vmware restart  it still fails to start the network. The error message in player is "can't find /vmnet0"

Any ideas where to go next?

Kind Regards,

Jochen

---

### Post by HermanAB on 2009-04-13
Howdy,

You have to reinstall VMware Player.

If you are working with VMs, then it is best not to update your host kernel, unless you actually enjoy re-installing the VM system every time.

---

### Post by jdaum on 2009-04-13
Ok, I've installed VMWare Workstation Trial instead. There were a couple of other functions I have eyed, just didn't want to spend the money now.

Thanks for your answer,

Jochen

---

### Post by Shazaam on 2009-04-13
Also, if you install dkms (through Synaptic) it will rebuild the vmware kernel modules (and others) when you do a kernel update on the host.
[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)

---

