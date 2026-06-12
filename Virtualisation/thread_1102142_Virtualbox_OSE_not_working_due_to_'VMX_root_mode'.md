---
title: "Virtualbox OSE not working due to 'VMX root mode'"
date: 2009-03-21
forum: Virtualisation
---

### Post by Admiral Yi on 2009-03-21
Hello,
I posted this already in general help forum, but I got no replies, so thought i'd try again here.

I'm trying to run virtual box OSE on my Ubutnu 8.10 desktop. I would like to try out some other Linux operating systems in it, with a view to installing Windows Xp for gaming at some point in the future. I downloaded it via synaptic and started it up. I set a virtual machine and created a virtual hard drive to run Open Solaris as a sort of test. However, when I start it up I get this message:

Code:

VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot.
VBox status code: -4011 (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

I'm reasonably proficient with Linux, but I don't really understand much of this. I've never done any messing around with the kernel. I tried running it as root, but to no avail. Anyone got a solution? Presumably I have to 'disable the KVM kernel' but I have no idea how to do this, so can someone please show me how?

I have tested this with other OSes (gentoo, knoppix and fedora) but still no luck.

---

### Post by namaku0 on 2009-03-21
Hope this is the case:
[http://blog.123sv.com/post/2008/12/02/VERR_VMX_IN_VMX_ROOT_MODE.aspx](http://blog.123sv.com/post/2008/12/02/VERR_VMX_IN_VMX_ROOT_MODE.aspx)

Can you post the output from lsmod?

Also try to turn off hardware assisted feature for your
VM and see if it works (uncheck the 'Enable VT-x/AMD-V').
[IMG]http://wikis.sun.com/download/attachments/54366392/Screenshot-Porting%20-%20Settings.png[/IMG]

---

### Post by jayleemor on 2009-04-14
I am also having the same problem.  I am very new to Linux.  I have tried the other threads with no success.  The link above does not go anywhere.  VBox worked for a couple of days, then all of a sudden, I started getting the above error message.  Tried removing/re-installing everything.  Nothing works.  Switched to Ubuntu 9.04 64bit, still nothing.  Any help would be appreciated.

---

### Post by Dedoimedo on 2009-04-14
VirtualBox and KVM are mutually exclusive, to the best of my knowledge.
You can't have both of them running on the same host. And as suggested, at the very least, not both can use the processor extensions.

Dedoimedo

---

### Post by jayleemor on 2009-04-14
Yeah, KVM is not installed.  Checked and rechecked.  With the extensions unchecked, still not working.  I don't know what to do besides uninstall KVM in Synaptic.  It says to recompile the kernel, currently researching how to do that.  Just a newb still.:cry:

---

### Post by debmissing on 2009-06-10
Hi and sorry if the answer is a bit late.

It seems that the kvm **module** is loaded as you're trying to use virtualbox. So you should first see the result of
```
lsmod | grep kvm
```
If there's something displayed, you just have to unload the module by theses 2 commands :
```
sudo modprobe -r kvm_intel
sudo modprobe -r kvm
```
(replace kvm_intel by kvm_amd if you're running an amd processor).

---

### Post by blknite on 2009-06-15
Awesome,  I was having this problem too.  :) This Work like a charm!

Thank you!

---

### Post by kngharv on 2010-01-04
> **jayleemor said:**
> Yeah, KVM is not installed.  Checked and rechecked.  With the extensions unchecked, still not working.  I don't know what to do besides uninstall KVM in Synaptic.  It says to recompile the kernel, currently researching how to do that.  Just a newb still.:cry:


I think the issue is that by default karmic install qemu, another virtualization software. 

If you choose to install and use Virtualbox, you can simply remove that qemu package.

---

### Post by jeffwiggins on 2010-01-29
Thanks for the tip.  After upgrading to Karmic I was having the same problem.  I removed qemu from my system and all appears to be working again.  

Jeff.

---

### Post by JEREMIAHBARLOW on 2010-04-01
Ya, that works fine until you reboot.

How do you get it to always work?
:D

---

### Post by naaman on 2010-04-04
> **JEREMIAHBARLOW said:**
> Ya, that works fine until you reboot.

How do you get it to always work?
:D

Try out the following:
("nano" can be substituded for "vi" for easier editing)

```
naaman@caterham:~$ sudo vi /etc/modprobe.d/blacklist-kvm.conf

# Disable kvm modules at boot
blacklist kvm_intel
blacklist kvm

```

---

### Post by gurensan on 2010-04-14
Completely remove qemu, qtemu, and qemu-kvm and it works.

---

### Post by JEREMIAHBARLOW on 2010-05-21
I removed kvm, qemu, qtemu, and qemu-kvm and still not worked after reboot.


Ok

```
naaman@caterham:~$ sudo nano /etc/modprobe.d/blacklist-kvm.conf

# Disable kvm modules at boot
blacklist kvm_intel
blacklist kvm

```

Worked great! 


Thank YOU!

---

### Post by Paul.E.T on 2011-03-20
Ref:  above  March 21st, 2009 	  #1
by  Admiral Yi   and others above

Virtualbox OSE not working due to 'VMX root mode'
March 2011:
     I have put V-box on five independent systems:  3 amd and 2 intel.  This is the first time I've run into this same VMX root mode problem on the two intel machines.  I hope debmissing's solution works with Ubuntu 10.4.1 and .2 but won't know until later this week.
Paul

---

