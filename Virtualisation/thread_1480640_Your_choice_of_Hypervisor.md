---
title: "Your choice of Hypervisor?"
date: 2010-05-11
forum: Virtualisation
---

### Post by samosamo on 2010-05-11
It's been almost two years since I built my home server virtual machine environment using Ubuntu 8.04 with VMWare Server 2.0.  Now that I have some experience there are a few things I'd like to do differently.  VMWare Server 2.0 is great and all but I need more. I was waiting for Ubuntu 10.04 to be released to begin the project.  That time is here now.

Requirements:
[LIST]
[*]Professional, stable*, easy maintenance, easy management*
[*]The ability to back up image files daily (I cron'd "vmbackup" tool for VMWare Server)
[*]Bare Metal preferred*
[*]The ability to virtualize any OS preferred
[/LIST]

I put asterisks on the points where VMWare Server 2.0 has failed me.

---

### Post by HermanAB on 2010-05-11
Well, VMware Server 2.x is total garbage, but it should not be lightly discarded.  It should be **thrown**, with great force...

The other VMware products work fine.  So, if you don't want to spend money, use VMware Player.

---

### Post by samosamo on 2010-05-12
> **HermanAB said:**
> Well, VMware Server 2.x is total garbage, but it should not be lightly discarded.  It should be **thrown**, with great force...

The other VMware products work fine.  So, if you don't want to spend money, use VMware Player.

Wow.  Did you... you just suggested I replace VMware Server 2.0 with VMWare Player?  I'm not sure if you're being sarcastic or not?  You must be?

---

### Post by TheFu on 2010-05-13
If you don't need or want a GUI, take a look at VMware ESXi 4.x. It is rock solid.  I've found 1 free GUI tool for backups (MS-Windows based), but you have to pay $$$ to get it to schedule backups or remember any settings. I think it is called VM-Explorer, VMX. You probably could write a AHK script to automate that.  Sadly, you still need an MS-Windows machine to run the VM controller software so you can manage ESXi.  The VMs can remain running while you're doing a backup thanks to VMware's snapshots.

There is also a backup script based on ssh access that can be used. Google a little to find it. If you enable ssh access on ESXi, you've just become unsupported with your ESXi install. OTOH, you didn't pay anything for it. I've had this running for 9+ months - never had a failure with either ubuntu server or Win7 Pro client VM installs.

If you need a GUI on the same machine, I'd definitely look at VirtualBox. I've only used vbox on a Windows host, so weekly stability issues may have been due to the host OS and not Vbox, but I wouldn't trust it for "server class" needs.

If you weren't running 10.04, I'd suggest looking at Xen. Xen as a host hypervisor appears to have been removed in 10.04. I've been looking at KVM for a few months, but haven't gained the confidence in that tool to suggest it.

VMware Player or a newer version of Server may also be worth a look. I simply don't have any recent experience with those.

---

