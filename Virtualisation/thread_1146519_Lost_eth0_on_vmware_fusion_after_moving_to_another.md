---
title: "Lost eth0 on vmware fusion after moving to another computer"
date: 2009-05-02
forum: Virtualisation
---

### Post by opus_az on 2009-05-02
Hello....This may be one for the VMWare Fusion folks but I thought I'd ask here, too.

Ubuntu 8.04 server was on a vmware fusion 1.1.1. Then I copied it to another computer with vmware fusion 2.0.

Now the Ubuntu lost its eth0. I tried upgrading the virtual machine from the menu item. No help.

$ sudo /etc/init.d/networking restart

eth0: ERROR while getting interface flags: No such device

SIOCSIFADDR: No such device

$ifconfig ;only shows lo

Any suggestions?

Thx,

D.

---

### Post by opus_az on 2009-05-02
Nevermind, I got it. I was choosing "copied it" in vmware fusion when first starting the VM. Should have chosen "moved it" for this instance. :)

---

### Post by daffy_dowden on 2009-11-19
I came across this problem too, but I wanted to copy the machine (figured that's the easiest way to clone an instance) Anyway, I discovered a [solution to the problem here]("http://muffinresearch.co.uk/archives/2008/07/13/vmware-siocsifaddr-no-such-device-eth0-after-cloning/") where you simply delete the instances duplicated MAC address from a config file and reboot. Problem solved!

Daf

---

