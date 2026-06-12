---
title: "KVM guest display not detected"
date: 2015-04-14
forum: Virtualisation
---

### Post by satimis on 2015-04-14
Hi all,

Host ubuntu 14.04
Guest ubuntu 14.04
KVM

Guest couldn't have the right driver for display which couldn't be detected, only showing "unknow display"

Please advise how to fix it.  Is there some like "guest addition" on KVM?

Daemon to access to guest virtual machine through virtio serial - Not installed

Guest-side qemu-system agent, qemu-guest-agent - not installed

Regards
satimis

---

### Post by TheFu on 2015-04-15
The guest system doesn't know anything about your real hardware.  Without extreme effort, that won't change.
KVM does not have "guest additions", but you can use Spice if you want more graphics performance before attempting the very difficult dedicated GPU passthru method.

Sorry - I don't understand the rest of your notes.

---

### Post by satimis on 2015-04-15
> **TheFu said:**
> The guest system doesn't know anything about your real hardware.  Without extreme effort, that won't change.
KVM does not have "guest additions", but you can use Spice if you want more graphics performance before attempting the very difficult dedicated GPU passthru method.

- snip - 
Hi,

Thanks for your advice.

I have been running virtualization somtimes.

Qemu/KVM -> Virtualbox

Now I come back to KVM and encountered the graphic problem.  I think I have to moving back to Virtualbox

Regards
satimis

---

### Post by TheFu on 2015-04-16
Did you remove the vbox guest additions before moving to KVM?

---

### Post by satimis on 2015-04-16
> **TheFu said:**
> Did you remove the vbox guest additions before moving to KVM?
Hi,

I haven't installed vbox guest additions on this box.

I removed Virtualbox running following commands before installing KVM```

$ sudo aptitude remove --purge virtualbox
$ sudo aptitude clean

```
They went through without complaint.

Also there was no complaint on installing KVM.

Regards
satimis

---

### Post by TheFu on 2015-04-16
> **satimis said:**
> Now I come back to KVM and encountered the graphic problem.

What "graphic problem?"
Hard to help without any data or description. Can you please tell us more?
Which video option is selected? VGA is usually the best choice for 14.04 and later KVM hosts.
Are you using virt-manager to create the VMs?
Are you trying to connect to the VM local or from a remote location?
What isn't working related to the screen?

---

### Post by satimis on 2015-04-16
> **TheFu said:**
> What "graphic problem?"
What isn't working related to the screen?

Guest couldn't detect the correct display
(please see screenshot_kvm_guest01.png attached)

I tried```

-> Settings -> Software & Updates -> Additional Drivers (tab)
```
but no driver was found
(please see screenshot_kvm_guest01.png attached)
However these steps work on Ubuntu 14.04 as host

> 
Which video option is selected? VGA is usually the best choice for 14.04 and later KVM hosts.
Where to check it?

> 
Are you using virt-manager to create the VMs?
Yes

> 
Are you trying to connect to the VM local or from a remote location?

To connect VM locally is for testing.  The final goal is to connect it remotely.

Other problems
1) How to copy/paste amongst guests and host
2) How to share files amongst guests and host
3) Where can I input the info of the guest similar to VM of Virtualbox
(please see settings.png attached)

Thanks

Regards
satimis

---

### Post by TheFu on 2015-04-16
There aren't any additional drivers for a guest VM display. The VM doesn't know anything about your real hardware and definitely doesn't know about your GPU.
The "VGA" is set in the VM settings (virt-manager) for the VM, under "Video".  The "Display" should probably be "VNC".  If you are just double-clicking to access the VM login and desktop, them you are using VNC.  VNC isn't very fast. You may want Spice which uses the QXL driver or for remote access, use x2go (client/server). x2go is installed like there isn't any VM involved at all.

My VM hosts don't have anything physically connected like a keyboard, monitor, or mouse, so I always connect remotely over either ssh or x2go. Only under desperate situations will I use the virt-manager "console" connection through VNC. There is a world of difference in performance between x2go and VNC, plus x2go works over ssh automatically.

[https://virt-manager.org/](https://virt-manager.org/) might be helpful. Especially [https://virt-manager.org/wp-content/uploads/2013/04/virt-manager-guest-cpu.png](https://virt-manager.org/wp-content/uploads/2013/04/virt-manager-guest-cpu.png)

I need to make a fresh "how-to" document for KVM+virt-manager for my blog ... similar to what I did for virtualbox years ago. I've been playing with screen recordings, but don't think I'm ready for that at this point. Have a new VM server to setup .. .that will be a good chance to capture screens - probably in a few days. Sorry I can't do it today.

---

### Post by satimis on 2015-04-16
> **TheFu said:**
> There aren't any additional drivers for a guest VM display. The VM doesn't know anything about your real hardware and definitely doesn't know about your GPU.
The "VGA" is set in the VM settings (virt-manager) for the VM, under "Video".  The "Display" should probably be "VNC".  If you are just double-clicking to access the VM login and desktop, them you are using VNC.  VNC isn't very fast. You may want Spice which uses the QXL driver or for remote access, use x2go (client/server). x2go is installed like there isn't any VM involved at all.

My VM hosts don't have anything physically connected like a keyboard, monitor, or mouse, so I always connect remotely over either ssh or x2go. Only under desperate situations will I use the virt-manager "console" connection through VNC. There is a world of difference in performance between x2go and VNC, plus x2go works over ssh automatically.

[https://virt-manager.org/](https://virt-manager.org/) might be helpful. Especially [https://virt-manager.org/wp-content/uploads/2013/04/virt-manager-guest-cpu.png](https://virt-manager.org/wp-content/uploads/2013/04/virt-manager-guest-cpu.png)

I need to make a fresh "how-to" document for KVM+virt-manager for my blog ... similar to what I did for virtualbox years ago. I've been playing with screen recordings, but don't think I'm ready for that at this point. Have a new VM server to setup .. .that will be a good chance to capture screens - probably in a few days. Sorry I can't do it today.

Hi,

Your advice noted.  Thanks.

I have come across Spice before
[http://www.spice-space.org/](http://www.spice-space.org/)

I'll test it after completing my current test first.

Regards
satimis

---

### Post by TheFu on 2015-04-16
I haven't tried spice recently, but it wasn't a good as x2go last time I did it. Think there was a keyboard mapping issue too - like the arrow keys didn't work at all - don't remember now, but it was something important like that. Under 12.04, don't think spice worked at all for me.  It has promise and has been getting much better with every release.

Good luck - let us know how it works out, please.

---

