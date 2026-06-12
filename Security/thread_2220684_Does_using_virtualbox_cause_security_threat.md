---
title: "Does using virtualbox cause security threat?"
date: 2014-04-29
forum: Security
---

### Post by grier-devon on 2014-04-29
Hello Ubuntu Community,
I have to use virtualbox to run Windows for college thanks to proprietary software that some classes require. I was curious while working in Windows 7 is it possible for a hacker to be able to access the Linux partitions through the Windows vdi? I don't keep anything personal on the Window VM but would hate to think that a hacker or NSA could get into my Linux system while I am using the Windows VM, Thanks for any input.

Devon

---

### Post by QIII on 2014-04-29
Secure your Win VM as you should and secure your Ubuntu machine as you should and you should have no problem with either.

In general, your VM is sandboxed and separate from your host.  I haven't heard of any serious exploits of any weakness in that regard.  People us VM Servers all the time for just that reason, although VirtualBox is not the sort of solution used by major sites.  If your Win VM gets compromised, either go back to an earlier snapshot or dump it and start a new one.

You are better off worrying about being struck by a meteor than snooping by spooky guys from the NSA in black vans down the street.  Unless you are plotting an armed overthrow of the US government, they are not going to take much interest in the fact that you surf open source web sites!  ;)

---

### Post by ant2ne on 2014-04-29
Your Win7 VM, if compromised could be used to attack other systems. So keep it as secure as you would a physical machine. I've heard of theoretical attacks where a compromised VM could attack the hypervisor and then take control of ALL VMs. But it is highly unlikely.

---

### Post by jon43 on 2014-04-29
I have this same sort of concern. In the end, I make sure I take all appropriate security measures in the Windows guest (login as a standard user instead of admin, use sandboxie for my browsing, and run an A/V program). I also take the additional step (although I have no idea if it does any good) of running the VBox only from a non-admin Ubuntu account.

---

### Post by bashiergui on 2014-04-29
> **QIII said:**
> Secure your Win VM as you should and secure your Ubuntu machine as you should and you should have no problem with either.definitely agree with this part.

> In general, your VM is sandboxed and separate from your host. I haven't heard of any serious exploits of any weakness in that regard. People us VM Servers all the time for just that reason, although VirtualBox is not the sort of solution used by major sites. If your Win VM gets compromised, either go back to an earlier snapshot or dump it and start a new one.Well kind of.

A VM will be a sandbox if you set it up as a sandbox. If you set it up as just another machine on your network, then it will not be a sandbox. It will just be another device on the Iternet.

There are plenty of known vulnerabilities and exploits that will allow a guest to break out of a VM. Your best defense against that is to keep your software (all of it) updated. I wouldn't expect to see guest breakout exploits in your average malware anyway, that would be more for targeted and corporate attacks.

to the OP: if you need certain apps to run on windows then you can set a VM to be "host only networking". That means the VM can only talk to your host computer and it cannot talk to the internet. Even if you transfer malware to the Windows VM by accident it wont matter because no hackers will be able to talk to it. That's what I recommend for you.

That will not keep the NSA out though. If the NSA wants on your linux or windows machines then they already did. You'll drive yourself nuts if that's really your goal so focus on the stuff you can actually control.

---

### Post by HermanAB on 2014-05-01
If you are paranoid, then set the VM to host networking only for example, so that it cannot be connected to anything else and do your web browsing on Linux.

...and if you actually want to improve something in Linux too, enable App Armor.

---

### Post by bashiergui on 2014-05-10
> **HermanAB said:**
> If you are paranoid, then set the VM to host networking only for example, so that it cannot be connected to anything else and do your web browsing on Linux.
Jee I wish I would have thought of that ;)

---

