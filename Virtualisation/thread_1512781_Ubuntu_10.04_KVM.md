---
title: "Ubuntu 10.04 KVM"
date: 2010-06-18
forum: Virtualisation
---

### Post by Siryx on 2010-06-18
Hi all.

I am beginning with KVM. I got one problem in this moment, and I google it for a while, but I didn't find a solution.

I create a VM from Ubuntu Server 10.04. 

When i got to virsh to "console" it, i "connect" but doesn't show me a thing

```
virsh # define /etc/libvirt/qemu/monitoring.xml 
Domain monitoring defined from /etc/libvirt/qemu/monitoring.xml

virsh # start monitoring
Domain monitoring started

virsh # list --all
 Id Name                 State
----------------------------------
  5 monitoring          running


virsh # console monitoring
Connected to domain monitoring
Escape character is ^]


```

Thanks in advance.

---

### Post by TheFu on 2010-06-19
I'm pretty certain you just need to hit <enter> to see a console login screen.  When you want to leave the console, <ctl>-] is how you close it.  Telnet has worked this way for as long as I can recall - 25+ (and probably 35+ yrs).

---

### Post by Siryx on 2010-06-19
> **TheFu said:**
> I'm pretty certain you just need to hit <enter> to see a console login screen.  When you want to leave the console, <ctl>-] is how you close it.  Telnet has worked this way for as long as I can recall - 25+ (and probably 35+ yrs).

I hit <enter> many times :lolflag:, before i create this post, but nothing happens.

nothing i hit on the keyboard appear in the screen.

Any other ideas??

---

### Post by andydread on 2010-07-25
Same exact problem here.  I pressed enter several times also.  I get a connect but no login prompt.

---

### Post by alastair on 2010-07-28
I think I have this problem as well. The console connection doesn't seem to work directly so I used VNC instead.

I mostly just SSH to the VM now however.

---

### Post by papertigers on 2010-07-30
Do you have the serial interface set up on the VM??

There is a guide here:
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

---

