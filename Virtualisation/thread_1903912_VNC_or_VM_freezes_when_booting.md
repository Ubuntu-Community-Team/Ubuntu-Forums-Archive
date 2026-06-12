---
title: "VNC or VM freezes when booting"
date: 2012-01-03
forum: Virtualisation
---

### Post by BloodyIron on 2012-01-03
Hi,

I'm using Ubuntu server 10.04 with the initial virtualization installation. I am using another system, ubuntu desktop, with Virtual Machine Manager to interact with ubuntu server which I am trying to use as a host.

I put ISOs in the right location ( /var/lib/libvirt/images ) and they show up. I go and make a new VM, use the default settings and get it to boot off any ISO I have and then when I watch the console it just seems to show the initial screen of starting the BIOS and loading the ISO, but never displays any further.

I am uncertain if the VM is actually getting any further, or if it's frozen completely.

I went to take a look at the logs for the VM and there is no error, the only thing that shows up is the init string which is used, and the VNC string appears to be correct ( -vnc 127.0.0.1:0)

Now, I'm new to LinuxKVM, and this implementation. I tried looking it up, and giving it the old college try and I can't seem to figure out what is going wrong here.

Any ideas?

---

### Post by BloodyIron on 2012-01-06
Bump

---

### Post by BloodyIron on 2012-01-09
Bump again.

---

### Post by BloodyIron on 2012-01-10
Does anyone have any ideas on this?

---

### Post by BloodyIron on 2012-01-11
Bump

---

### Post by BloodyIron on 2012-01-13
So I guess there is no fix for this?

---

